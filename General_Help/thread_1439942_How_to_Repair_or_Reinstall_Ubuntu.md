---
title: "How to Repair or Reinstall Ubuntu?"
date: 2010-03-26
forum: General Help
---

### Post by sgsawant on 2010-03-26
My cups-pdf is not working. I tried asking a lot of people on the internet and tried a few tweaks on my own too. Here's my relevant thread:
[http://ubuntuforums.org/showthread.php?t=1412336&highlight=sgsawant](http://ubuntuforums.org/showthread.php?t=1412336&highlight=sgsawant)

But I am not able to find any solution to the problem. I need to convert a document into a pdf quite a few times. Unfortunately, I am not able to do so as my cups-pdf has failed. The latest error reads "Output Stream Write Error" (that is when I try to print a test page).

I know it's perhaps too much to reinstall the whole system just to solve the pdf-printing problem. But the same is bugging me no ends. Hence can someone please tell me a safe to reinstall Ubuntu as I don't want to harm the Windows installation on my system.

Is there a repair option available?

---

### Post by louieb on 2010-03-26
Reinstalling is about the same as installing. The one difference is at the partition step. 

[LIST]
[*]You will have to select the manual option.
[*]Then click on your current Ubuntu Partition.
[*]Select edit and tell the installer to use it (mount) as / (root). and format it.
[/LIST]
You will loose all you data. This does a fresh install. One question did you set up a separate /home partition?  


Kinda drastic to reinstall to fix a broken program. But oh  well.

---

### Post by sgsawant on 2010-03-29
Well thanks a lot!

I think I have setup a separate /home partition. Like quite a few of my folder begin with /home
So I guess I have a separate /home.

By why do you ask? Is it important for a safe reinstall?

Regards

---

### Post by louieb on 2010-03-29
Having a separate partition for /home is one way of preserving your data if you have to reinstall. If you don't know for sure you have one - you probably don't - you have to use manual partitioning at time of install. 

But not its not important  you can reinstall safely if you don't have one.

---

### Post by oldfred on 2010-03-30
Did you create a separate folder named PDF in your home partition/folder. The cups PDF writer defaults to that folder for all output but does not create it first time. I also had to run the aa-complain when I upgrade to Karmic.

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/295536](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/295536)
Confirmed. The following workaround even with PDF as a symlink to an encrpyted Private/PDF :)

$ sudo aa-complain cupsd
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.

---

