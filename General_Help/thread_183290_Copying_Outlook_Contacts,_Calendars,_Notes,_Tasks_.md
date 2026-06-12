---
title: "Copying Outlook Contacts, Calendars, Notes, Tasks and Mail to Evolution"
date: 2006-05-27
forum: General Help
---

### Post by mtappenden on 2006-05-27
Hi there,

I found that Evolution can't support .pst files pretty quick, so I found Outport ([http://outport.sourceforge.net](http://outport.sourceforge.net)) which looks awesome it saved my Contacts, Calendar and Tasks to Evolution compatible files. So I saved those to a folder called Evolution and put them on my pen drive. I started by copying Evolution/local/Contacts all the stuff from in thre into ~/.evolution/addressbook/local/system then I opened up Evolution and clicked Contacts and nothing is in there. Anyone know why this is and how to fix?

Sorry if this question sounds a bit dumb, but I'm a mac user and my parents use Windows and have just decided to give Ubuntu a try after getting sick of reformatting their PC every few months and not wanting to pay the cash for a Mac at the moment.

Thanks
Max

---

### Post by skippy81 on 2006-05-27
Right, evolution appears to look for two files - adressbook.db and addressbook.db.summary. 

You need to rename the adressbook file you copy in to addressbook.db.  You may also have a summary file, if you don't just try teh addressbook.db.

Then restart evolution and see if any contacts appear.  

If the file you have is not in an .db format, then try using import under the file menu in evolution.  Browse to the file and see if you can just to a simple import. 

Also if you need more help please list the names of the backup files you are trying to use.

---

