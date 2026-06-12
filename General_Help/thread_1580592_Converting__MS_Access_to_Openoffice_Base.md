---
title: "Converting  MS Access to Openoffice Base"
date: 2010-09-23
forum: General Help
---

### Post by madsmaddad on 2010-09-23
Everywhere I read, this seems to come up as a very difficult thing. 

Just want to record how I did it.

In Access, export the table to an Excel Spreadsheet.

Using Openoffice, open the Spreadsheet, but save as an Openoffice (.ods) spreadsheet.  ( Note - According to the Base help files, if you import an Excel Spreadsheet, it is read-only)

Open Base and Create a database. No tables, no nothing, just create.  Now Open this and and also Open the spreadsheet. Select all the data in the spreadsheet, 'copy' it, and in the Database tables area, 'paste' it. 

I had problems in that it wanted to create a primary key, so added an extra field. 

I then went into the database design view, right click on the appropriate field to make that the primary key, and remove the primary key from the unwanted field. 

Delete the excess column.

This is just for a single flat table, with no linking to other tables.

I hope that this helps someone. I did it for a membership database table, and have been able to replicate the query to filter  for the Snailmail folks (Those that did not have an email address in the table).

Still trying to figure out how to do an envelopes report though. 

Cheers,

---

### Post by Zimmer on 2010-09-23
Saving from Openoffice as a .dbf file is good. Pop your dbf files in a folder, create and open your Database (or use the one already created :) ) and Right click on the empty pane for a 'Database' menu , select <connection type>  make sure it says Dbase on the form that opens, click <Next> and point it to the folder with the dbf file(s).

Tables should appear in your Database...

EDIT:
(try <View> Refresh Tables if they do not.....)

---

### Post by Zimmer on 2010-09-23
As for your 'Envelope' Report, do you mean you wish to print labels for envelopes?
Brief outline .....
If so, to do this you create Labels New>Label (better, a Template of a label to use later) . if you have a look at that you will see how to follow the Wizard to create a template for address labels (Avery or whatever Brand you use in drop down list) .

save template
Use F4 key to bring up the database select the table then records you want in labels and click the Data to Fields icon....
F4 will toggle the database bar off again...
Print..

---

### Post by madsmaddad on 2010-09-24
No, not labels. I feed in and print directly to the envelopes in the Access system. I even have a logo on it. 

I think I built that from a blank report many moons ago. In Base I am forced to use the wizard, and now I am trying to modify the default to one record per page, in DL10 format.

And in response to your suggestion for using dbase format as an intermediary, is the result read-only as it is if you go direct via Excel, without saving as an Ods format?


Mmd.

---

### Post by Zimmer on 2010-09-24
[http://www.tutorialsforopenoffice.org/tutorial/Print_An_Envelope.html](http://www.tutorialsforopenoffice.org/tutorial/Print_An_Envelope.html)
or

[http://wiki.services.openoffice.org/wiki/Documentation/OOoAuthors_User_Manual/Writer_Guide/Printing_envelopes](http://wiki.services.openoffice.org/wiki/Documentation/OOoAuthors_User_Manual/Writer_Guide/Printing_envelopes)

[http://openoffice.blogs.com/openoffice/2005/12/printing_envelo.html](http://openoffice.blogs.com/openoffice/2005/12/printing_envelo.html)

Not had time to read all and test them through yet....
EDIT:
and this Chapter 11...

[http://documentation.openoffice.org/manuals/oooauthors2/](http://documentation.openoffice.org/manuals/oooauthors2/)

And to cap it all..
[http://templates.services.openoffice.org/en/search/node/envelope](http://templates.services.openoffice.org/en/search/node/envelope)

---

### Post by Zimmer on 2010-09-24
> **madsmaddad said:**
> No, not labels. 

And in response to your suggestion for using dbase format as an intermediary, is the result read-only as it is if you go direct via Excel, without saving as an Ods format?


Mmd.

It is NOT read-only..
In my experience .xls files are  opened read/write and can be saved to .xls or any other available format... (just experimented on an old Excel file..)

---

