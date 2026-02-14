# ERD-
```mermaid
erDiagram

    USERS {
        bigint id PK
        string username
        string name
        string role
        timestamp created_at
        timestamp updated_at
    }

    SISWAS {
        bigint id PK
        bigint user_id FK
        string nis UNIQUE
        string nama
        string kelas
        timestamp created_at 
        timestamp updated_at
    }

    ADMINS {
        bigint id PK
        bigint user_id FK
        enum level
        timestamp created_at
        timestamp updated_at
    }

    KATEGORIS {
        bigint id PK
        string nama
        timestamp created_at
        timestamp updated_at
    }

    ASPIRASIS {
        bigint id PK
        string nama_siswa
        bigint nis
        bigint id_kategori FK
        string lokasi
        string keterangan
        bigint user_id FK
        enum status
        text feedback
        timestamp created_at
        timestamp updated_at
    }

    USERS ||--o{ SISWAS : "has"
    USERS ||--o{ ADMINS : "has (nullable)"
    USERS ||--o{ ASPIRASIS : "creates"
    KATEGORIS ||--o{ ASPIRASIS : "categorizes"
    SISWAS ||--o{ ASPIRASIS : "files (via nis)"
```

