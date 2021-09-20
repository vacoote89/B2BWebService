# B2B Web Service

In this activity we will create a Web Service based on the following XML documents.

### po.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<po id="43871" submitted="2004-01-05" customerId="73852">
	
	<billTo id="addr-1">
		<company>The Skateboard Warehouse</company>
		<street>One Warehouse Park</street>
		<street>Building 17</street>
		<city>Boston</city>
		<state>MA</state>
		<postalCode>01775</postalCode>
	</billTo>
	<shipTo href="addr-1"/>
	<order>
		<item sku="318-BP" quantity="5">
			<description>
				Skateboard backpack; five pockets
			</description>
		</item>
		<item sku="947-TI" quantity="12">
			<description>
				Street-style titanium skateboard.
			</description>
		</item>
		<item sku="008-PR" quantity="1000"/>
	</order>
</po>
```

### invoice.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<invoice:invoice xmlns:invoice="http://www.skatestown.com/ns/invoice"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://www.skatestown.com/ns/invoice http://www.skatestown.com/schema/invoice.xsd" 
	id="43871" submitted="2004-01-05" customerId="73852">
	
	<billTo id="addr-1">
		<company>The Skateboard Warehouse</company>
		<street>One Warehouse Park</street>
		<street>Building 17</street>
		<city>Boston</city>
		<state>MA</state>
		<postalCode>01775</postalCode>
	</billTo>
	<shipTo href="addr-1"/>
	<order>
		<item sku="318-BP" quantity="5" unitPrice="49.95">
			<description>Skateboard backpack; five pockets</description>
		</item>
		<item sku="947-TI" quantity="12" unitPrice="129.00">
			<description>Street-style titanium skateboard.</description>
		</item>
		<item sku="008-PR" quantity="1000" unitPrice="0.00">
			<description>Promotional: SkatesTown stickers</description>
		</item>
	</order>
	<tax>89.89</tax>
	<shippingAndHandling>200</shippingAndHandling>
	<totalCost>2087.64</totalCost>
	
</invoice:invoice>
```

## Starting the project

We will be starting a new project. We will be creating a Java with Maven Project. Maven is a repository that has many Java classes that we can add to our project.

In NetBeans:
1. Select **New Project > Java with Maven > Project from Archetype**
1. Search for for *glassfish* and select **jersey-quickstart-webapp**
1. Name your project and click Finish.

## Dependencies

Your classes and web service will utilize existing Java Classes. Some of these classes are already part of your project. Some need to be added. We add classes by adding dependencies. This adds the compiled version of the required class to the project. 

In the `pom.xml` file under the `<dependencies>` add the following:

```xml
<dependency>
	<groupId>com.liferay</groupId>
	<artifactId>javax.jws-api</artifactId>
	<version>1.1.0.LIFERAY-PATCHED-1</version>
	<type>jar</type>
</dependency>
<dependency>
	<groupId>javax</groupId>
	<artifactId>javaee-api</artifactId>
	<version>8.0.1</version>
</dependency>
<dependency>
	<groupId>javax.xml.bind</groupId>
	<artifactId>jaxb-api</artifactId>
	<version>2.4.0-b180830.0359</version>
</dependency>
```
 
## Adding Local Server

For this activity we will be using a local server on your computer. This server is call Payara. Payara is a Glassfish server with some additional functionality. This environment will host your web service and allow us to view the results of our code in the browser and with SOAPUI.

To add a server in NetBeans:
1. Select **Tools > Servers**
1. Click *Add Server*
1. Select `Payara Server`
1. Select the checkbox to agree to the terms and then click *Download*
	1. When the download is complete, click *Next*
1. Give your domain a name. Then click Finish.
	1. You don't need to set the username and password.

## Classes

Under `Source Packages` right click on the package name and choose **New > Package**. Name the package `model`.

In the new model packagage, recreate the classes we made previously:
- Address
- Item
- PO
- InvoiceItem
- Invoice

*Don't forget to include all the getters, setters, and constructors.*

## Web Service

We will be creating a web service with the following functionality:
- Display all purchase orders
- Find a purchase order by the id
- Find a purchase order by the submitted date
- Display all invoices
- Find a invoice by the id
- Display all invoices by customerId

# License

[License](LICENSE)
