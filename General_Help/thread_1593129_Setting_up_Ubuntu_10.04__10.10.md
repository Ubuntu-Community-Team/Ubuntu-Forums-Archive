---
title: "Setting up Ubuntu 10.04 / 10.10"
date: 2010-10-11
forum: General Help
---

### Post by TheAnachron on 2010-10-11
Hello guys!

First of, I want to thank you for making Ubuntu! Its awesome.
Secondly, I have some troubles configuring it.

_I.) Setting up the network:_[INDENT] I have 3 pcs: 
1x Ubuntu 10.04 (Desktop)
1x Ubuntu 10.10 (Desktop)
1x Windows 7 (Professional [activated])

I tried setting up samba (install all the required packages and stuff) but it does not work for the Ubuntu 10.10 PC! I can enter the IP of my 10.04 desktop pc and those files are shared, however, with the exact same settings (and other IP) the 10.10 pc does not seem to be able to use any samba shared stuff at all! (Not even the samba stuff it shared). 

However, on the 10.04 I can access the shared 10.10 stuff so samba should be running and be configured correctly. I know uninstalled everything (Samba) and replaced the smb.conf with an old backup. Is there any guide how I can set up an samba share that also appears in the network? I will sooner or later update the 3rd PC to ubuntu too, however, I'd like to have Windows compactiblity in my network.
[/INDENT][U]
II.) Working with PlayOnLinux (POL):[/U][INDENT] I have installed Warcraft 3 + TFT successfully, however, I don't know how I can install any game that is not on the POL list into the POL framework.
[/INDENT]_III.) Programs that I am missing:_[INDENT] I have found a lot of software already that I use every day, however, here is some stuff I am missing that I haven't found a good replacement until yet: (Would be great if you tell me programs that could replace them)

[LIST]
[*]Mikogo (Teamviewer is totally laggy) [An presentation remote-control GUI-based program]
[/LIST]
[/INDENT]_IV.) Troubles using Empathy/Pidgin:_[INDENT] I am using the latest pidgin and latest empathy version and enabled the empathy plugin for pidgin. However, from time to time Pidgin tells me that I need to reactivate accounts and I will get disconnected. Is there any way  to solve this? (And why does this happen?)
[/INDENT]_V.) Partition "magic" - Suggestions or feedback:_[INDENT] I have these partitions: 
1.) Primary Ubuntu, 20GB, ext2 (System)
2.) Extended, 400GB
3.) (Extends 2.) Data, 50GB (Backups & co), NTFS - Should be accessable in windows too
4.) (Extends 2.) Files, 300GB (Media...), NTFS - Should be accessable in windows too
5.) (Extends 2.) Docs, 50GB (.doc, .xcl,..), NTFS - Should be accessable in windows too
6.) Primary Windows, 100GB
7.) Swap

In linux I mount them as /data, /files/, /docs, /windows and /.
[/INDENT][LEFT]_VI.) Backup the whole system (**Solved**):_[/LEFT]
[INDENT] Connected to V, I would like to know how to backup the whole primary ubuntu drive with being able to restore it.
[/INDENT]_VII.) Login issues:_[INDENT]Whenever I log into my ubuntu, it says "Waiting for a program to react" (Power Manager). It says logout or wait as actions. How can I solve this? 
[/INDENT][U]
VIII.) Again, thanks for this nice system, the forum and for all the free work.[/U]

---

### Post by TheAnachron on 2010-10-11
Shameless bump since this is in the 4th page without any replies already.

---

### Post by mastablasta on 2010-10-11
> **TheAnachron said:**
> Hello guys!
 
 
 
_I.) Setting up the network:_
[INDENT] 
I tried setting up samba (install all the required packages and stuff) but it does not work for the Ubuntu 10.10 PC! I can enter the IP of my 10.04 desktop pc and those files are shared, however, with the exact same settings (and other IP) the 10.10 pc does not seem to be able to use any samba shared stuff at all! (Not even the samba stuff it shared). 
 
However, on the 10.04 I can access the shared 10.10 stuff so samba should be running and be configured correctly. I know uninstalled everything (Samba) and replaced the smb.conf with an old backup. Is there any guide how I can set up an samba share that also appears in the network? I will sooner or later update the 3rd PC to ubuntu too, however, I'd like to have Windows compactiblity in my network.

 
How did you set it up? I can reach winxp computer by default. In order for WinXP to reach Ubuntu computer all i did was righclick in nautilus on public folder and make it as shared. it them asked me if i wanted to install and configure SAMBA and i said yes. after install was finished, windows can see the folder. no special installing or setting up.
[/INDENT]
> _V.) Partition "magic" - Suggestions or feedback:_
[INDENT]I have these partitions: 
1.) Primary Ubuntu, 20GB, ext2 (System)
2.) Extended, 400GB
3.) (Extends 2.) Data, 50GB (Backups & co), NTFS - Should be accessable in windows too
4.) (Extends 2.) Files, 300GB (Media...), NTFS - Should be accessable in windows too
5.) (Extends 2.) Docs, 50GB (.doc, .xcl,..), NTFS - Should be accessable in windows too
6.) Primary Windows, 100GB
7.) Swap
 
In linux I mount them as /data, /files/, /docs, /windows and /.

 
Im not sure if this still goes, but windows usually wanted the first part of the disk. otherwise partition away... :-) do it as you like...
 
> 
[/INDENT]_VI.) Backup the whole system:_
[INDENT]Connected to V, I would like to know how to backup the whole primary ubuntu drive with being able to restore it.
[/INDENT]
 
 
have you tried Mint Linux backup tool? it seems really easy to use and can be used effectivly on Ubuntu as well. Mint (though Ubuntu based) does not support system upgrade method. so they developed an easy to use tool, so users can back up home and important data and perform a fresh install with each version.
 
for the rest of your questions i don't have a slightest clue... :P

---

### Post by TheAnachron on 2010-10-12
> 
How did you set it up? I can reach winxp computer by default. In order  for WinXP to reach Ubuntu computer all i did was righclick in nautilus  on public folder and make it as shared. it them asked me if i wanted to  install and configure SAMBA and i said yes. after install was finished,  windows can see the folder. no special installing or setting up.There is no dialog which asks me to install and configure samba. (I simply can't mark it public because its missing the required programs)

> Im not sure if this still goes, but windows usually wanted the first part of the disk. otherwise partition away... :smile: do it as you like...Hmm, that is bad. So I have to switch sda0 and sda6? Windows sucks :)

> have you tried Mint Linux backup tool? it seems really easy to use and  can be used effectivly on Ubuntu as well. Mint (though Ubuntu based)  does not support system upgrade method. so they developed an easy to use  tool, so users can back up home and important data and perform a fresh  install with each version.
 
No I haven't, will check it out, thanks!

Edit: Oh well,  that only comes with the system itself :) That is bad  because I really love Ubuntu and don't want to install another system (I know its based on ubuntu, but i.e. the UI in Ubuntu is better as in Linux Mint)

> for the rest of your questions i don't have a slightest clue... :razz:Still thanks for the other answers!

---

### Post by mastablasta on 2010-10-12
> **TheAnachron said:**
> There is no dialog which asks me to install and configure samba. (I simply can't mark it public because its missing the required programs)

 
where is the folder you are trying to share. i used the default one in Home.
 
> 
Hmm, that is bad. So I have to switch sda0 and sda6? Windows sucks :)

All i am saying here is you should check this out. it's been a while since i installed windows...
 
> 
 
Edit: Oh well, that only comes with the system itself :) That is bad because I really love Ubuntu and don't want to install another system (I know its based on ubuntu, but i.e. the UI in Ubuntu is better as in Linux Mint)

 
No, it works in linux. and you can install it in ubuntu. i just saw a thread last week on which packages you need.
 
 
According to this website: [http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)
 
all you need to do is copy paste this command in terminal:
```
add-apt-repository ppa:webupd8team/mintbackup && sudo apt-get update
sudo apt-get install mintbackup
```

---

### Post by TheAnachron on 2010-10-12
> where is the folder you are trying to share. i used the default one in Home.
Hey, when I go to system -> settings -> shared folders all the options are disabled. 
 Also I don't want to share public in home, but my /files patition instead (NTFS) (Have ntfs-3g installed).

> All i am saying here is you should check this out. it's been a while since i installed windows...
 I will, thanks.

 
> No, it works in linux. and you can install it in ubuntu. i just saw a thread last week on which packages you need.
 
 
According to this website: [http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)
 
all you need to do is copy paste this command in terminal:
[CODE]add-apt-repository ppa:webupd8team/mintbackup && sudo apt-get update
sudo apt-get install mintbackup
Thank you very much, I will check it out when I come home! Will only applications be saved or the whole system with applications? Can't seem to find that out.

---

### Post by TheAnachron on 2010-10-14
Really sorry but I have to bump this.

---

### Post by TheAnachron on 2010-10-14
Hey thanks for the reply. 

I was bumping this thread because my other questions are still unanswered :) I marked all answered questions. Thanks anyway!

---

### Post by jquis8411 on 2010-10-14
Are you saying that the properties box for sharing are grayed out? If so you need to install appache2.2 and lib appache2 mod dssnd

---

### Post by TheAnachron on 2010-10-14
Nope, everything works fine, just the PC does not show up in the network.

---

### Post by TheAnachron on 2010-10-28
Bump! All pcs are now on 10.10, but one PC can't see himself in the network, all others work.

---

