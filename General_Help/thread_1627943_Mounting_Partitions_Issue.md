---
title: "Mounting Partitions Issue"
date: 2010-11-22
forum: General Help
---

### Post by SuperKammz on 2010-11-22
Hello all!

This is my first time using Ubuntu (though I've been interested in it for about a year). I decided to dual-boot my Acer AspireOne netbook running Windows 7 starter with Ubuntu 10.10 Netbook version. I am in the process of looking through all of the information in terms of getting use to the system, but right now I am trying to figure out how to access my files on the Windows half of the computer.

I've been following the instructions here: [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions) but I am unable to get NFTS configuration to run, so I moved onto PySDM which appeared to work just fine except now when I boot up it gives me the error:

*"Unable to mount media/sda3" Press S to skip mounting process or M for manual recovery*

Since I am still very much a newbie when it comes to terminal commands, I stayed away from the manual recovery and pressing S just puts me back into the welcome screen so I can log in. I've been searching the forums and I can't find much on it.

Maybe I am missing a really important factor here?

Also, in some version of the instructions, the other partitions are supposed to become viewable once mounted. I went into looking through the files using PySDM, but what I saw was mostly greyed out files...

Any help would be appreciated and I hope you guys can understand what I mean. :D

Thank you in advance! So far, so good I LOVE this OS and I cannot wait to see how my Android phone interacts with it, it's just inconvenient to be without my music or documents and I don't want to transfer all of the information on to this side because it's a waste of space...

---

### Post by mikewhatever on 2010-11-22
You should see the Windows partition in the left panel of the file browser. Clicking it should mount the partition. Be careful not to delete important system files there.

---

### Post by garvinrick4 on 2010-11-22
In my signature is a great pdf book on Ubuntu to keep on hand to help out:

---

### Post by SuperKammz on 2010-11-22
> **mikewhatever said:**
> You should see the Windows partition in the left panel of the file browser. Clicking it should mount the partition. Be careful not to delete important system files there.

Do you mean the file browser within PySDM? Like in the first screenshot I attached PySDM1.png? The second attachment shows when I click within the listed folders on the side. The folder named "windows" is not the actual folder, I was giving a random mount point name.

[quote=garvinrick4]In my signature is a great pdf book on Ubuntu to keep on hand to help out:     [/quote]
Thank you!!! I am going to take a look at it now.

---

### Post by SuperKammz on 2010-11-22
Nevermind! It's already mounted... stupid me. I went into Disk Utility, clicked on the partition which was sda3 and it was already mounted under /host :) Thank you guys for your help!

---

### Post by Mark Phelps on 2010-11-22
If the Windows partition is mounted under /host -- you have a Wubi-based install.  Something important to point out to folks when you ask for help.

---

