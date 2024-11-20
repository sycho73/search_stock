MySQL 데이터베이스 테이블
CREATE TABLE Users (
  user_id VARCHAR(50) PRIMARY KEY,
  user_password TEXT NOT NULL,
  user_email TEXT NOT NULL
);

CREATE TABLE Predictstocks (
  id INT AUTO_INCREMENT PRIMARY KEY,
  stock_name VARCHAR(20) NOT NULL,
  stock_code VARCHAR(20) UNIQUE
);

CREATE TABLE Onedaypredict (
  id INT AUTO_INCREMENT PRIMARY KEY,
  stock_code VARCHAR(20),
  price30min DECIMAL(10,2),
  price60min DECIMAL(10,2),
  price90min DECIMAL(10,2),
  price120min DECIMAL(10,2),
  price150min DECIMAL(10,2),
  price180min DECIMAL(10,2),
  price210min DECIMAL(10,2),
  price240min DECIMAL(10,2),
  price270min DECIMAL(10,2),
  price300min DECIMAL(10,2),
  price330min DECIMAL(10,2),
  price360min DECIMAL(10,2),
  price390min DECIMAL(10,2),
  price420min DECIMAL(10,2),
  FOREIGN KEY (stock_code) REFERENCES Predictstocks(stock_code)
);

CREATE TABLE Oneweekpredict (
  id INT AUTO_INCREMENT PRIMARY KEY,
  stock_code VARCHAR(20),
  price1day DECIMAL(10,2),
  price2day DECIMAL(10,2),
  price3day DECIMAL(10,2),
  price4day DECIMAL(10,2),
  price5day DECIMAL(10,2),
  price6day DECIMAL(10,2),
  price7day DECIMAL(10,2),
  FOREIGN KEY (stock_code) REFERENCES Predictstocks(stock_code)
);

CREATE TABLE Onemonthpredict (
  id INT AUTO_INCREMENT PRIMARY KEY,
  stock_code VARCHAR(20),
  price3day DECIMAL(10,2),
  price6day DECIMAL(10,2),
  price9day DECIMAL(10,2),
  price12day DECIMAL(10,2),
  price15day DECIMAL(10,2),
  price18day DECIMAL(10,2),
  price21day DECIMAL(10,2),
  price24day DECIMAL(10,2),
  price27day DECIMAL(10,2),
  price30day DECIMAL(10,2),
  FOREIGN KEY (stock_code) REFERENCES Predictstocks(stock_code)
);

CREATE TABLE Userrating (
  id INT AUTO_INCREMENT PRIMARY KEY,
  stock_code VARCHAR(20),
  user_id VARCHAR(50),
  rating DECIMAL(2,1),
  content VARCHAR(500),
  FOREIGN KEY (stock_code) REFERENCES Predictstocks(stock_code),
  FOREIGN KEY (user_id) REFERENCES Users(user_id)
);

CREATE TABLE Userfavorite (
  id INT AUTO_INCREMENT PRIMARY KEY,
  user_id VARCHAR(50),
  stock_code VARCHAR(20),
  FOREIGN KEY (user_id) REFERENCES Users(user_id),
  FOREIGN KEY (stock_code) REFERENCES Predictstocks(stock_code)
);
