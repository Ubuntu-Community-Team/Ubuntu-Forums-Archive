---
title: "Evolution: AddressBook lost after re-install"
date: 2009-08-13
forum: General Help
---

### Post by UranUtan on 2009-08-13
Hi,
Using Ubuntu 9.04 x64. I have had instabilities issues caused by the upgraded 8.10 -> 9.04. I ended up re-installing 9.04 x64, overwritting 8.10 x64.

I have /home on a separate partition so most of application settings are recovered. However, Evolution seems to lose some settings. The minor one is the email, SMTP, POP settings. But a bigger one is that only the first address book is visible. All other address books are not displayed and yet I see them in the .evolution hidden folfer in the form of:

> /home/myusername/.evolution/addressbook/local/1241917004.3776.2@MyMachineName
   addressbook.db
   addressbook.db.summary
/home/myusername/.evolution/addressbook/local/1241917004.3776.3@MyMachineName
   addressbook.db
   addressbook.db.summary
/home/myusername/.evolution/addressbook/local/1241917004.3776.4@MyMachineName
  etc.

Is there anyway to recover these address books?

Thanks in advance for any help.

---

### Post by fballem on 2009-08-13
Could you please check to see if there are entries for addressbook.db and addressbook.db.summary in the following folder:

/home/yourusername/.evolution/addressbook/local/system

If there is, then you could use Nautilus to copy the entries from one of the folders that you mentioned in your original post to this location (replace the current files), To do this, open Nautilus by selecting Home from the Places menu.

If you don't know how to do this, then please let us know.

A suggestion for the future would be to use the backup feature in Evolution, which will make a .tar.gz file containing your e-mails, calendar, and address book. When you have completed a re-install, you can start Evolution and restore these from the backup.

In spite of having a separate /home partition, you should always have a backup of your important data, including the evolution backup, on an external media (like a large USB drive). That way, if you have a failure, such as a hard drive, you will be able to re-install with minimal loss.

Hope this helps,

---

### Post by dcstar on 2009-08-13
> **UranUtan said:**
> Hi,
Using Ubuntu 9.04 x64. I have had instabilities issues caused by the upgraded 8.10 -> 9.04. I ended up re-installing 9.04 x64, overwritting 8.10 x64.

I have /home on a separate partition so most of application settings are recovered. However, Evolution seems to lose some settings. The minor one is the email, SMTP, POP settings. But a bigger one is that only the first address book is visible. All other address books are not displayed and yet I see them in the .evolution hidden folfer in the form of:


And you have gone into the Evolution settings and enabled these extra Address Books?

---

### Post by UranUtan on 2009-08-13
> **dcstar said:**
> And you have gone into the Evolution settings and enabled these extra Address Books?

I went through all Evolution settings and failed to see any option related to extra Address Books. Can you please indicate where is this option?

---

### Post by UranUtan on 2009-08-14
Problem solved. Actually not really, I still had the Contact Export files from Thunderbird. I just recreated new Address Books and import again.

Looking in /home/myusername/.evolution/addressbook/local/ I notice that the random folder has changed from 1241917004.3776.2@MyMachineName to 1250221043.6579.2@MyMachineName

I guess that with some renaming and fooling around after a months, I would probably succeed to recover manually the address books lost by the re-installation. But the re-import is way faster. So finally I am no longer interested by the solution.

For sure Backup is the way to go and I am going now to abuse this function frequently.

---

### Post by SusieSA on 2010-02-01
> **fballem said:**
> Could you please check to see if there are entries for addressbook.db and addressbook.db.summary in the following folder:

/home/yourusername/.evolution/addressbook/local/system

If there is, then you could use Nautilus to copy the entries from one of the folders that you mentioned in your original post to this location (replace the current files), To do this, open Nautilus by selecting Home from the Places menu.

If you don't know how to do this, then please let us know.

A suggestion for the future would be to use the backup feature in Evolution, which will make a .tar.gz file containing your e-mails, calendar, and address book. When you have completed a re-install, you can start Evolution and restore these from the backup.

In spite of having a separate /home partition, you should always have a backup of your important data, including the evolution backup, on an external media (like a large USB drive). That way, if you have a failure, such as a hard drive, you will be able to re-install with minimal loss.

Hope this helps,



I am also having a problem with contact import.  I've just trashed my old 8.04 and totally reinstalled Ubuntu 9.10.  Everything looks good except for the Evolution Contacts.  As suggested above, I created a .tar.gz file of all emails, address book entries etc and I've unzipped this.  When I look in Evolution, all my emails are there, but no Contacts.  

In the /.evolution/addressbook/local  directory, the following exists:
[SIZE="4"][SIZE="1"]
drwxr-xr-x 2 sally sally 4096 2010-01-20 11:10 1205755104.5365.0@sally-desktop
drwxr-xr-x 2 sally sally 4096 2010-01-20 22:03 1205755118.5365.1@sally-desktop
drwxr-xr-x 2 sally sally 4096 2009-07-13 13:57 1205755131.5365.2@sally-desktop
drwxr-xr-x 2 sally sally 4096 2010-01-25 15:16 1205755181.5365.5@sally-desktop
drwxr-xr-x 2 sally sally 4096 2010-02-01 17:01 1205755263.5365.12@sally-desktop
drwxr-xr-x 2 sally sally 4096 2010-02-01 17:08 system[/SIZE][/SIZE]

and, in any of these folders, there is a 'addressbook.db' and a 'addressbook.db.summary' file in which, if I edit, I can see my contacts.

How do I get the contacts out of these files into my address book in Evolution?

Thanks for your help.

---

### Post by SusieSA on 2010-02-01
I have fixed this problem by deleting the .evolution folder and other folders that I had extracted to.  Then I re-extracted my archive using the tar command in the terminal window.

This worked fine.

The previous time, I had used the GUI archive manager to extract the file.

---

