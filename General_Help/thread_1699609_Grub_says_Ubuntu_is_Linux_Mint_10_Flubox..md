---
title: "Grub says Ubuntu is Linux Mint 10 Flubox."
date: 2011-03-03
forum: General Help
---

### Post by Nictra Savios on 2011-03-03
When im in the grub menu, it calls my Ubuntu 10.10 "Linux Mint 10 Flubox" 

When i went back from mint to ubuntu, i did take a few things over.
I took the ubuntu stock pkg list ( dpkg --get-selections > ubulist )
and the mint stock list (same except for mintlist) Then put em in a website that took out everything in the mint list that was alredy in the ubuntu list, i did a quick check on the mint list, removing pidgin and thunderbird, aswell as mintinstall and mintupdate...

Added the Linux Mint 10 (Gnome) source to my souces, set up my ubuntu desktop, installed that list with a bash script i made and voila.... Untill 2 things happend.

1) My splash screen changed.... Quick google and i solved that.
2) What the title says. 


Running wilee-nilee's boot script i got

File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Fluxbox
    Boot files/dirs:   /etc/fstab

:/....

How do i fix it ? Do i need to install some "sysinfo" type package like "ubuntu-system-info" ?

Just, how do i get this back to normal.....

---

### Post by wilee-nilee on 2011-03-03
Does a grub header really matter, you have mint with a Ubuntu desktop.

---

### Post by Nictra Savios on 2011-03-03
> **wilee-nilee said:**
> Does a grub header really matter, you have mint with a Ubuntu desktop.

Yes it dose, And infact i have Ubuntu with a mint desktop. (and no ugly green) 
Esspecialy when im not using flubox.......

I want to know this for 2 reasons, 1) to get it back to normal. 2) Becuase this may cause issues if somthing needs ubuntu (UBUNTU ONLY) and thinks im running mint, Also i hate the name "Mint" ... yuk.


So yea... Matters alot.

---

### Post by Nictra Savios on 2011-03-03
> **wilee-nilee said:**
> Does a grub header really matter, you have mint with a Ubuntu desktop.


Oh and i tried your boot script, see

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Fluxbox
    Boot files/dirs:   /etc/fstab


...... Thats not right. Im running Ubuntu 10.10 GNOME....

---

### Post by Nictra Savios on 2011-03-03
oh and if someone can tell me WHY this happend, please do.

---

### Post by Nictra Savios on 2011-03-03
Please..... Quickly? :(

---

### Post by Nictra Savios on 2011-03-04
Thanks for all the kind informative anwsers ... Oh  wait there aren't any.

---

### Post by Nictra Savios on 2011-03-04
Bump

---

### Post by wiggly81 on 2011-03-04
sarcasm is the lowest form of wit

---

### Post by overdrank on 2011-03-04
Duplicate [here]("http://ubuntuforums.org/showthread.php?p=10523097#post10523097"). Thread closed.

---

