### 整理後的原文：
Among the disadvantages of the proliferation of database technology is the potential of sensitive data being accessed by unauthorized personnel. Someone placing an order at a company’s website should not have access to the company’s financial data; similarly, an employee in a company’s benefits department may need access to the company’s employee records but should not have access to the corporation’s inventory or sales records. Thus, the ability to control access to the information in the database is as important as the ability to share it.

To provide different users access to different information within a database, database systems often rely on schemas and subschemas. A schema is a description of the entire database structure that is used by the database software to maintain the database. A subschema is a description of only that portion of the database pertinent to a particular user’s needs. For example, a schema for a university database would indicate that each student record contains such items as the current address and phone number of that student in addition to the student’s academic record. Moreover, it would indicate that each student record is linked to the record of the student’s faculty adviser. In turn, the record for each faculty member would contain the person’s address, employment history, and so on. Based on this schema, a linkage system would be maintained that ultimately connected the information about a student to the employment history of a faculty member.

To keep the university’s registrar from using this linkage to obtain privileged information about the faculty, the registrar’s access to the database must be restricted to a subschema whose description of the faculty records does not include employment history. Under this subschema, the registrar could find out which faculty member is a particular student’s adviser but could not obtain access to additional information about that faculty member. In contrast, the subschema for the payroll department would provide the employment history of each faculty member but would not include the linkage between students and advisers. Thus, the payroll department could modify a faculty member’s salary but could not obtain the names of the students advised by that person.

---

### 翻譯：
在數據庫技術普及的缺點中，敏感數據可能被未經授權的人員訪問是一個潛在問題。例如，在公司網站下訂單的人不應該有權訪問公司的財務數據；同樣，公司福利部門的員工可能需要訪問公司的員工記錄，但不應該有權訪問公司的庫存或銷售記錄。因此，控制數據庫中信息的訪問權限與共享信息的能力同樣重要。

為了讓不同用戶訪問數據庫中的不同信息，數據庫系統通常依賴於模式（schema）和子模式（subschema）。模式是對整個數據庫結構的描述，數據庫軟件使用它來維護數據庫。子模式則是僅描述與特定用戶需求相關的那部分數據庫。例如，大學數據庫的模式可能會指出，每個學生記錄包含學生的當前地址、電話號碼以及學業記錄。此外，它還會指出每個學生記錄與其指導教師的記錄相連。而每位教師的記錄則包含其地址、就業歷史等信息。基於此模式，系統會維護一個連接機制，最終將學生的信息與教師的就業歷史聯繫起來。

為了防止大學註冊處利用這種連接機制獲取教師的特權信息，註冊處對數據庫的訪問必須限制在一個子模式下，該子模式對教師記錄的描述不包含就業歷史。在這個子模式下，註冊處可以查詢某位學生的指導教師是誰，但無法獲取該教師的其他信息。相比之下，薪資部門的子模式會提供每位教師的就業歷史，但不包含學生與指導教師之間的連接。因此，薪資部門可以修改教師的薪水，但無法獲取該教師指導的學生名單。

---

### 解釋：
在資料庫技術的上下文中，**Schemas（模式）** 指的是對資料庫結構的完整描述，定義了資料的組織方式、資料表（tables）之間的關聯性，以及每個資料表包含的欄位（fields）和資料型態。模式是資料庫的「藍圖」，它由資料庫管理系統（DBMS）用來維護和管理資料的儲存與存取。

---

### 在原文中的具體含義：
1. **整體結構定義**  
   - Schema 描述整個資料庫的邏輯結構。例如，在大學資料庫的例子中，模式會明確定義：
     - 學生記錄包含哪些欄位（如姓名、地址、學業記錄、指導教師的連結）。
     - 教師記錄包含哪些欄位（如地址、就業歷史）。
     - 學生與教師之間的關聯性（如「每個學生連結到一名指導教師」）。

2. **安全與權限控制的基礎**  
   - Schema 是實現「子模式（subschema）」的基礎。通過子模式，可以限制不同使用者看到的資料範圍。例如：
     - 教務處的子模式可能只顯示學生記錄中的基本資訊（姓名、學業記錄）和指導教師的姓名，但隱藏教師的就業歷史。
     - 薪資部門的子模式可能僅顯示教師的薪資和就業歷史，但隱藏學生與教師的關聯。

3. **資料獨立性**  
   - Schema 將資料的邏輯結構（使用者看到的資料）與物理儲存方式（資料實際如何存儲）分離。這種分離讓使用者無需了解底層儲存細節，也能透過子模式安全存取所需資料。

---

### 舉例說明：
- **大學資料庫的 Schema**  
  - 定義學生表（Student Table）：  
    `學號（ID）、姓名（Name）、地址（Address）、電話（Phone）、學業記錄（Academic Record）、指導教師ID（Advisor_ID）`
  - 定義教師表（Faculty Table）：  
    `教師ID（ID）、姓名（Name）、地址（Address）、就業歷史（Employment History）`
  - 定義關聯：  
    `學生表中的 Advisor_ID 連結到教師表的 ID`。

- **子模式的作用**  
  - **教務處的子模式**：僅顯示學生表中的 `學號、姓名、學業記錄、指導教師姓名`，但不顯示教師的就業歷史。
  - **薪資部門的子模式**：僅顯示教師表中的 `姓名、就業歷史、薪資`，但不顯示學生與教師的關聯。

---

### 總結：
在資料庫系統中，**Schema 是資料的「總設計圖」**，確保資料結構的一致性，並作為權限控制的基礎。通過子模式（Subschema），系統能限制使用者僅存取與其職責相關的部分資料，從而平衡資料共享與安全性。

