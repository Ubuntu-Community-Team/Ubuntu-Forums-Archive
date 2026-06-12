---
title: "Partitions"
date: 2011-03-20
forum: General Help
---

### Post by Miykel on 2011-03-20
[FONT=Georgia][SIZE=2]G'Day;  My question is in regards to pertitioning;[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]     This PC has 2x500Gig HDDs which I partitioned into several sectors, one for Vista, one for W7 (64), the rest for secified data, I store nothing in my OS, except Apps.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]  Now what I want to know is if I use the partition manager in W7 to delete and reformat the Vista partition and rename it Ubuntu, when I install the Ubuntu OS will I have to rework the partition with GParted or will it go strait onto the Ubuntu Partition ??[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]  Kind Regards  Miykel  :confused:[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]P.S. How do I upload my avitar   :oops:[/SIZE][/FONT]

---

### Post by mikewhatever on 2011-03-20
Yes, you'll have to redo partitions with Gparted. The names of partitions are irrelevant here, but their file systems are quite important, and Windows can't create Linux file systems. To save time, I suggest you both delete and create partitions with Gparted.

---

### Post by wilee-nilee on 2011-03-20
Run the bootscript in my signature as Vista and W7 may have their boot combined, so a removal of Vista then will leave W7 unbootable without a little fix.

If you run the script post the text in code tags by clicking on the **(#)** in the reply panel to generate them,.

---

### Post by Miykel on 2011-03-20
[FONT=Georgia][SIZE=2]G'Day;   Guys and thanks for the reply, however Wilee-Nilee I am not sure what your reply means, excuse my ignorance, this is quite new to me, which is why I want to go to Ubuntu, something new.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]    Now if I was to delete the Vista partition with my partition Manager then edit the W7 bootloader to show only W7 and leave the Vista partition as Unalocated space would that be to any advantage ?? :confused:[/SIZE][/FONT]
[FONT=Georgia][SIZE=2] Kind regards Miykel[/SIZE][/FONT]

---

### Post by wilee-nilee on 2011-03-21
> **Miykel said:**
> [FONT=Georgia][SIZE=2]G'Day;   Guys and thanks for the reply, however Wilee-Nilee I am not sure what your reply means, excuse my ignorance, this is quite new to me, which is why I want to go to Ubuntu, something new.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]    Now if I was to delete the Vista partition with my partition Manager then edit the W7 bootloader to show only W7 and leave the Vista partition as Unalocated space would that be to any advantage ?? :confused:[/SIZE][/FONT]
[FONT=Georgia][SIZE=2] Kind regards Miykel[/SIZE][/FONT]

I can't really confirm anything without seeing your set up in more detail, which is what the bootscript in my signature is for.

---

### Post by Miykel on 2011-03-21
[FONT=Georgia][SIZE=2]G'Day;  Wilee-nilee I just reread what was on your link and could you clear up something for me please, it seems that it assumes I already have a Linux distro already installed, which I have not as yet, I'm just trying to gather as much info as I can so I have no dramas when I come to install Ubuntu.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]  Does it have to be a txt result or could I paste a screen shot of the drive layout from my Partition manager ???[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]  Kind Regards and thanks for your patients.   [/SIZE][/FONT]
[FONT=Georgia][SIZE=2] Miykel[/SIZE][/FONT]

---

### Post by wilee-nilee on 2011-03-21
> **Miykel said:**
> [FONT=Georgia][SIZE=2]G'Day;  Wilee-nilee I just reread what was on your link and could you clear up something for me please, it seems that it assumes I already have a Linux distro already installed, which I have not as yet, I'm just trying to gather as much info as I can so I have no dramas when I come to install Ubuntu.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]  Does it have to be a txt result or could I paste a screen shot of the drive layout from my Partition manager ???[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]  Kind Regards and thanks for your patients.   [/SIZE][/FONT]
[FONT=Georgia][SIZE=2] Miykel[/SIZE][/FONT]

When you install windows distros consecutively they combine their boot files. The bootscript will identify this so that it can be fixed correctly. Editing a file from inside of windows is not a usual fix, you use a recovery or install disc.

Back up your computer and make a recovery disc.

---

### Post by Miykel on 2011-03-21
[FONT=Georgia][SIZE=2]G'Day;  Well thanks for that explaination, when ever I've had to reload a windows distro on either partition I just open the Command Prompt and use bcdedit.exe to get rid of extra entries from previous installs, but this is a whole other deal, I have this link which explains how to use the windows boot loader instead of Grub so I might look at that as well, not sure yet.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]  I run Ubuntu from CD a little while ago now I'm busting to get it installed and get going.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]    If you hear any blood curdleing screams coming from down under you'll know what it is[/SIZE][/FONT]
[FONT=Georgia][SIZE=2]  Kind Regards   Miykel   :popcorn:
[FONT=Georgia] [/FONT]
[FONT=Georgia]  [/FONT]
[/SIZE][/FONT]

---

