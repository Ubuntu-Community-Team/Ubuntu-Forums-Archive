---
title: "How do I mount my Windows partition when using Wubi?"
date: 2010-05-25
forum: General Help
---

### Post by accguy9009 on 2010-05-25
Using Ubuntu 10.04 with a Wubi Install. Vista Home Premium is the host. I can access all my  partitions and external drives with the exception of my windows partition where Wubi is installed. I have seen some suggestion to go to "places" and click on "host", but there is no "host" listed. My windows install is on sda1 and I believe I need to create a directory for it and then execute a command in the terminal but I have no idea if this correct or what really needs to be done. Any assistance to help me mount my NTFS windows partition while I am running Ubuntu 10.04 in Wubi would be greatly appreciated.

---

### Post by bcbc on 2010-05-25
It's the /host directory. You can go to Places, File system, and look for the host directory.

---

### Post by accguy9009 on 2010-05-25
That is the reason for my post. When I go to places I don't see anything that says host or file system. My other drives and partitions are there. I even see something for a floppy and for the blank disc I currently have in my optical drive, but no host. I wish it were that easy. Everything else is working wonderfully. I even installed Nexuix from the command line and played the game. It is fun for someone like me who isn't much of a gamer but I like a lil FSP on occasion. I got chromium and vlc installed and working. If I could just get that windows partition mounted life wud be grand.

---

### Post by bcbc on 2010-05-25
> **accguy9009 said:**
> That is the reason for my post. When I go to places I don't see anything that says host or file system. My other drives and partitions are there. I even see something for a floppy and for the blank disc I currently have in my optical drive, but no host. I wish it were that easy. Everything else is working wonderfully. I even installed Nexuix from the command line and played the game. It is fun for someone like me who isn't much of a gamer but I like a lil FSP on occasion. I got chromium and vlc installed and working. If I could just get that windows partition mounted life wud be grand.

Sorry - I'm not currently running ubuntu so maybe I didn't give the precise name. But I can assure you it is mounted. Perhaps it's Places, My Computer or you could hit ALT-F2 and run ```
nautilus /host
```

Play around, it's there.

---

### Post by accguy9009 on 2010-05-25
I opened up a file browser and I did see what you described and I now have the ability to use the partition I need. Thanks for your help. Its weird I can't get it right from "places", but as long as I can get at it I am ok. Thanks again.

---

### Post by accguy9009 on 2010-05-25
Wubi really is a great way for a new user to try Ubuntu. I have found 10.04 easy to use. I have a little bit of Nix experience (very little) but never really liked the prev. versions I tried. It is easy to remove if you are so inclined using add remove in windows and you don't need to mess with your MBR which I prefer to avoid doing.

---

### Post by bcbc on 2010-05-25
> **accguy9009 said:**
> Wubi really is a great way for a new user to try Ubuntu. I have found 10.04 easy to use. I have a little bit of Nix experience (very little) but never really liked the prev. versions I tried. It is easy to remove if you are so inclined using add remove in windows and you don't need to mess with your MBR which I prefer to avoid doing.

Yes I agree. You just can't hibernate (which I use a lot), but other than that it's a good way of getting to know ubuntu.

Talking of the MBR, be careful whenever there's a grub update (that's the ubuntu bootloader). Sometimes the mainstream updates don't always consider the wubi crowd and problems can occur. 

PS If you add a bookmark to the host directory it will appear under the places menu. Or any folder under the /host that you need e.g. your old My Documents

---

### Post by accguy9009 on 2010-05-25
I did an system update today and I was offered a chance to skip the grub update which I did. None of the other updates offered this. I thought since I was using wubi it was a windows bootloader I was using. Am I using Grub? Didn't think so but I will have to check

---

### Post by bcbc on 2010-05-25
> **accguy9009 said:**
> I did an system update today and I was offered a chance to skip the grub update which I did. None of the other updates offered this. I thought since I was using wubi it was a windows bootloader I was using. Am I using Grub? Didn't think so but I will have to check

You're using a windows bootloader, and grub2 on ubuntu - in order to boot ubuntu from windows, it uses grub4dos. When I upgraded a 9.10 wubi to 10.04 the version of grub2 was changed 1.97beta4 to grub 1.98, and it offered to install the grub bootloader to the MBR and any partition bootsector (it's not aware that it was a wubi install). I think a simple update won't do this, maybe only a new release of grub, but either way - it pays to understand a little about how grub works so you can avoid these problems.

---

### Post by accguy9009 on 2010-05-27
Thanks

---

### Post by gadolinio on 2010-05-27
> **accguy9009 said:**
> I opened up a file browser and I did see what you described and I now have the ability to use the partition I need. Thanks for your help. Its weird I can't get it right from "places", but as long as I can get at it I am ok. Thanks again.

You can add it to the Places menu. Once you are in the folder with nautilus, go to the Bookmarks menu, and click "add bookmark". You'll see that the folder you're currently in (that would be /host, in your case) is added to nautilus's left side pane. Then go to Places, and it will be there as well.

---

### Post by gadolinio on 2010-05-27
You can also create a launcher on a panel and/or desktop.
Right click the panel you want to add the launcher to, select "add to panel". Then "custom launcher". Under "type" pick "place"; name: whatever you like;
place: "file:///host" (without quotes). Comments: whatever you want, even nothing. Then click close. A single click on that launcher will open /host.
You might also want to click-drag-and-drop that launcher to the desktop, and thus have a copy there (and then delete the one from the panel, if you want).

---

