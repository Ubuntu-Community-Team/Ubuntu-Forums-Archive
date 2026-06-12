---
title: "Pegasus mail in Ubuntu and windows"
date: 2009-10-31
forum: General Help
---

### Post by gseward on 2009-10-31
I am running Pegasus Mail using Wine in Karmic, no problem, works fine, I would like to share the mailbox with Win7, so it is always updated, in either OS. The problem is the path to the mailbox in Ubuntu/Wine/Pegasus Mail.  The mailbox is on a partition that in Windows is labeled "D:\Pmail\Mail\Gil" and I can access it in Ubuntu by clicking on "Data", entering my password and selecting Pmail/Mail/Gil  If I then get properties on the folder Gil it says "/media/Data/PMAIL/MAIL".  This path does not work in Pegasus as the mail directory.  What is the path I would give Pegasus to the mail directory?
Sorry to be so long winded, I hope I have not made a simple question complicated.
Gil

---

### Post by misfitpierce on 2009-10-31
Move to Wine section maybe as more experienced Wine users using Wine apps reside there maybe? I  think this is mainly for Ubuntu general help on Ubuntu apps and OS... Just saying, may find help there better than here since that section is for sure based on Wine and apps running via Wine! Just a suggestion :P

Id help if I could but I have never heard of that mail app and don't really use wine :P

---

### Post by XCan on 2009-10-31
You should be able to configure wine to map /media/Data/PMAL/MAIL to D:. Have a look in Applications -> Wine -> Configure Wine -> Drives.

---

