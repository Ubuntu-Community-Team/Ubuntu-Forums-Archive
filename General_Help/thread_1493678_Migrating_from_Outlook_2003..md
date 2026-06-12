---
title: "Migrating from Outlook 2003."
date: 2010-05-26
forum: General Help
---

### Post by WarrenL on 2010-05-26
Hi folks,

Friends have asked me if I can upgrade their laptop from Windows XP to Ubuntu. Of course I can! Except I don't know the best way to transfer their email and account data from Outlook 2003 to Thunderbird/Evolution. I googled the forum for this subject but only found some old threads from several years ago. Surely times have changed since then and there is some new advice to be had?

Thanks again,
Warren

---

### Post by Joe of loath on 2010-05-26
The evolution setup wizard asks if you want to restore from a backup file. Can you export the outlook emails to a backup file, and see if it will import into evolution?

---

### Post by jarviser on 2010-05-26
Not much has changed - Microsoft never make it easy to migrate away from them. It's only a problem if the user holds messages on the PC in local folders. If they are all on the Webmail "POP" service then you simply need to sign up to the POP service in the Thunderbird setup.

If you do need to convert the Outlook personal message folders, it will usually involve installing both Thunderbird and Outlook Express on the XP partition first. Import folders from Outlook 2003 into Outlook Express and then import into Thunderbird from Outlook Express. Then copy the thunderbird personal folders to the Ubuntu machine.  

Alternatively you can drag the contents of each Outlook folder in turn into the "Inbox" which should place the messages back into the POP service. (Takes a while) Then open the POP mail in Thunderbird and move them from that inbox into a new folder there.

For address book/contacts, export into a comma separated (CSV) file and import into Thunderbird. NB you may find that the fields are not in the right "columns". When I converted I exported contacts as CSV, imported into Thunderbird. Then created a fresh contact and exported straight out again to another CSV file and checked that all the fields in the CSV lined up with the fresh contact. They didn't and I edited the CSV file in OpenOffice Spreadsheet. Keep the CSV as backup.

See here [http://kb.mozillazine.org/Import_.pst_files](http://kb.mozillazine.org/Import_.pst_files) and similar articles.

---

### Post by obscurant1st on 2010-05-26
I think thunderbird can help u in this matter. But not sure though. Why dont you give it a try in windows itself before migrating. If it works in windows, then surely it will work in linux. :)

---

### Post by WarrenL on 2010-05-26
Thanks folks, it looks like we're heading in the right direction. It's happening this weekend so I'll try installing Thunderbird in XP in the interim and see how far I get.

---

### Post by pcrepairguy on 2011-07-09
There is a great solution @ [http://outport.sourceforge.net/](http://outport.sourceforge.net/)

Run this tool from Window$ with Outllook open and it will export your PST to format you need to import into EVOLUTION

---

### Post by haqking on 2011-07-09
evolutiuon will import a .pst file amongst many others

---

