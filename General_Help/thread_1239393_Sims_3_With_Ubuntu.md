---
title: "Sims 3 With Ubuntu"
date: 2009-08-13
forum: General Help
---

### Post by Aweyer2 on 2009-08-13
I am not sure if this is even the right place to post this question. Could not find one that relates to this topic exactly. If I post in the wrong place, sorry. Anyways, I have Sim's 3 and want to install it on Ubuntu but have no idea how. I have play on linux installed but can't configure the thing to work properly. Any help would be greatly appreciated. I have seen and heard of this being done on Ubuntu but I just can't get it.:confused:

---

### Post by coldReactive on 2009-08-13
Use WINE: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

In Terminal (Applications > Accessories > Terminal) cd to the directory of the Sims 3 setup file, and use **wine setup_file_name.extension**

This should start the setup process. After you install it through wine, you can access it through **Applications > Wine > Programs**. if there's an error, and setup cannot complete, then you might as well submit a bug report at winehq.org's bugzilla with terminal output.

There is no other way to run Windows applications on Ubuntu unless you have a copy of Windows and use a virtual machine such as VirtualBox.

---

### Post by Aweyer2 on 2009-08-14
Ok so I CD to my cdrom0 drive and type wine setup.app as the install file is called .app on the cd. Wine then gives me this message. ajweyer@ajweyer-ubuntu:/media/cdrom0$ wine setup.app
wine: could not load L"C:\\windows\\system32\\setup.app": Module not found
What am I doing wrong.

---

### Post by coldReactive on 2009-08-14
> **Aweyer2 said:**
> Ok so I CD to my cdrom0 drive and type wine setup.app as the install file is called .app on the cd. Wine then gives me this message. ajweyer@ajweyer-ubuntu:/media/cdrom0$ wine setup.app
wine: could not load L"C:\\windows\\system32\\setup.app": Module not found
What am I doing wrong.

What files are on the CDROM?

---

### Post by P4man on 2009-08-14
scroll down to the HowTo Guide:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664](http://appdb.winehq.org/objectManager.php?sClass=version&iId=16664)

---

### Post by FeTTo on 2009-10-25
this thread was being helpfull until that "how to" link was posted and no more responses. that "HOW TO" link makes no sense nor does it work what so ever. Can someone please assist where this thread left off. thanks

---

### Post by P4man on 2009-10-26
Perhaps you should read the howto more carefully. You might see that you best install PlayOnLinux and that you need a nocd crack for the game.

The advice given earlier was in general for wine, but to get sins3 working you need a lot more than that. Thats why it has a dedicated howto. 

If you get stuck anywhere there, feel free to ask though.

---

### Post by FeTTo on 2009-10-26
i read that how-to about 20 times, still doesnt help much. says to skip to step 15 if im using playonlinux. but then playonlinux just errors over and over when i try to install directx....none of those codes work as all the directorys are not found or will tell me it cant move the ts3.exe.

if someone could help me that would be great. im sure theres something im doing wrong obviously

---

