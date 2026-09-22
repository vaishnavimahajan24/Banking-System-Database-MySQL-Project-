
create database Banking_system;
use banking_system;

CREATE TABLE Customers (
    Customer_ID INT PRIMARY KEY,
    Customer_Name varchar(100) NOT NULL,
    Date_Of_Birth date,
    Gender ENUM('Male', 'Female', 'Other'),
    Email varchar(100),
    Phone varchar(15),
    Address varchar(255)
);
INSERT INTO Customers (Customer_ID, Customer_Name, Date_Of_Birth, Gender,Email, Phone, Address) VALUES
(1, 'Aarav Sharma', '1987-03-15', 'Male', 'aarav.sharma@example.com', '9876543210', '12 MG Road, Bengaluru, Karnataka'),
(2, 'Priya Iyer', '1992-07-28', 'Female', 'priya.iyer@example.com', '9123456780', '45 Nehru Street, Chennai, Tamil Nadu'),
(3, 'Rohan Mehta', '1985-11-02', 'Male', 'rohan.mehta@example.com', '9988776655', '8 C.G. Road, Ahmedabad, Gujarat'),
(4, 'Sneha Nair', '1994-05-19', 'Female', 'sneha.nair@example.com', '9012345678', '22 Marine Drive, mumbai, maharashtra'),
(5, 'Aditya Verma', '1990-01-10', 'Male', 'aditya.verma@example.com', '9765432109', '67 Park Street, Kolkata, West Bengal'),
(6, 'Kavya Reddy', '1996-09-23', 'Female', 'kavya.reddy@example.com', '9345678901', '14 Jubilee Hills, Hyderabad, Telangana'),
(7, 'Ishaan Kapoor', '1989-06-30', 'Male', 'ishaan.kapoor@example.com', '9786543210', '110 Connaught Place, New Delhi, Delhi'),
(8, 'Meera Joshi', '1993-12-14', 'Female', 'meera.joshi@example.com', '9823456789', '29 Fergusson College Road, Pune, Maharashtra'),
(9, 'Vikram Singh', '1988-04-21', 'Male', 'vikram.singh@example.com', '9654321098', '54 Civil Lines, Jaipur, Rajasthan'),
(10, 'Ananya Chatterjee', '1995-08-07', 'Female', 'ananya.chatterjee@example.com', '9876123450', '19 Salt Lake, Kolkata, West Bengal'),
(11, 'Rahul Deshmukh', '1986-02-18', 'Male', 'rahul.deshmukh@example.com', '9812345671', '5 FC Road, Pune, Maharashtra'),
(12, 'Tanya Malhotra', '1991-09-25', 'Female', 'tanya.malhotra@example.com', '9901234567', '12 Sector 17, Chandigarh, Punjab'),
(13, 'Arjun Banerjee', '1997-07-12', 'Other', 'arjun.banerjee@example.com', '9945671230', '33 College Street, Kolkata, West Bengal'),
(14, 'Neha Kulkarni', '1984-11-03', 'Female', 'neha.kulkarni@example.com', '9798123456', '7 Law Garden, Ahmedabad, Gujarat'),
(15, 'Sahil Khan', '1998-05-29', 'Other', 'sahil.khan@example.com', '9934567890', '23 Linking Road, Mumbai, Maharashtra');


CREATE TABLE Branches (
    Branch_ID INT PRIMARY KEY,
    Branch_Name varchar(100) NOT NULL,
    Location varchar(150),
    Phone varchar(15)
);
INSERT INTO Branches (Branch_ID,Branch_Name,Location,Phone) VALUES
(1, 'Mumbai Central Branch', 'Mumbai, Maharashtra', '022-23456789'),
(2, 'Delhi Connaught Place Branch', 'New Delhi, Delhi', '011-22334455'),
(3, 'Bengaluru MG Road Branch', 'Bengaluru, Karnataka', '080-44556677'),
(4, 'Chennai T Nagar Branch', 'Chennai, Tamil Nadu', '044-55667788'),
(5, 'Hyderabad Banjara Hills Branch', 'Hyderabad, Telangana', '040-66778899'),
(6, 'Kolkata Park Street Branch', 'Kolkata, West Bengal', '033-77889900'),
(7, 'Pune FC Road Branch', 'Pune, Maharashtra', '020-33445566'),
(8, 'Jaipur Civil Lines Branch', 'Jaipur, Rajasthan', '0141-99887766'),
(9, 'Ahmedabad CG Road Branch', 'Ahmedabad, Gujarat', '079-88997766'),
(10, 'Kochi Marine Drive Branch', 'Kochi, Kerala', '0484-22335566'),
(11, 'Lucknow Hazratganj Branch', 'Lucknow, Uttar Pradesh', '0522-44557788'),
(12, 'Bhopal New Market Branch', 'Bhopal, Madhya Pradesh', '0755-66778899'),
(13, 'Chandigarh Sector 17 Branch', 'Chandigarh, Punjab', '0172-22334455'),
(14, 'Indore Vijay Nagar Branch', 'Indore, Madhya Pradesh', '0731-33445566'),
(15, 'Visakhapatnam RK Beach Branch', 'Visakhapatnam, Andhra Pradesh', '0891-55667788');


CREATE TABLE Accounts (
    Account_ID INT PRIMARY KEY,
    Account_Type ENUM('Savings', 'Current', 'Fixed Deposit'),
    Balance decimal(15, 2),
    OpenDate date,
    Customer_ID int,
    Branch_ID int,
    Status ENUM('Active', 'Inactive') default 'Active',
    FOREIGN KEY (Customer_ID) REFERENCES Customers(Customer_ID),
    FOREIGN KEY (Branch_ID) REFERENCES Branches(Branch_ID)
);
INSERT INTO Accounts (Account_ID, Account_Type, Balance, OpenDate, Customer_ID, Branch_ID, Status)
VALUES
(1, 'Savings', 45230.50, '2018-03-15', 1, 1, 'Active'),
(2, 'Current', 125000.00, '2019-06-20', 2, 2, 'Active'),
(3, 'Fixed Deposit', 500000.00, '2020-01-10', 3, 3, 'Active'),
(4, 'Savings', 8745.75, '2021-08-05', 4, 4, 'Inactive'),
(5, 'Current', 35000.00, '2017-11-12', 5, 5, 'Active'),
(6, 'Savings', 26780.90, '2019-04-18', 6, 6, 'Active'),
(7, 'Fixed Deposit', 750000.00, '2020-12-25', 7, 7, 'Active'),
(8, 'Savings', 15300.00, '2018-07-30', 8, 8, 'Inactive'),
(9, 'Current', 98000.00, '2021-03-14', 9, 9, 'Active'),
(10, 'Savings', 5600.50, '2016-09-09', 10, 10, 'Active'),
(11, 'Fixed Deposit', 1200000.00, '2022-02-22', 11, 11, 'Active'),
(12, 'Savings', 44250.75, '2018-05-17', 12, 12, 'Inactive'),
(13, 'Current', 67000.00, '2019-10-21', 13, 13, 'Active'),
(14, 'Savings', 23450.00, '2021-12-01', 14, 14, 'Active'),
(15, 'Fixed Deposit', 850000.00, '2020-06-16', 15, 15, 'Active');


CREATE TABLE Transactions(
Transaction_id int PRIMARY KEY,
    Transaction_Date DATETIME DEFAULT CURRENT_TIMESTAMP,
    Type ENUM('Deposit', 'Withdrawal', 'Transfer'),
    Amount decimal(15, 2),
    Description text,
    Account_ID int,
    FOREIGN KEY (Account_ID) REFERENCES Accounts(Account_ID)
);
INSERT INTO Transactions (Transaction_id,Transaction_Date, Type, Amount, Description, Account_ID)
VALUES
(1, '2025-08-01 09:00:00', 'Deposit', 5000.00, 'Salary payment', 1),
(2, '2025-08-01 10:15:00', 'Withdrawal', 200.00, 'ATM cash withdrawal', 1),
(3, '2025-08-02 14:30:00', 'Deposit', 150.75, 'Gift from friend', 2),
(4, '2025-08-03 09:00:00', 'Transfer', 999.99, 'Sent to savings account', 3),
(5, '2025-08-03 16:45:00', 'Deposit', 500.00, 'Freelance project', 4),
(6, '2025-08-04 11:20:00', 'Withdrawal', 120.50, 'Grocery shopping', 2),
(7, '2025-08-05 08:10:00', 'Deposit', 75.25, 'Refund from store', 5),
(8, '2025-08-05 15:55:00', 'Withdrawal', 320.00, 'Utility bill payment', 5),
(9, '2025-08-06 13:05:00', 'Deposit', 560.40, 'Sold old furniture', 1),
(10, '2025-08-06 18:25:00', 'Withdrawal', 45.00, 'Coffee shop expenses', 1),
(11, '2025-08-07 12:00:00', 'Deposit', 785.99, 'Tax refund', 3),
(12, '2025-08-08 09:40:00', 'Withdrawal', 230.10, 'Online purchase', 4),
(13, '2025-08-09 07:50:00', 'Deposit', 100.00, 'Interest earned', 4),
(14, '2025-08-10 20:30:00', 'Withdrawal', 89.99, 'Dinner with friends', 2),
(15, '2025-08-11 21:15:00', 'Deposit', 1500.75, 'Side business income', 5);




CREATE TABLE Transfers(
    Transfer_ID INT PRIMARY KEY,
    Transfer_Amount decimal(15, 2) NOT NULL,
    Transfer_Date DATETIME DEFAULT CURRENT_TIMESTAMP,
    FromAccount_ID int not null,
    ToAccount_ID int not null,
    FOREIGN KEY (FromAccount_ID) REFERENCES Accounts(Account_ID),
    FOREIGN KEY (ToAccount_ID) REFERENCES Accounts(Account_ID)
);

INSERT INTO Transfers(Transfer_ID, Transfer_Amount, Transfer_Date,FromAccount_ID, ToAccount_ID)
VALUES
(1, 2500.00, '2025-08-01 10:15:00', 1, 2),
(2, 150.75,  '2025-08-02 14:30:00', 2, 3),
(3, 999.99,  '2025-08-03 09:00:00', 3, 4),
(4, 500.00,  '2025-08-04 16:45:00', 1, 3),
(5, 1200.50, '2025-08-05 11:20:00', 4, 1),
(6, 75.25,   '2025-08-06 08:10:00', 5, 1),
(7, 320.00,  '2025-08-06 15:55:00', 2, 5),
(8, 560.40,  '2025-08-07 13:05:00', 1, 4),
(9, 45.00,   '2025-08-07 18:25:00', 4, 1),
(10, 785.99, '2025-08-08 12:00:00', 3, 5),
(11, 230.10, '2025-08-09 09:40:00', 5, 3),
(12, 100.00, '2025-08-10 07:50:00', 1, 4),
(13, 3400.25,'2025-08-11 20:30:00', 4, 1),
(14, 89.99,  '2025-08-12 10:10:00', 3, 2),
(15, 1500.75,'2025-08-13 21:15:00', 2, 3);

Select * FROM CUSTOMERS;
-- This will show each Account_Type and its total balance
SELECT Account_Type, SUM(Balance) AS Total_Balance FROM Accounts GROUP BY Account_Type;

SELECT Customer_Name, Date_Of_Birth FROM Customers ORDER BY Date_Of_Birth ASC;

-- Shows only the first 5 customers from the table.
SELECT * FROM Customers LIMIT 5;

-- Finds customers whose names start with 'A'
SELECT * FROM Customers WHERE Customer_Name LIKE 'A%';

-- Selects accounts that belong to branch 1, 3, or 5.
SELECT * FROM Accounts WHERE Branch_ID IN (1, 3, 5);

-- Finds only active Savings or Current accounts
SELECT * FROM Accounts
WHERE (Account_Type = 'Savings' OR Account_Type = 'Current')AND Status = 'Active';

-- Shows all inactive accounts
SELECT * FROM Accounts WHERE NOT Status = 'Active';

-- Savings accounts with balance more than 20,000
SELECT * FROM Accounts WHERE Account_Type = 'Savings' AND Balance > 20000;

-- Either Savings accounts OR accounts with balance above 500,000
SELECT * FROM Accounts
WHERE Account_Type = 'Savings'OR Balance > 500000;

SELECT * FROM Accounts WHERE Balance > 100000;

-- Accounts with balance higher than the average balance
SELECT * FROM Accounts
WHERE Balance > (SELECT AVG(Balance) FROM Accounts);

START TRANSACTION;
UPDATE Accounts SET Balance = Balance - 5000 WHERE Account_ID = 1;
UPDATE Accounts SET Balance = Balance + 5000 WHERE Account_ID = 2;

-- Shows total funds in all accounts
SELECT SUM(Balance) AS Total_Funds FROM Accounts;

-- Lists all unique account types (no duplicates).
SELECT DISTINCT Account_Type FROM Accounts;

-- Counts number of active accounts
SELECT COUNT(*) AS Active_Accounts
FROM Accounts
WHERE Status = 'Active';

-- -- Finds the smallest balance
SELECT MIN(Balance) AS Min_Balance
FROM Accounts;

-- Finds the largest transfer amount
SELECT MAX(Transfer_Amount) AS Max_Transfer
FROM Transfers;

-- assign a unique sequential number to each account per customer based on balance
SELECT Customer_ID,Account_ID,Balance,ROW_NUMBER()OVER(PARTITION BY Customer_ID ORDER BY Balance DESC)AS row_num
FROM Accounts;


-- rank accounts based on balance
SELECT Customer_ID,Account_ID,Balance,RANK()OVER(PARTITION BY Customer_ID ORDER BY Balance DESC)AS account_rank,
DENSE_RANK()OVER(PARTITION BY Customer_ID ORDER BY Balance DESC)AS dense_account_rank
FROM Accounts;


-- distribute accounts into quartiles (or any N-tiles) based on balance
SELECT Account_ID,Balance,NTILE(4)OVER(ORDER BY Balance DESC)AS quartile
FROM Accounts;

-- compare current balance to previous and next account for each customer (lead-next, lag-previous)
SELECT Customer_ID,Account_ID,OpenDate,Balance,
LAG(Balance)OVER(PARTITION BY Customer_ID ORDER BY OpenDate)AS previous_balance,
LEAD(Balance)OVER(PARTITION BY Customer_ID ORDER BY OpenDate)AS next_balance
FROM Accounts;

-- inner join accounts with customers to get customer names and account balances
SELECT a.Account_ID,a.Balance,c.Customer_Name
FROM Accounts a
INNER JOIN Customers c ON a.Customer_ID=c.Customer_ID;

-- left join customers with accounts to include customers with no accounts
SELECT c.Customer_ID,c.Customer_Name,a.Account_ID,a.Balance
FROM Customers c
LEFT JOIN Accounts a ON c.Customer_ID=a.Customer_ID;

-- right join customers with accounts to include accounts with no matching customer
SELECT c.Customer_ID,c.Customer_Name,a.Account_ID,a.Balance
FROM Customers c
RIGHT JOIN Accounts a ON c.Customer_ID=a.Customer_ID;

-- union all combining active and inactive accounts
SELECT Account_ID,Balance,Status
FROM Accounts WHERE Status='Active'
UNION ALL
SELECT Account_ID,Balance,Status
FROM Accounts WHERE Status='Inactive';










