---
title: "USB Stick Weirdness (Virus?)"
date: 2011-05-30
forum: General Help
---

### Post by Tubbytee on 2011-05-30
Hi,

I'm having a weird problem with my USB Sticks.

I've done a low level format on them so they're completely empty. When I use them with my windows machines, they're absolutely fine.
When I plug them into my Ubuntu machine, there is a hidden directory created called 'RECYCLER' which I'm assuming is for deleted files? 

However, it also creates a .exe file in this directory called 0x2D9FA278 which has an Icon with an H in it and a comment of 'Facebook Photo'

This has the effect of making all the directories on the stick into shortcuts! 

I googled the file name and it seems to be some sort of Trojan, but I don't understand how it's go into my Ubuntu machine, I've scanned with ClamAV and it finds nothing!

Anybody shed any light on this?

Cheers in advance for any help!


Pierce

---

### Post by Tubbytee on 2011-05-30
Quick update, all the folders display alright in Ubuntu, although there are <Folder Name>.lnk files on the stick. However, if on the Windows machine, I delete the RECYCLER folder, I am no longer able to access the folders via the shortcuts! The folders are still visible in Ubuntu though.

?????


Cheers,

Pierce

---

### Post by nerdy_kid on 2011-05-30
> **Tubbytee said:**
> Hi,

When I use them with my windows machines

Pierce

Viruses don't run on Ubuntu (without wine, and even then they cant do anything serious, and usually dont do anything at all), is your windows system infected?


> **Tubbytee said:**
> Hi,

When I plug them into my Ubuntu machine, there is a hidden directory created called 'RECYCLER' which I'm assuming is for deleted files? 

Pierce

That is Windows recycling bin folder, it is hidden on Windows.  .Trash-001(or something like that) is Ubuntu's. Sounds like your Windows machine could be infected to me.

---

### Post by Tubbytee on 2011-05-30
Actually, the more I try and eliminate things, the more I think you're right! 

Thing that bugs me though is that this Windows box isn't connected to the internet!

Oh well, I'll see if I can work it out!


Cheers for your help though

---

### Post by sbraz on 2011-05-30
in ubuntu press **ctrl + h** to see hidden files, then delete anything suspicious.
usually, removing anything unusual does the trick, otherwise from linux copy the contents locally then format the usb stick.

if it's a virus, windows might still be infected though. :(

---

### Post by linuxinstalledfromhdd on 2011-05-30
If you want to install an antivirus program on your system to check that, you can find it about 1/3 the way down this guide:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

