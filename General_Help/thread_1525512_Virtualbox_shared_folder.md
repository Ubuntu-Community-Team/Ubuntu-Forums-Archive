---
title: "Virtualbox shared folder"
date: 2010-07-06
forum: General Help
---

### Post by Cpierce on 2010-07-06
I am a newbie running 10.04. Can someone give me step-by-step instructions on how to set up a shared folder in Ubuntu for virtualbox ? To be clear, Ubuntu host and Windows guest.

---

### Post by Leppie on 2010-07-06
this depends on which windows will be the guest os.
there's actually many step-by-step guides on setting up virtualbox shared folders on the net.

---

### Post by Cpierce on 2010-07-07
Sorry, I should have included more info. I have read the virtualbox manual on shared folders but it still didn't make sense to me. Let's say that I have a folder called "VBshare" that is located in /home/chuck/.  The host is Ubuntu 10.04 and the guest is Win XP pro with guest additions installed. What commands would I need to do ?

---

### Post by Irony on 2010-07-07
See here go to about 2:30 make sure you tick make permanent at 2:50;

[http://www.youtube.com/watch?v=75FeKOkpSKk](http://www.youtube.com/watch?v=75FeKOkpSKk)

Also make sure that afterwards you change the settings back to cd or else it thinks you want to install guest additions again.

---

### Post by Leppie on 2010-07-07
assuming that you've already passed on the folder path to virtualbox add the shared folder in the guest os like this:
in windows explorer, go to my computer.
click on the "Folders" button (don't open the "my network places" link), expand "Entire Network", expand "VirtualBox Shared Folders". expand "VBOXSVR" you're folder(s) should be there. if you right click it and choose "create shortcut" it will create a shortcut on your desktop.

---

### Post by Muttley99 on 2010-07-07
I gave up with shared folders as mine was very slow to access. I use dropbox for small or medium size files.
Maybe it was just my settings!

---

### Post by mister_playboy on 2010-07-07
> **Muttley99 said:**
> I gave up with shared folders as mine was very slow to access. I use dropbox for small or medium size files.
Maybe it was just my settings!

I experienced this same issue with my XP VM.  Access to the shared folder took ages and would often time out.  A Win2000 machine had no such problems, however. :P

---

### Post by Leppie on 2010-07-07
> **mister_playboy said:**
> I experienced this same issue with my XP VM.  Access to the shared folder took ages and would often time out.  A Win2000 machine had no such problems, however. :P
yes, my xp connection is very slow as well. win7 doesn't have this problem either, but i guess i would prefer win2k to win7 :)

---

### Post by Cpierce on 2010-07-07
I got it. You guys are the best. Thank you very much

---

### Post by Leppie on 2010-07-07
> **Cpierce said:**
> I got it. You guys are the best. Thank you very much
so you've been able to mount the share in the guest os?

---

### Post by Ender985 on 2010-07-07
For the record, my Shared folder from WinXP guest to Lucid host works almost instantly (I have running the latest VBox version for if it matters).

Regarding Dropbox: I got Dropbox installed in Lucid and set the dropbox folder as the vbox_shared folder, so that I would keep everything shared between the virtual, the ubuntu and all my other dropbox computers. But it turns out that if you put files in the folder from the virtual XP, dropbox does not sync it very reliably, I think I might need to exit virtualbox in order for dropbox to sync it all. I guess I'll have to just give up, plug in the virtual XP to the net and install Dropbox separately there as well, even though it will be very odd to have 2 separate ways to cross info between the systems (and more dangerous to have XP exposed to internet)...

---

### Post by Cpierce on 2010-07-07
I too am running Lucid and the newest VB and found it ran quickly as well. Very pleased, so thanks everyone again

---

### Post by Cpierce on 2010-07-07
Leppie, I can share files, so it is working well. Thanks for your help !

---

### Post by Leppie on 2010-07-07
> **Cpierce said:**
> Leppie, I can share files, so it is working well. Thanks for your help !
you're very welcome, glad it's working :)

did you install/do something in particular?
i'm running the latest version  as well on lucid.

---

### Post by Cpierce on 2010-07-07
What I did was first add the VB shared folder in the "detail" section of the VM. Then I started the guest XP>my computer> tools>map network drive. In the window that opens, I left the drive letter to Z, and then in the second part I hit "browse" and navigated to my VB shared folder. Now anytime I want to access the shared folder, I just open "My Computer" and it is listed there just like C: drive is.
The same thing worked on Win7. Although when you open "my computer", the "map network drive" is already there. In other words you don't have to go to "tools" first.

I hope this helps speed yours up !

---

### Post by Leppie on 2010-07-07
thanks, i'll give it a try :)

---

