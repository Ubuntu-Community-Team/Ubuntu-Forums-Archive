---
title: "LiveCD Mod's- Changing boot menu."
date: 2011-06-22
forum: General Help
---

### Post by MAFoElffen on 2011-06-22
Don't know if this is the place (forum) to ask this, but did not find any other forum that really fit any better than this.

My question is:  "What file is the Ubuntu distribution LiveCD using for the Try / Install Menu?"

I support Ubuntu (and it's dirivatives) graphic's issues.  Because of the skill level and equipment of a particular user that needs assistance- A user cannot get to the boot options settings of a LiveCD, so I decided to modify a LiveCD for this user. This modified LiveCD would help them to have Graphics for their equipment on boot from that LiveCD image and further script in changes that would automate what they need for a successful install for their equipment.. 

I've expanded and mounted a current LiveCD ISO image...

According to the Isolinux conventions... the usually suspects... It would be /casper/isolinux.cfg and files included / called from that file.(menu.cfg, stdmenu.cfg, etc.) I've gone thorugh these files, and the Fn.txt files (F1.txt...)...  They seem just different enough to lead me to believe that maybe that the main menu being used is coming from somewhere else!

Anyone here know which files are being used and where they are located?

Or should I ask this from: **"Development CD/DVD Image Testing"?  **

---

### Post by grahammechanical on 2011-06-22
I am looking through the files on the 11.04 install CD and the file with the menu items of Try Ubuntu without installing and the rest is called txt.cfg (it is a text file. It will open in text editor) and is in the isolinux folder.

Regards.

---

### Post by MAFoElffen on 2011-06-24
> **grahammechanical said:**
> I am looking through the files on the 11.04 install CD and the file with the menu items of Try Ubuntu without installing and the rest is called txt.cfg (it is a text file. It will open in text editor) and is in the isolinux folder.

Regards.
Thanks.  That's what I thought, but when I traced it down to the function key submenus, they looked different.

---

