---
title: "How to upgrade from Ubuntu 7 to current Ubuntu?"
date: 2010-04-30
forum: General Help
---

### Post by newbun on 2010-04-30
Hello 

Currently I have a AMD athlon 1.5 ghtz processor and want to upgrade to Ubuntu 10.  I currently have 7.2 and when I click on the upgrade to latest version I get errors "can't find....."

I've downloaded the latest version onto the desktop, but need to get the iso file onto a blank cd.  That's the other problem, I need a quick and efficient cd eraser/writer.  so after erasing I can write the iso file and then, hopefully, boot to 10.

What are the simple steps of firstly: 

1) erasing the cd (what program do I download)?
2) writing the Version 10 and then booting up to the current?

All this is very basic to this forum, but I'm from the Windows lot....looking to make the switch.  If it goes OK on the (very old ) desktop, I'll do the same with this laptop ;-)

Hope you can help?

thanks

---

### Post by dino99 on 2010-04-30
dist-upgrading is available from:
- previous to next
- LTS to LTS

so in your case, better to do a clean install

---

### Post by newbun on 2010-04-30
Ok...but, this clean install, how is it done?  I've downloaded the current onto the desktop.

I need to wipe the cd with an application - which?

then I write the ISO file to the cd.....so, presumably I'll need a CD writer/eraser

then Boot up?

Help!!

---

### Post by sdowney717 on 2010-04-30
use this if your using windows, its free.
[http://cdburnerxp.se/](http://cdburnerxp.se/)

if on ubuntu, cd-dvd creator, k3b or brasero
you will have to download the iso and burn it.

---

### Post by dino99 on 2010-04-30
[https://help.ubuntu.com/9.10/index.html](https://help.ubuntu.com/9.10/index.html)

---

### Post by newbun on 2010-05-01
Thanks for the replies ;-)

---

### Post by Umang on 2010-05-01
Hey, by the way. Ubuntu 7 and Ubuntu 10 don't exists. Every year Ubuntu has two releases (in April and October). 7.04 and 7.10 were the 2007 April and 2007 October releases. The difference between the two is as much as between 6.10 and 7.04 or 7.10 and 8.04. Therefore, 7.04 was not a minor release after 7.0. There was no 7.0 to begin with. :)

Every two years there is an LTS (long term service). If you don't like upgrading, you should consider using only these as it is possible to upgrade from one to the other without having to go through the ones in between.

---

### Post by newbun on 2010-05-02
Hi Umang - thanks for the reply....and putting me straight:)

Just had a closer look at the version of Ubuntu that I'm currently running, and , you're quite right is NOT 7, but 7.04 ;-)

I've downloaded UBUNTU-9.10 - the ISO image and I'm just about to wipe the boot tape and burn the image with one of the utilities that was recommended.

Thanks again.

---

### Post by newbun on 2010-05-02
..just as a follow up...



...forgot to say I tried to instal K3B (plus other pkgs) and am getting:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/c/cdw/cdw-common_0.2.4-2_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/c/cdw/cdw-common_0.2.4-2_all.deb)  404 Not Found....

Same thing with K3b.

---

### Post by coffeecat on 2010-05-02
> **newbun said:**
> ..just as a follow up...



...forgot to say I tried to instal K3B (plus other pkgs) and am getting:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/c/cdw/cdw-common_0.2.4-2_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/c/cdw/cdw-common_0.2.4-2_all.deb)  404 Not Found....

Same thing with K3b.

That's because the repositories for Feisty Fawn (7.04) have long since gone, so you can neither upgrade nor install applications. In fact, the packages you need are still available on an archive server, but to utilise them you'd need to edit your sources.list. It would probably be quicker and easier to use a Windows app to burn the ISO. Either use the one sdowney717 recommended or the free [Infra Recorder]("http://infrarecorder.org/"). Infra Recorder is the one suggested on the [Ubuntu Burning ISO howto]("https://help.ubuntu.com/community/BurningIsoHowto") (do read that before you start) and I got good results with it when I tried it.

---

### Post by dino99 on 2010-05-02
all in one process:

[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by newbun on 2010-05-03
Thanks 'coffeecat' and 'dino99'.  Firstly I'll us the suggested windows app to erase and burn the CD.  I'll also read the suggested links for burning the ISO.  I should be ok, but if I run into problems (on the ubuntu side) I'll let you know.

Thanks again :)

---

### Post by newbun on 2010-05-05
Ok.  So I downloaded 'InfraRecorder', used it to erase a 700mb cd-rw disc and then burn the ISO image file Ubuntu-9.10.  Did this on a Windows laptop.  
From there took it to the ubuntu machine, into the cd reader and tried to boot up.

Got the language screen:  chose English.  Then it gave this:

I/O error
Error Reading BOOT CD - reboot.    Before you say; 'check your cd' - I did and it appeared to 'write successfully'...also tried another cd; same thing.

So...what do you think?

Oh, just booted up with the old Ubuntu 7.01...loaded the cd and the contents seem ok;   

casper, dists, install, isolinux, pics, pool, preseed, ubuntu  - all folders, and a few other files.

---

