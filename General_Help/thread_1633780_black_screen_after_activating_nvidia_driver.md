---
title: "black screen after activating nvidia driver"
date: 2010-11-29
forum: General Help
---

### Post by purpleyuan on 2010-11-29
I've been using ubuntu fine for a while when I decide to activate my nvidia graphics card. After rebooting, however, I hit nothing but a black screen. I've searched the nets and others have seemed to solve the problem after hitting alt+ctrl+f1/f2 and editing some files after that, but that doesn't work for me. Booting into recover console gives me nothing but a long stream of white words before it runs to --> done. and then it goes back to a black screen. Running from Live CD I can't access my ubuntu files. 

Is there any other way to solve this problem beyond reinstalling? 

Thanks for your time.

---

### Post by Hippytaff on 2010-11-29
Welcome to the forums, Nvidia cards can be tempremental and usually need some configuring...in the first instance try this courtesy of Forum Member Rubi1200
> 
Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

nomodeset

In other words, the boot should look like this:

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --

Now hit Enter.

You may have to toggle the F6 option a bit (do it first etc.).

If this gets the LiveCD booted and to the desktop, then we can go from there for a more permanent solution.

Let us know how it goes :-)

---

### Post by purpleyuan on 2010-11-29
Hahah, everything works!

Heh, I was able to boot into LiveCD and then access my ubuntu files. Then I deleted the xorg.conf files via [http://ubuntuforums.org/showthread.php?t=1356138](http://ubuntuforums.org/showthread.php?t=1356138)

so thank you very much :)

---

### Post by Hippytaff on 2010-11-29
No problem
Remember to mark the tread as solved in the thread tools at te top of the page so others with the same issue can benefit :-D

---

