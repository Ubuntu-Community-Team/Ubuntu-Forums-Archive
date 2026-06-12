---
title: "Libre Office automation ideas wanted"
date: 2012-10-10
forum: General Help
---

### Post by bill-lancaster on 2012-10-10
I have a property management programme written in Gambas.
At the moment, to send a letter to a tenant I open a template annd cut & paste key data (name, address etc).

What would be the best way to automate this?

Any ideas would be welcome.

Ubuntu 12.04
KDE 4.8.1
Gambas3

---

### Post by audiomick on 2012-10-10
I have no idea how to realise it, but basically I think you would need to have Gambas putting it's contact info into a Contact file that Libre office can access. I do this to write invoices. I have a template set up for Open Office and have it accessing my contact data from evolutoion. Then, when I open the template, there is a section at the top where I can search the name of the reciever and then automatically insert the data in the fields on the template. The fields are available in Open Office under the "insert" menu. They are called "Feldbefehl" in German, which is roughly "field command".

So, I would suggest looking into how and which Contact data Libre office can access, and a way to get Gamba to write you contacts there into a Contact bank that Libre Office can access.

---

### Post by bill-lancaster on 2012-10-10
A good start, thank you Michael.

I can easily write the data to a file.  Just need to get to grips with data fields in OO

Thanks

---

### Post by Vaphell on 2012-10-10
in my work we use open office templates that the custom ruby script fills with data.
.odt is just a zipped bunch of xml and stuff - see for yourself. The script unzips the file, looks for user defined fields in content.xml which look like this:
```
... <text:s/><text:user-field-get text:name="FIELD_NAME">???</text:user-field-get> ... 
```
fills them with data or should i say replaces them with the end value and zips everything again.

all you need in this low level approach is a bit of python with imported zip (to uncompress and compress again) and xml libs (to parse and modify xml)

---

### Post by drdos2006 on 2012-10-10
Gambas can access a MySQL database, maybe that is an option as well.

regards

---

### Post by Zimmer on 2012-10-10
OK, 
Create your Name and address file - best solution from scratch is a spreadsheet with column headings containing field names for the Data eg, FULLNAME, ADDRESS1,ADDRESS2 etc.
Save this file(single sheet of spreadsheet)  as a .dbf file and place it in the biblio folder in the hidden Libreoffice/OpenOffice Database folder in your /home/username directory.
( You may also be able to create/export a .dbf from the Gambas data directly or as .csv to Calc then to .dbf ?)

If you then create a letter and use
 insert>fields>other 
a dialog box will appear , select the 'Database' tab, select 'Mail Merge Fields' in the left hand column
and select the field you require from the expanded list under your address table name you stored in the biblio folder and click on the 'Insert' button.

Repeat for more fields...

Save this as a .ott template.

When you open the Template with Writer, press F4 to show the Database tables at the top.
Select your table. Select the record you require and click the icon for 'Data to Fields' .

Viola!

By using an Avery label template(3x7 labels) you can select 21 addresses at a time for a mail shot, or xmas card labels :)
The Mail merge wizard (never used it) may help in creating a mail shot using the Database....
Hope this helped...

EDIT ps.
The latest location for the biblio folder in Mint 13 is /home/username/.config/libreoffice/3/user/database/biblio/

In Ubuntu 10.04 it was /home/username/.openoffice.org/3/user/database/biblio/

---

