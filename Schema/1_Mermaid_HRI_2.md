
```mermaid
classDiagram
    class Catalog {
        +string title
        +string description
        +Agent publisher
        +date issued
        +date modified
        +string language
        +string license
        +string homepage
        +string spatialCoverage
    }

    class Project {
        +string title
        +string description
        +Agent coordinator
        +date startDate
        +date endDate
        +string funding
        +string objective
    }

    class Study {
        +string title
        +string description
        +Agent principalInvestigator
        +date studyStartDate
        +date studyEndDate
        +string studyType
        +string studyDesign
        +string population
    }

    class Dataset {
        +string title
        +string description
        +date issued
        +date modified
        +string language
        +string theme
        +string keyword
        +string spatial
        +string temporal
        +Agent publisher
        +string identifier
        +string healthCategory
        +string personalData
    }

    class Distribution {
        +string title
        +string description
        +string format
        +string accessURL
        +string downloadURL
        +string byteSize
        +string license
        +string rights
    }

    class DataService {
        +string title
        +string description
        +string endpointURL
        +string license
        +Agent publisher
    }

    class Agent {
        +string name
        +string type
        +string publisherNote
        +string publisherType
        +bool trustedDataHolder
    }

    class License {
        +string title
        +string URL
    }

    class Location {
        +string name
        +string geometry
    }

    Catalog "1" -- "0..*" Project : contains
    Project "1" -- "0..*" Study : includes
    Study "1" -- "0..*" Dataset : generates
    Dataset "1" -- "1..*" Distribution : has
    Dataset "1" -- "0..*" DataService : provides
    Dataset "1" -- "1" Agent : publishedBy
    Dataset "0..*" -- "0..1" License : licensedUnder
    Dataset "0..*" -- "0..*" Location : spatialCoverage
    DataService "1" -- "1" Agent : providedBy
