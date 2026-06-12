---
title: "can not find KDE package for ubuntu anywhere"
date: 2006-04-11
forum: General Help
---

### Post by roast on 2006-04-11
I have been trying since a long time bbut i am unable to find the KDE package that can install KDE Desktop on ubuntu. Its not present on cd... not available anywhere for download.....

Please some one tell me step by step what to do...

I am not the only one with problem. You will help a lot of people. :)

---

### Post by ogbg_82 on 2006-04-11
Have you tried "apt-cache search kde"?
I think you get it on apt.  If it's there when you search, I think you just need to do: "sudo apt-get install kde"

---

### Post by Darkriser on 2006-04-11
edit your /etc/apt/sources.list according to the following thread:
[http://ubuntuforums.org/showthread.php?t=157890](http://ubuntuforums.org/showthread.php?t=157890)

type 'sudo apt-get update' in console

type 'sudo apt-get install kubuntu-desktop' in console

---

### Post by Darkriser on 2006-04-11
[QUOTE=ogbg_82]Have you tried "apt-cache search kde"?
I think you get it on apt.  If it's there when you search, I think you just need to do: "sudo apt-get install kde"[/QUOTE]


differences between kde and kubuntu-desktop can be found here:
[https://wiki.ubuntu.com/InstallingKDE](https://wiki.ubuntu.com/InstallingKDE)

---

### Post by davebgimp on 2006-04-11
[QUOTE=roast]I have been trying since a long time bbut i am unable to find the KDE package that can install KDE Desktop on ubuntu. Its not present on cd... not available anywhere for download.....

Please some one tell me step by step what to do...

I am not the only one with problem. You will help a lot of people. :)[/QUOTE]

First off, make sure your repositories are correct. Create a backup of your sources.list file first though.

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup (or whatever you want)

Then, refer to the repo info in this post:
[http://ubuntuforums.org/showthread.php?t=92672](http://ubuntuforums.org/showthread.php?t=92672)

After editing, replacing or whatever you need to do after comparing this, run:
sudo apt-get update

and then run
sudo apt-get install kubuntu-desktop

restart x (ctrl-alt-del) and choose kde.

Hope that helps.

---

### Post by roast on 2006-04-11
another problem is this i can not connect to internet with ubuntu.... i can only connect to my isp's ip and home page ... nothing else works... so does this process that u told me , requires internet connection ???...


what i do is try the solution given by u guyz and the reboot to windows and come here and check the forum and the again reboot ...reboot.... reboot :(

---

### Post by davebgimp on 2006-04-11
[QUOTE=roast]another problem is this i can not connect to internet with ubuntu.... i can only connect to my isp's ip and home page ... nothing else works... so does this process that u told me , requires internet connection ???...


what i do is try the solution given by u guyz and the reboot to windows and come here and check the forum and the again reboot ...reboot.... reboot :([/QUOTE]

Well, that's weird. I'd guess that if you are truly able to connect to your ISP's ip and page and not viewing some cache, you do in fact have an internet connection. What's going on with it, I'm not so sure but if you're tired of going back and forth, you could download and burn the official Kubuntu .iso which will give you Ubuntu with KDE and not Gnome. You'll have to reinstall your OS, but you'll have KDE with or without an internet connection.

You can dowload that here: [http://kubuntu.org/download.php](http://kubuntu.org/download.php)
You can download and burn that under windows (assuming you have a cd burner).

---

### Post by roast on 2006-04-12
**Solved**

1. The internet cnnection..   i have 2 ethernet cards both have different gateways, one for home networkand  one for internet, the default gateway option in the network settings dialogbox was set to home network card (eth0)
but it should be internet card (eth1) . For some reason this was changing but not saving the change, but now its changes are saved. So internet works.

2. I updated the source list as told by "davebgimp" (Thanks man !!)

3. Then i ran this in console....
      """""   sudo apt-get update ; sudo apt-get upgrade  """""

4. It connected to net and started downloading.... arround 150 MB (at my 128kbps connection it took arround 2 1/2 hours).

5. Then it installed by itself.

Voila !!!! I have KDE !!!


Thanks to everyone who helped me :) 
love thy community :)

---

