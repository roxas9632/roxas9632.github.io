# 專案使用說明


## 資料庫

USE [master]
GO
/****** Object:  Database [goshopping]    Script Date: 2021/7/6 上午 11:02:26 ******/
CREATE DATABASE [goshopping]
 CONTAINMENT = NONE
 ON  PRIMARY 
( NAME = N'goshopping', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER1\MSSQL\DATA\goshopping.mdf' , SIZE = 8192KB , MAXSIZE = UNLIMITED, FILEGROWTH = 65536KB )
 LOG ON 
( NAME = N'goshopping_log', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER1\MSSQL\DATA\goshopping_log.ldf' , SIZE = 8192KB , MAXSIZE = 2048GB , FILEGROWTH = 65536KB )
 WITH CATALOG_COLLATION = DATABASE_DEFAULT
GO
ALTER DATABASE [goshopping] SET COMPATIBILITY_LEVEL = 150
GO
IF (1 = FULLTEXTSERVICEPROPERTY('IsFullTextInstalled'))
begin
EXEC [goshopping].[dbo].[sp_fulltext_database] @action = 'enable'
end
GO
ALTER DATABASE [goshopping] SET ANSI_NULL_DEFAULT OFF 
GO
ALTER DATABASE [goshopping] SET ANSI_NULLS OFF 
GO
ALTER DATABASE [goshopping] SET ANSI_PADDING OFF 
GO
ALTER DATABASE [goshopping] SET ANSI_WARNINGS OFF 
GO
ALTER DATABASE [goshopping] SET ARITHABORT OFF 
GO
ALTER DATABASE [goshopping] SET AUTO_CLOSE OFF 
GO
ALTER DATABASE [goshopping] SET AUTO_SHRINK OFF 
GO
ALTER DATABASE [goshopping] SET AUTO_UPDATE_STATISTICS ON 
GO
ALTER DATABASE [goshopping] SET CURSOR_CLOSE_ON_COMMIT OFF 
GO
ALTER DATABASE [goshopping] SET CURSOR_DEFAULT  GLOBAL 
GO
ALTER DATABASE [goshopping] SET CONCAT_NULL_YIELDS_NULL OFF 
GO
ALTER DATABASE [goshopping] SET NUMERIC_ROUNDABORT OFF 
GO
ALTER DATABASE [goshopping] SET QUOTED_IDENTIFIER OFF 
GO
ALTER DATABASE [goshopping] SET RECURSIVE_TRIGGERS OFF 
GO
ALTER DATABASE [goshopping] SET  DISABLE_BROKER 
GO
ALTER DATABASE [goshopping] SET AUTO_UPDATE_STATISTICS_ASYNC OFF 
GO
ALTER DATABASE [goshopping] SET DATE_CORRELATION_OPTIMIZATION OFF 
GO
ALTER DATABASE [goshopping] SET TRUSTWORTHY OFF 
GO
ALTER DATABASE [goshopping] SET ALLOW_SNAPSHOT_ISOLATION OFF 
GO
ALTER DATABASE [goshopping] SET PARAMETERIZATION SIMPLE 
GO
ALTER DATABASE [goshopping] SET READ_COMMITTED_SNAPSHOT OFF 
GO
ALTER DATABASE [goshopping] SET HONOR_BROKER_PRIORITY OFF 
GO
ALTER DATABASE [goshopping] SET RECOVERY FULL 
GO
ALTER DATABASE [goshopping] SET  MULTI_USER 
GO
ALTER DATABASE [goshopping] SET PAGE_VERIFY CHECKSUM  
GO
ALTER DATABASE [goshopping] SET DB_CHAINING OFF 
GO
ALTER DATABASE [goshopping] SET FILESTREAM( NON_TRANSACTED_ACCESS = OFF ) 
GO
ALTER DATABASE [goshopping] SET TARGET_RECOVERY_TIME = 60 SECONDS 
GO
ALTER DATABASE [goshopping] SET DELAYED_DURABILITY = DISABLED 
GO
ALTER DATABASE [goshopping] SET ACCELERATED_DATABASE_RECOVERY = OFF  
GO
EXEC sys.sp_db_vardecimal_storage_format N'goshopping', N'ON'
GO
ALTER DATABASE [goshopping] SET QUERY_STORE = OFF
GO
USE [goshopping]
GO
/****** Object:  Table [dbo].[Carts]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Carts](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[lot_no] [nvarchar](50) NULL,
	[user_no] [nvarchar](50) NULL,
	[product_no] [nvarchar](50) NULL,
	[product_name] [nvarchar](250) NULL,
	[product_spec] [nvarchar](250) NULL,
	[qty] [int] NULL,
	[price] [int] NULL,
	[amount] [int] NULL,
	[crete_time] [datetime] NULL,
 CONSTRAINT [PK_Carts] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Categorys]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Categorys](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[parentid] [int] NULL,
	[category_no] [nvarchar](50) NULL,
	[category_name] [nvarchar](50) NULL,
 CONSTRAINT [PK_Categorys] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Companys]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Companys](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[mno] [nvarchar](50) NULL,
	[msname] [nvarchar](50) NULL,
	[mname] [nvarchar](250) NULL,
	[date_register] [date] NULL,
	[tel_company] [nvarchar](50) NULL,
	[fax_company] [nvarchar](50) NULL,
	[name_charge] [nvarchar](50) NULL,
	[name_contact] [nvarchar](50) NULL,
	[tel_contact] [nvarchar](50) NULL,
	[adr_company] [nvarchar](250) NULL,
	[email_company] [nvarchar](250) NULL,
	[url_company] [nvarchar](250) NULL,
	[remark] [nvarchar](250) NULL,
 CONSTRAINT [PK_Companys] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Orders]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Orders](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[order_no] [nvarchar](50) NULL,
	[order_date] [datetime] NULL,
	[order_status] [nvarchar](50) NULL,
	[user_no] [nvarchar](50) NULL,
	[payment_no] [nvarchar](50) NULL,
	[shipping_no] [nvarchar](50) NULL,
	[receive_name] [nvarchar](50) NULL,
	[receive_email] [nvarchar](50) NULL,
	[receive_address] [nvarchar](250) NULL,
	[amounts] [int] NULL,
	[taxs] [int] NULL,
	[totals] [int] NULL,
	[remark] [nvarchar](250) NULL,
	[order_guid] [nvarchar](50) NULL,
	[order_closed] [int] NULL,
	[order_validate] [int] NULL,
 CONSTRAINT [PK_Orders] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[OrdersDetail]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[OrdersDetail](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[order_no] [nvarchar](50) NULL,
	[vendor_no] [nvarchar](50) NULL,
	[category_name] [nvarchar](50) NULL,
	[product_no] [nvarchar](50) NULL,
	[product_name] [nvarchar](250) NULL,
	[product_spec] [nvarchar](250) NULL,
	[price] [int] NULL,
	[qty] [int] NULL,
	[amount] [int] NULL,
	[remark] [nvarchar](250) NULL,
 CONSTRAINT [PK_OrdersDetail] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Payments]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Payments](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[mno] [nvarchar](50) NULL,
	[mname] [nvarchar](50) NULL,
	[remark] [nvarchar](250) NULL,
 CONSTRAINT [PK_Payments] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Products]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Products](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[categoryid] [int] NULL,
	[category_name] [nvarchar](250) NULL,
	[istop] [int] NULL,
	[ishot] [int] NULL,
	[issale] [int] NULL,
	[browse_count] [int] NULL,
	[vendor_no] [nvarchar](50) NULL,
	[product_no] [nvarchar](50) NULL,
	[product_name] [nvarchar](250) NULL,
	[product_spec] [nvarchar](250) NULL,
	[price_cost] [int] NULL,
	[price_sale] [int] NULL,
	[price_discont] [int] NULL,
	[start_count] [int] NULL,
	[remark] [nvarchar](max) NULL,
 CONSTRAINT [PK_Products] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY] TEXTIMAGE_ON [PRIMARY]
GO
/****** Object:  Table [dbo].[ProductsCategory]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[ProductsCategory](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[vendor_no] [nvarchar](50) NULL,
	[mno] [nvarchar](50) NULL,
	[mname] [nvarchar](50) NULL,
	[remark] [nvarchar](250) NULL,
 CONSTRAINT [PK_ProductsCategory] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[ProductsProperty]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[ProductsProperty](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[product_no] [nvarchar](50) NULL,
	[property_no] [nvarchar](50) NULL,
	[text_value] [nvarchar](500) NULL,
	[remark] [nvarchar](250) NULL,
 CONSTRAINT [PK_ProductsProperty] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Propertys]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Propertys](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[mno] [nvarchar](50) NULL,
	[mname] [nvarchar](50) NULL,
	[mvalue] [nvarchar](500) NULL,
	[remark] [nvarchar](250) NULL,
 CONSTRAINT [PK_Propertys] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Roles]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Roles](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[mno] [nvarchar](50) NULL,
	[mname] [nvarchar](50) NULL,
	[remark] [nvarchar](250) NULL,
 CONSTRAINT [PK_Roles] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Shippings]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Shippings](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[mno] [nvarchar](50) NULL,
	[mname] [nvarchar](50) NULL,
	[remark] [nvarchar](250) NULL,
 CONSTRAINT [PK_Shippings] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Status]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Status](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[mno] [nvarchar](50) NULL,
	[mname] [nvarchar](50) NULL,
	[remark] [nvarchar](250) NULL,
 CONSTRAINT [PK_Status] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Users]    Script Date: 2021/7/6 上午 11:02:26 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Users](
	[rowid] [int] IDENTITY(1,1) NOT NULL,
	[mno] [nvarchar](50) NULL,
	[mname] [nvarchar](50) NULL,
	[password] [nvarchar](50) NULL,
	[email] [nvarchar](250) NULL,
	[role_no] [nvarchar](50) NULL,
	[birthday] [datetime] NULL,
	[remark] [nvarchar](250) NULL,
	[varify_code] [nvarchar](50) NULL,
	[isvarify] [int] NULL,
 CONSTRAINT [PK_Users] PRIMARY KEY CLUSTERED 
(
	[rowid] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
ALTER TABLE [dbo].[Orders] ADD  CONSTRAINT [DF_Orders_order_closed]  DEFAULT ((0)) FOR [order_closed]
GO
ALTER TABLE [dbo].[Orders] ADD  CONSTRAINT [DF_Orders_order_validate]  DEFAULT ((0)) FOR [order_validate]
GO
ALTER TABLE [dbo].[Products] ADD  CONSTRAINT [DF_Products_istop]  DEFAULT ((0)) FOR [istop]
GO
ALTER TABLE [dbo].[Products] ADD  CONSTRAINT [DF_Products_ishot]  DEFAULT ((0)) FOR [ishot]
GO
ALTER TABLE [dbo].[Products] ADD  CONSTRAINT [DF_Products_issale]  DEFAULT ((1)) FOR [issale]
GO
ALTER TABLE [dbo].[Products] ADD  CONSTRAINT [DF_Products_browse_count]  DEFAULT ((0)) FOR [browse_count]
GO
ALTER TABLE [dbo].[Products] ADD  CONSTRAINT [DF_Products_start_count]  DEFAULT ((5)) FOR [start_count]
GO
USE [master]
GO
ALTER DATABASE [goshopping] SET  READ_WRITE 
GO


## 簡單操作說明

## 帳密
管理者:admin/admin
公司:V01/V01
使用者:001/001
