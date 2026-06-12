---
title: "Importing Outlook .pst files to Ubuntu Evolution Mail"
date: 2012-04-24
forum: General Help
---

### Post by isalovell on 2012-04-24
I'm on Ubuntu and did a back-up of .PST files for Outlook mail amounting to 1.6GB and need to do a restore of the mail to Ubuntu's Evolution Mail client. The problem is that the client will only do an import of mail from a PST file which is less than 1GB. Any ideas on how to shrink it to less than a gig? All suggestions will be appreciated. Thanks in advance.

---

### Post by sanderj on 2012-04-24
I have no experience with .PST, but:

Do you get an error?

Have you tried the command line tool 'readpst'?

---

### Post by megabuffen on 2012-04-24
I have no idea how to import such a large file, but there may be some workarounds.

1. Instead of doing a complete export from outlook, try manually selecting some emails and exporting them to a PST file. You should get two files that are smaller.

2. Transfer your email messages to separate files and delete them from outlook before exporting.

3. Do you you have an email account that supports IMAP? If so, you can set it up in outlook and transfer your email to this account. You can then use this account with evolution. This option brings the added advantage of being able to have all you email synchronized across different computers. I use this option with GMail, and Evolution even syncs my calendars and contacts.

---

### Post by Mark Phelps on 2012-04-24
You can't import .pst files, but you can export from Outlook into files you then CAN import.  See the link below:

[http://askubuntu.com/questions/84239/import-pst-in-evolution-3-2-1]("http://askubuntu.com/questions/84239/import-pst-in-evolution-3-2-1")

---

### Post by techsupport on 2012-04-24
> **Mark Phelps said:**
> You can't import .pst files, but you can export from Outlook into files you then CAN import.  See the link below:

[http://askubuntu.com/questions/84239/import-pst-in-evolution-3-2-1](http://askubuntu.com/questions/84239/import-pst-in-evolution-3-2-1)

Go down the list until you get to Thunderbird. There is a app that will convert your PST file for you that you need to install in Evolution here:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

### Post by dcstar on 2012-04-24
> **Mark Phelps said:**
> You can't import .pst files, 
.........

Then why does Evolution have a specific Outlook PST Import plugin?

---

### Post by dcstar on 2012-04-24
> **isalovell said:**
> I'm on Ubuntu and did a back-up of .PST files for Outlook mail amounting to 1.6GB and need to do a restore of the mail to Ubuntu's Evolution Mail client. The problem is that the client will only do an import of mail from a PST file which is less than 1GB. Any ideas on how to shrink it to less than a gig? All suggestions will be appreciated. Thanks in advance.

You have not specified what version of Evolution you are using, but they should all import PST files up to 2GB in size.

Run a **scanpst** on the Outlook file in Windows, chances are it contains errors which are preventing the import.

---

### Post by techsupport on 2012-04-25
> **dcstar said:**
> Then why does Evolution have a specific Outlook PST Import plugin?

To find out if you have a corrupted PST file, naturally we would want use the converter to find out. It might be able to fix it too. Don't know until you try.

Cheers

---

