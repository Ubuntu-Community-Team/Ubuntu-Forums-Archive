---
title: "Display out of range"
date: 2010-08-04
forum: General Help
---

### Post by Drui on 2010-08-04
Hi All,
 I have reloaded windows xp and now after installing ubuntu latest version, I get a boot menu that gives options.
if I select the Ubuntu option, within a few seconds(2)the monitor  shows "out of range"! However it is possible to get a command prompt from this menu,(Grub)by pressing "C" then Tab, which lists about 30 commands! But I cannot find what command will overide the ubuntu boot display setting! yet if it is possible in the disc boot F6 menu, then it follows that it must be possible in the hard disk boot menu? (ie nomodeset available on the disk F6, so using F6-nomodeset on the disk allows me to install or run from the disk, which then runs perfectly) Only I cannot make changes in the Ubuntu live that runs direct from the disk, to the installation on the hard drive.
    	     
PS. My Monitors Max is 75hz 1280x1024, LCD.
And although not the latest model, Its still relatively current.

Windows from the boot menu works fine.

Can any expert user help? 
Drui

---

### Post by Drui on 2010-08-05
this has been resolved by hitting e from the boot menu and then adding
nomodeset after Quiet splash. Bingo!    
after getting into ubuntu, and adding the recommended driver, Guess what?
Out OF RANGE!   sod it, back to windows at least it works!

---

