# PrintNinja Demo Project

![image](https://github.com/user-attachments/assets/00944f54-beae-43d2-9f84-d3d15c3c3995)


> Backend-focused demo project created for a job interview at PrintNinja, showcasing advanced customer and business-oriented features.

## Quick Start Access

To explore the full features of this demo as a logged-in user, use the following credentials:

```
Email: alice@gmail.com
Password: Password123!
```

These credentials will give you access to all user features including saved quotes, order history, and personalized AI recommendations.

## 1. Overview

### Purpose
This project is a comprehensive demonstration of my backend development skills, created specifically for the PrintNinja backend role interview. It enhances the original PrintNinja website with advanced features focused on improving both customer experience and business operations.

### Technologies Used
- **Frontend:** React.js, TailwindCSS, Framer Motion
- **Backend:** Node.js, Express
- **Database:** PostgreSQL, Supabase
- **Authentication:** Supabase Auth
- **File Storage:** Supabase Storage
- **Deployment:** Vercel (Frontend), Supabase Edge Functions (Backend)

### Features at a Glance
- Dynamic Product Catalog with Categorization
- Interactive Quote Generation with Real-time Updates
- Smart File Validation & Print-Ready Checks
- Enhanced Order Tracking & Management
- AI-assisted Print Specification Suggestions
- Real-time Pricing Calculator with Detailed Breakdown
- Quote Comparison & Management System
- Role-based User Access Control
- Live Customer Support Chat
- Instant File Preview with Print Issue Detection
- Multi-quote Comparison Tool
- Shipping & Delivery ETA Estimator
- Saved Quotes & Reorder Functionality
- Mobile-Responsive UI with Modern Design

## 2. Features Implemented

### Core Features

#### Product Catalog
- Organized by categories (Comics, Children's Books, Art Books, etc.)
- Detailed product specifications
- Sample galleries with previous projects
- Filter by size, binding type, and other parameters

#### Quote Generation Wizard
- Step-by-step guided process
- Interactive selection of options
- Real-time pricing updates
- Option comparison
- Save quotes for later

#### File Upload System
- Multi-file upload support
- Automatic validation for print-ready files
- Format compatibility checking
- Resolution and color space verification
- Error reporting with actionable feedback

#### Order Management
- Comprehensive order history
- Real-time status updates
- Tracking integration
- Reordering capability
- Order modification before production

### Advanced Features

#### AI Print Specification Suggestion System
- Analyzes uploaded files to suggest optimal print settings
- Recommends paper types based on content analysis
- Suggests binding options based on page count and usage
- Estimates optimal quantities based on project type
- Provides cost-saving recommendations
- Detects image quality issues and suggests improvements
- Intelligently identifies color profile mismatches
- Recommends complementary finishing options
- Predicts optimal size based on content type and purpose
- Suggests eco-friendly alternatives when applicable

### AI Suggestion System
*The AI-powered print specification suggestion system analyzing a comic book file*

##### Advanced AI Features

###### Content Analysis Engine
- Automatic content type detection (text-heavy, image-heavy, mixed)
- Image resolution and quality assessment
- Color distribution analysis for optimal paper selection
- Text density evaluation for binding recommendations

### Content Analysis
*Content analysis breakdown showing detected elements and quality scores*

###### Smart Budget Optimization
- Multi-tier pricing recommendations
- Volume discount optimization
- Alternative material suggestions for cost reduction
- Quality-cost tradeoff visualization
- Budget-constrained specification finder

### Budget Optimization
*Budget optimization interface showing cost-saving alternatives*

###### Print Issue Prevention
- Automated bleed and margin checks
- Spine width calculation based on page count and paper thickness
- Color space conversion warnings and recommendations
- Binding compatibility warnings for specific content layouts
- Automated preflight checking with actionable feedback

### Print Issue Prevention
*Print issue detection and resolution recommendations*

#### Real-time Quote Calculator
- Detailed pricing breakdown by component
- Volume discount visualization
- Option comparison with cost differences
- Tax and shipping estimations
- Currency conversion options

#### Quote Management System
- Save multiple versions of quotes
- Share quotes via email or link
- Convert quotes to orders
- Quote expiration management
- Bulk quote operations for large clients

#### Instant File Preview
- Browser-based PDF rendering
- Page-by-page preview
- Bleed and trim line visualization
- Color accuracy simulation
- Print issues detection and highlighting

#### Role-based Authentication
- Customer accounts with order history
- Admin dashboard with order management
- Print operator portal with production queues
- Sales representative views with client management
- Analytics dashboard for business intelligence

#### Multi-quote Comparison
- Side-by-side quote comparison
- Highlight differences between quotes
- Save comparison results
- Share comparisons with team members
- Export comparison data

#### Delivery Estimator
- Real-time shipping rate calculation
- Production time estimation
- Delivery date prediction
- Express options visualization
- International shipping support

## 3. API Endpoints

### Quote Generation

```
POST /api/quotes
```

Request:
```json
{
  "projectType": "comic",
  "size": "6.625\" x 10.25\"",
  "bindingType": "perfectBound",
  "coverType": "softcover",
  "coverPaper": "100# Gloss",
  "insidePaper": "70# Matte",
  "pageCount": 32,
  "quantity": 500,
  "color": "fullColor",
  "shipping": {
    "method": "standard",
    "address": {
      "country": "USA",
      "postalCode": "60290"
    }
  }
}
```

Response:
```json
{
  "quoteId": "QT-10245",
  "projectType": "comic",
  "totalPrice": 1275.50,
  "priceBreakdown": {
    "printing": 975.50,
    "binding": 200.00,
    "shipping": 100.00
  },
  "estimatedDelivery": "2025-06-15",
  "expiresAt": "2025-06-23"
}
```

### Product Catalog

```
GET /api/products?category=comics
```

Response:
```json
{
  "products": [
    {
      "id": "comic-standard",
      "name": "Standard Comic",
      "description": "Industry standard size comic with premium paper options",
      "sizes": ["6.625\" x 10.25\"", "8.5\" x 11\""],
      "bindingOptions": ["saddle-stitch", "perfect-bound"],
      "minimumPages": 8,
      "maximumPages": 240,
      "priceStartingAt": 3.25,
      "imageUrl": "/assets/products/standard-comic.jpg",
      "sampleProjects": [
        {
          "name": "Amazing Adventures #1",
          "thumbnailUrl": "/assets/samples/comic-sample-1.jpg"
        }
      ]
    }
  ],
  "totalCount": 5
}
```

### File Upload

```
POST /api/upload
```

Request:
```
FormData with file attached
```

Response:
```json
{
  "fileId": "file-28a7d2",
  "fileName": "my-comic-interior.pdf",
  "fileSize": 15242880,
  "uploadedAt": "2025-05-23T14:32:10Z",
  "validation": {
    "status": "warning",
    "issues": [
      {
        "type": "resolution",
        "severity": "warning",
        "message": "Some images are below 300 DPI",
        "pages": [3, 7, 12],
        "recommendation": "Consider replacing low-resolution images for better print quality"
      }
    ],
    "recommendations": [
      "Switch to CMYK color space for more accurate color representation"
    ]
  },
  "previewUrl": "/api/preview/file-28a7d2"
}
```

### Order Status

```
GET /api/orders/ORD-5687/status
```

Response:
```json
{
  "orderId": "ORD-5687",
  "status": "production",
  "statusHistory": [
    {
      "status": "received",
      "timestamp": "2025-05-10T09:15:32Z"
    },
    {
      "status": "prepress",
      "timestamp": "2025-05-11T11:32:45Z"
    },
    {
      "status": "production",
      "timestamp": "2025-05-12T08:45:12Z"
    }
  ],
  "currentStage": {
    "name": "Printing",
    "progress": 65,
    "estimatedCompletion": "2025-05-24"
  },
  "shipping": {
    "carrier": "FedEx",
    "estimatedDelivery": "2025-05-30",
    "trackingAvailable": false
  }
}
```

### AI Print Suggestions

```
POST /api/ai/suggestions
```

Request:
```json
{
  "fileId": "file-28a7d2",
  "projectType": "comic",
  "budget": 2000,
  "audience": "collectors"
}
```

Response:
```json
{
  "suggestions": {
    "paperType": {
      "recommendation": "80# Gloss",
      "reasoning": "Vibrant colors in your artwork would benefit from a glossy finish",
      "alternatives": ["70# Matte", "100# Gloss"]
    },
    "binding": {
      "recommendation": "Perfect Bound",
      "reasoning": "Your 64-page comic exceeds the optimal page count for staple binding",
      "alternatives": ["Saddle Stitch with thinner paper"]
    },
    "quantity": {
      "recommendation": 500,
      "reasoning": "Best price-per-unit balance for your budget",
      "costBreakdown": {
        "250": {
          "totalCost": 1250,
          "unitCost": 5.00
        },
        "500": {
          "totalCost": 1750,
          "unitCost": 3.50
        },
        "1000": {
          "totalCost": 2800,
          "unitCost": 2.80
        }
      }
    }
  }
}
```

### AI Content Analysis

```
POST /api/ai/analyze-content
```

Request:
```json
{
  "fileId": "file-28a7d2",
  "analysisType": "comprehensive",
  "targetProductType": "comic",
  "qualityPreference": "premium"
}
```

Response:
```json
{
  "analysisId": "analysis-56792",
  "contentBreakdown": {
    "textDensity": 0.35,
    "imagePercentage": 0.65,
    "colorfulness": 0.82,
    "contrastRatio": 0.75
  },
  "qualityAssessment": {
    "averageImageDpi": 285,
    "lowestImageDpi": 210,
    "problematicImages": [
      {
        "pageNumber": 7,
        "issue": "Resolution below 300 DPI",
        "recommendedAction": "Replace or upscale image"
      }
    ],
    "textQuality": "good",
    "colorSpaceIssues": false
  },
  "recommendations": {
    "paperType": {
      "primary": "80# Gloss",
      "reason": "Best for vibrant colors with 65% image content",
      "alternatives": ["100# Gloss", "70# Matte"]
    },
    "printProcess": {
      "primary": "Offset",
      "reason": "Superior quality for high color saturation",
      "alternatives": ["Digital for smaller runs"]
    },
    "finishing": {
      "recommendations": ["Aqueous coating", "Spot UV on cover"],
      "reasoning": "Enhance color vibrancy and provide protection"
    }
  }
}
```

## 4. Database Schema

The application is built on a robust database schema designed to efficiently support all print-related business operations:

![image](https://github.com/user-attachments/assets/7cc9e1fa-e0d9-49d5-8740-06354bfc97ca)

*Complete database schema showing relationships between core entities*

### Core Tables

#### Users and Authentication
- **users**
  ```sql
  CREATE TABLE users (
    user_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    first_name VARCHAR(100),
    last_name VARCHAR(100),
    company VARCHAR(255),
    phone VARCHAR(50),
    role VARCHAR(50) DEFAULT 'customer',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    last_login TIMESTAMP
  );
  ```

- **auth_tokens**
  ```sql
  CREATE TABLE auth_tokens (
    token_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    user_id UUID REFERENCES users(user_id) ON DELETE CASCADE,
    token VARCHAR(255) UNIQUE NOT NULL,
    expires_at TIMESTAMP NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

- **user_preferences**
  ```sql
  CREATE TABLE user_preferences (
    preference_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    user_id UUID REFERENCES users(user_id) ON DELETE CASCADE,
    preference_key VARCHAR(100) NOT NULL,
    preference_value TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE (user_id, preference_key)
  );
  ```

#### Orders and Quotes
- **quotes**
  ```sql
  CREATE TABLE quotes (
    quote_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    user_id UUID REFERENCES users(user_id) ON DELETE SET NULL,
    quote_number VARCHAR(50) UNIQUE NOT NULL,
    project_type VARCHAR(100) NOT NULL,
    size VARCHAR(100) NOT NULL,
    binding_type VARCHAR(100) NOT NULL,
    cover_type VARCHAR(100),
    cover_paper VARCHAR(100),
    inside_paper VARCHAR(100) NOT NULL,
    page_count INTEGER NOT NULL,
    quantity INTEGER NOT NULL,
    color VARCHAR(50) NOT NULL,
    total_price DECIMAL(10, 2) NOT NULL,
    price_breakdown JSONB,
    status VARCHAR(50) DEFAULT 'active',
    expires_at TIMESTAMP NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

- **orders**
  ```sql
  CREATE TABLE orders (
    order_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    user_id UUID REFERENCES users(user_id) ON DELETE SET NULL,
    quote_id UUID REFERENCES quotes(quote_id),
    order_number VARCHAR(50) UNIQUE NOT NULL,
    status VARCHAR(50) DEFAULT 'received',
    total_amount DECIMAL(10, 2) NOT NULL,
    tax_amount DECIMAL(10, 2) DEFAULT 0,
    shipping_amount DECIMAL(10, 2) DEFAULT 0,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    estimated_delivery TIMESTAMP
  );
  ```

- **files**
  ```sql
  CREATE TABLE files (
    file_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    user_id UUID REFERENCES users(user_id) ON DELETE SET NULL,
    file_name VARCHAR(255) NOT NULL,
    file_size BIGINT NOT NULL,
    file_type VARCHAR(100) NOT NULL,
    storage_path VARCHAR(500) NOT NULL,
    validation_status VARCHAR(50),
    validation_details JSONB,
    preview_url VARCHAR(500),
    uploaded_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    analysis_results JSONB
  );
  ```

- **quote_files**
  ```sql
  CREATE TABLE quote_files (
    quote_file_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    quote_id UUID REFERENCES quotes(quote_id) ON DELETE CASCADE,
    file_id UUID REFERENCES files(file_id) ON DELETE CASCADE,
    file_purpose VARCHAR(100) NOT NULL, -- 'interior', 'cover', 'additional'
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE (quote_id, file_id)
  );
  ```

- **order_status_history**
  ```sql
  CREATE TABLE order_status_history (
    history_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    order_id UUID REFERENCES orders(order_id) ON DELETE CASCADE,
    status VARCHAR(50) NOT NULL,
    notes TEXT,
    created_by UUID REFERENCES users(user_id) ON DELETE SET NULL,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

#### Products and Options
- **products**
  ```sql
  CREATE TABLE products (
    product_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    name VARCHAR(255) NOT NULL,
    description TEXT,
    category VARCHAR(100) NOT NULL,
    min_pages INTEGER,
    max_pages INTEGER,
    base_price DECIMAL(10, 2),
    price_per_page DECIMAL(10, 2),
    active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

- **product_options**
  ```sql
  CREATE TABLE product_options (
    option_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    product_id UUID REFERENCES products(product_id) ON DELETE CASCADE,
    option_type VARCHAR(100) NOT NULL, -- 'size', 'binding', 'paper', etc.
    option_name VARCHAR(255) NOT NULL,
    option_value VARCHAR(255) NOT NULL,
    price_modifier DECIMAL(10, 2) DEFAULT 0,
    active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

- **order_items**
  ```sql
  CREATE TABLE order_items (
    item_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    order_id UUID REFERENCES orders(order_id) ON DELETE CASCADE,
    product_id UUID REFERENCES products(product_id) ON DELETE SET NULL,
    quantity INTEGER NOT NULL,
    unit_price DECIMAL(10, 2) NOT NULL,
    total_price DECIMAL(10, 2) NOT NULL,
    specifications JSONB,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

#### Payment and Shipping
- **payments**
  ```sql
  CREATE TABLE payments (
    payment_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    order_id UUID REFERENCES orders(order_id) ON DELETE SET NULL,
    amount DECIMAL(10, 2) NOT NULL,
    payment_method VARCHAR(100) NOT NULL,
    transaction_id VARCHAR(255),
    status VARCHAR(50) DEFAULT 'pending',
    payment_date TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

- **shipping_addresses**
  ```sql
  CREATE TABLE shipping_addresses (
    address_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    user_id UUID REFERENCES users(user_id) ON DELETE CASCADE,
    name VARCHAR(255),
    company VARCHAR(255),
    address_line1 VARCHAR(255) NOT NULL,
    address_line2 VARCHAR(255),
    city VARCHAR(100) NOT NULL,
    state VARCHAR(100) NOT NULL,
    postal_code VARCHAR(20) NOT NULL,
    country VARCHAR(100) NOT NULL,
    phone VARCHAR(50),
    is_default BOOLEAN DEFAULT false,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

- **shipping_methods**
  ```sql
  CREATE TABLE shipping_methods (
    method_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    name VARCHAR(100) NOT NULL,
    description TEXT,
    base_price DECIMAL(10, 2) NOT NULL,
    estimated_days INTEGER,
    carrier VARCHAR(100),
    active BOOLEAN DEFAULT true,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

- **order_shipping**
  ```sql
  CREATE TABLE order_shipping (
    shipping_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    order_id UUID REFERENCES orders(order_id) ON DELETE CASCADE,
    address_id UUID REFERENCES shipping_addresses(address_id) ON DELETE SET NULL,
    method_id UUID REFERENCES shipping_methods(method_id) ON DELETE SET NULL,
    tracking_number VARCHAR(255),
    carrier VARCHAR(100),
    estimated_delivery TIMESTAMP,
    shipped_date TIMESTAMP,
    delivery_date TIMESTAMP,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

#### Production Management
- **production_batches**
  ```sql
  CREATE TABLE production_batches (
    batch_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    batch_number VARCHAR(50) UNIQUE NOT NULL,
    status VARCHAR(50) DEFAULT 'queued',
    start_date TIMESTAMP,
    end_date TIMESTAMP,
    notes TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

- **batch_orders**
  ```sql
  CREATE TABLE batch_orders (
    batch_order_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    batch_id UUID REFERENCES production_batches(batch_id) ON DELETE CASCADE,
    order_id UUID REFERENCES orders(order_id) ON DELETE CASCADE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    UNIQUE (batch_id, order_id)
  );
  ```

- **ai_suggestions**
  ```sql
  CREATE TABLE ai_suggestions (
    suggestion_id UUID PRIMARY KEY DEFAULT uuid_generate_v4(),
    file_id UUID REFERENCES files(file_id) ON DELETE SET NULL,
    user_id UUID REFERENCES users(user_id) ON DELETE SET NULL,
    suggestion_type VARCHAR(100) NOT NULL,
    suggestion JSONB NOT NULL,
    accepted BOOLEAN,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );
  ```

### Relationships

The schema follows a carefully designed relational model with the following key relationships:

1. **Users to Quotes/Orders**: One-to-many relationship where a user can have multiple quotes and orders
   ```sql
   ALTER TABLE quotes ADD CONSTRAINT fk_quotes_user FOREIGN KEY (user_id) REFERENCES users(user_id);
   ALTER TABLE orders ADD CONSTRAINT fk_orders_user FOREIGN KEY (user_id) REFERENCES users(user_id);
   ```

2. **Quotes to Orders**: One-to-one relationship where a quote can be converted to an order
   ```sql
   ALTER TABLE orders ADD CONSTRAINT fk_orders_quote FOREIGN KEY (quote_id) REFERENCES quotes(quote_id);
   ```

3. **Orders to Items**: One-to-many relationship where an order contains multiple items
   ```sql
   ALTER TABLE order_items ADD CONSTRAINT fk_order_items_order FOREIGN KEY (order_id) REFERENCES orders(order_id);
   ```

4. **Files to Quotes**: Many-to-many relationship through the quote_files junction table
   ```sql
   ALTER TABLE quote_files ADD CONSTRAINT fk_quote_files_quote FOREIGN KEY (quote_id) REFERENCES quotes(quote_id);
   ALTER TABLE quote_files ADD CONSTRAINT fk_quote_files_file FOREIGN KEY (file_id) REFERENCES files(file_id);
   ```

5. **Orders to Status History**: One-to-many relationship tracking all status changes
   ```sql
   ALTER TABLE order_status_history ADD CONSTRAINT fk_status_history_order FOREIGN KEY (order_id) REFERENCES orders(order_id);
   ```

6. **Orders to Payments**: One-to-many relationship for multiple payment transactions
   ```sql
   ALTER TABLE payments ADD CONSTRAINT fk_payments_order FOREIGN KEY (order_id) REFERENCES orders(order_id);
   ```

7. **Products to Options**: One-to-many relationship for product configuration options
   ```sql
   ALTER TABLE product_options ADD CONSTRAINT fk_product_options_product FOREIGN KEY (product_id) REFERENCES products(product_id);
   ```

8. **Orders to Shipping**: One-to-one relationship for shipping details
   ```sql
   ALTER TABLE order_shipping ADD CONSTRAINT fk_order_shipping_order FOREIGN KEY (order_id) REFERENCES orders(order_id);
   ```

9. **Production Batches to Orders**: Many-to-many relationship through batch_orders junction table
   ```sql
   ALTER TABLE batch_orders ADD CONSTRAINT fk_batch_orders_batch FOREIGN KEY (batch_id) REFERENCES production_batches(batch_id);
   ALTER TABLE batch_orders ADD CONSTRAINT fk_batch_orders_order FOREIGN KEY (order_id) REFERENCES orders(order_id);
   ```

### Indexing Strategy

For optimal database performance, the following indexes are implemented:

```sql
-- User lookup optimization
CREATE INDEX idx_users_email ON users(email);

-- Quote and order lookup
CREATE INDEX idx_quotes_user ON quotes(user_id);
CREATE INDEX idx_orders_user ON orders(user_id);
CREATE INDEX idx_quotes_status ON quotes(status);
CREATE INDEX idx_orders_status ON orders(status);

-- File organization
CREATE INDEX idx_files_user ON files(user_id);
CREATE INDEX idx_quote_files_quote ON quote_files(quote_id);
CREATE INDEX idx_quote_files_file ON quote_files(file_id);

-- Order tracking
CREATE INDEX idx_order_status_history_order ON order_status_history(order_id);
CREATE INDEX idx_order_status_history_timestamp ON order_status_history(timestamp);

-- Product catalog navigation
CREATE INDEX idx_products_category ON products(category);
CREATE INDEX idx_product_options_product ON product_options(product_id);
CREATE INDEX idx_product_options_type ON product_options(option_type);

-- Payment processing
CREATE INDEX idx_payments_order ON payments(order_id);
CREATE INDEX idx_payments_status ON payments(status);

-- Shipping management
CREATE INDEX idx_shipping_addresses_user ON shipping_addresses(user_id);
CREATE INDEX idx_order_shipping_order ON order_shipping(order_id);
```

### Database Design Principles

The schema was designed following these key principles:

1. **Normalization** - Tables are normalized to the third normal form (3NF) to reduce redundancy while maintaining data integrity
2. **Performance** - Strategic indexes on frequently queried columns optimize query performance
3. **Referential Integrity** - Foreign key constraints ensure data consistency across related tables
4. **Scalability** - Horizontal partitioning capabilities for high-volume tables like orders and files
5. **Auditability** - History tables and timestamps maintain complete records of changes
6. **Security** - Role-based access controls at the database level complement application security

## 5. Architecture Diagram

```
┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│                 │       │                 │       │                 │
│  React Frontend ├───────┤  Node.js API    ├───────┤  PostgreSQL DB  │
│  (Vite + React) │       │  (Express)      │       │  (Supabase)     │
│                 │       │                 │       │                 │
└────────┬────────┘       └────────┬────────┘       └─────────────────┘
         │                         │
         │                         │
┌────────▼────────┐       ┌────────▼────────┐       ┌─────────────────┐
│                 │       │                 │       │                 │
│  File Storage   │       │  AI Services    ├───────┤  ML Models      │
│  (Supabase)     │       │  (Edge Funcs)   │       │  (TensorFlow)   │
│                 │       │                 │       │                 │
└─────────────────┘       └────────┬────────┘       └─────────────────┘
                                   │
                                   │
                          ┌────────▼────────┐
                          │                 │
                          │  Print Analysis │
                          │  Engine         │
                          │                 │
                          └─────────────────┘
```

The architecture follows a modern separation of concerns:

1. **Frontend:** React application with TailwindCSS for styling, handling UI rendering and state
2. **API Layer:** Node.js with Express providing RESTful endpoints and business logic
3. **Database:** PostgreSQL via Supabase for data persistence
4. **Storage:** Supabase Storage for file uploads and management
5. **AI Services:** Custom Edge Functions for intelligent processing of files and quote suggestions
6. **ML Models:** TensorFlow-based models for content analysis and recommendation generation
7. **Print Analysis Engine:** Specialized service for print-specific file analysis and validation

### AI Component Architecture

The AI suggestion system uses a multi-layered approach:

1. **File Analysis Layer** - Extracts metadata, analyzes image quality, detects content types
2. **Recommendation Engine** - Processes analyzed data to generate print specifications
3. **Cost Optimization Layer** - Balances quality requirements with budget constraints
4. **Learning System** - Improves suggestions based on customer feedback and acceptance rates


## 6. Screenshots

### Quote Builder UI
![image](https://github.com/user-attachments/assets/46f889ad-737d-43f8-b06a-4a6e8dc97da4)

*The multi-step quote builder with real-time pricing updates*


### Admin Dashboard
![image](https://github.com/user-attachments/assets/18a6b236-65fa-4148-af60-801cded475db)

*Order management interface for PrintNinja staff*

## 7. How to Run Locally

### Prerequisites
- Node.js v18 or later
- npm v8 or later
- PostgreSQL (optional, can use Supabase remote instance)
- Supabase account for database and authentication

### Environment Setup
1. Clone the repository
```bash
git clone https://github.com/yourusername/printninja-demo.git
cd printninja-demo
```

2. Install dependencies
```bash
npm install
```

3. Create a `.env` file using the example template
```bash
cp .env.example .env
```

4. Update the `.env` file with your Supabase credentials
```
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
VITE_API_ENDPOINT=http://localhost:3000/api
```

### Database Setup
1. Create your Supabase project at https://app.supabase.com
2. Run the database migration scripts
```bash
npx supabase db push
```

### Starting the Application
1. Start the development server
```bash
npm run dev
```

2. In a separate terminal, start the API server
```bash
npm run server
```

3. Access the application at http://localhost:5173

### Example `.env` File
```
# Supabase configuration
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key-here

# API configuration
VITE_API_ENDPOINT=http://localhost:3000/api

# File storage limits
VITE_MAX_FILE_SIZE=100000000
VITE_ALLOWED_FILE_TYPES=pdf,jpg,jpeg,png,tif,tiff,eps,ai

# Feature flags
VITE_ENABLE_AI_SUGGESTIONS=true
VITE_ENABLE_LIVE_CHAT=true

# Optional: Analytics
VITE_ANALYTICS_ID=
```

## 8. Implemented Components

Below are the key components implemented in this demo project:

### Frontend Components

```
src/
├── components/
│   ├── AdvancedQuoteCalculator.jsx  - Real-time quote pricing calculator
│   ├── AISuggestion.jsx             - AI printing recommendation component
│   ├── FileUploadValidator.jsx      - Print-ready file validation
│   ├── QuoteForm.jsx                - Multi-step quote generation form
│   ├── QuoteFormStep.jsx            - Individual step in quote wizard
│   ├── QuoteOptionCard.jsx          - Option selection cards
│   ├── QuoteSummary.jsx             - Quote details summary view
│   ├── QuoteSelector.jsx            - Multi-quote comparison tool
│   ├── EnhancedOrderTracking.jsx    - Order status tracking component
│   └── LiveChat.jsx                 - Customer support chat interface
├── routes/
│   ├── quotes/
│   │   └── MyQuotes.jsx             - Saved quotes management
│   ├── ordering/
│   │   └── History.jsx              - Order history with tracking
│   └── Products.jsx                 - Product catalog
└── services/
    └── ai-service.js                - AI suggestion API interface
```

### Backend Services (Supabase Edge Functions)

```
supabase/
└── functions/
    ├── analyze-print-file/          - AI-powered file analysis
    ├── generate-quote/              - Quote generation service
    ├── send-order-notification/     - Order status notifications
    └── send-quote-email/            - Quote sharing via email
```

![Component Structure](./public/assets/screenshots/component-structure.png)
*Visual representation of key components and their interactions*

## License
This project is proprietary and created solely for demonstration purposes for PrintNinja. All rights reserved.

## Contact
For any questions regarding this demo, please contact [your.email@example.com](mailto:your.email@example.com)

## 9. Implementation Highlights

### Technical Innovations

#### Reactive Quote Calculation System
The real-time quote calculator uses a reactive computation model that instantly updates pricing as users modify specifications. This avoids unnecessary API calls by handling common calculations client-side while complex pricing rules are managed server-side.

```javascript
// Excerpt from AdvancedQuoteCalculator.jsx
const calculateTotalPrice = useCallback(() => {
  const basePrice = getBasePrice(specifications.size, specifications.paperType);
  const quantityFactor = getQuantityDiscount(specifications.quantity);
  const bindingCost = getBindingCost(specifications.bindingType, specifications.pageCount);
  const finishingCost = specifications.finishingOptions.reduce(
    (total, option) => total + finishingCosts[option] * specifications.quantity, 0
  );
  
  return (basePrice * specifications.quantity * quantityFactor) + bindingCost + finishingCost;
}, [specifications]);
```

#### AI File Analysis System
The AI suggestion engine uses a combination of image processing techniques and machine learning to analyze uploaded files:

1. **Content Detection** - Identifies text, images, and graphical elements
2. **Quality Assessment** - Evaluates resolution, color profiles, and potential print issues
3. **Specification Matching** - Maps content characteristics to optimal print specifications

![AI Analysis Flow](./public/assets/screenshots/ai-analysis-flow.png)
*Flow diagram of the file analysis and recommendation process*

#### Database Implementation

The implementation follows the comprehensive schema detailed in Section 4 (Database Schema). Each entity and relationship has been carefully implemented in Supabase:

```javascript
// Example of database access in QuoteService.js
async function saveQuote(userId, quoteData, files) {
  const { data, error } = await supabase
    .from('quotes')
    .insert({
      user_id: userId,
      specifications: quoteData.specifications,
      price: quoteData.totalPrice,
      created_at: new Date().toISOString()
    })
    .select();
    
  if (error) throw error;
  
  // Associate uploaded files with the quote
  if (files && files.length > 0) {
    const fileAssociations = files.map(file => ({
      quote_id: data[0].id,
      file_id: file.id
    }));
    
    await supabase
      .from('quote_files')
      .insert(fileAssociations);
  }
  
  return data[0];
}
```

### Performance Optimizations

1. **Lazy Loading** - Components and large assets are loaded on-demand
2. **Virtualized Lists** - Quote history and product catalogs use virtualization for smooth scrolling
3. **API Response Caching** - Frequently accessed data is cached to reduce API calls
4. **Precomputed Recommendations** - Common AI suggestions are precomputed and cached

### Security Measures

1. **Row-Level Security** - Supabase RLS policies ensure users can only access their own data
2. **Secure File Handling** - Files are validated, sanitized, and stored with secure access controls
3. **API Rate Limiting** - Prevents abuse of quote generation and AI analysis endpoints

## 10. Future Development

While this demo showcases a robust set of features, several enhancements could be implemented in a production environment:

### Planned Enhancements

1. **Advanced AI Color Management**
   - Color calibration recommendations based on uploaded content
   - Pantone color detection and matching
   - Print simulation with different paper types

2. **Enhanced Production Workflow Integration**
   - Direct integration with printing press scheduling
   - Automated prepress workflow
   - Real-time production floor updates

3. **Expanded Analytics**
   - Customer behavior analysis
   - Quote conversion optimization
   - Price sensitivity modeling

4. **International Expansion**
   - Multi-currency support
   - Localized product offerings
   - International shipping optimization

5. **Sustainability Features**
   - Carbon footprint calculator
   - Eco-friendly material options
   - Waste reduction recommendations

![Roadmap](./public/assets/screenshots/future-roadmap.png)
*Visual roadmap of planned feature enhancements*
