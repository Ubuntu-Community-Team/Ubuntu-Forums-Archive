---
title: "HELP! I had a package 1/2 install and now I cant install anything"
date: 2010-01-30
forum: General Help
---

### Post by mushwars on 2010-01-30
I need help as soon as possible. I installed enlighenment and then I realized that netowork-manager wouldn't work on it so I installed emodule-exalt. I am not exactly sure what happened but It caused enlightenment to crash, so I went back to kde. 

Kde, for some reason lost my network-manager so I couldnt connect to the interent. So I tried to install if from a flash drive, but that didnt work

Then I tried installing wicd from a flash drive. It needed like 10 depenancies so I downloaded them and instlaled them from a flashdrive.

Then it kept telling me that I need to apt-get install -f which ofc I cant do without internet. So I booted the live cd and chrooted into my harddrive. copyed over the resolv.conf and then apt-get install -f. 
Unfortunatly that failed, with the same error in the pastebin at the end of this post. I cant install anything or remove the emodule that is causing the problem.

[http://pastebin.com/m14644b08](http://pastebin.com/m14644b08)

ps. I am not a newbie, I use gentoo on all my computers, and never have weird package problems like this, this is my brothers computer that is having the problem. Please enlighten me.

I can handle all the technobabble that you can throw at me, just tell me what to do.

Pss. I have tried in the past to just delete associating files on ubuntu, but that seems to confuse apt. So this time I decided not to do that (though in gentoo you can delete files and then just recompile. )


I hope we can come up with a solution soon. I will work with you guys. I wouldt be posting here if I could fix it on my own, I have been doing this for about 2 hours. and have no resolv. Thanks.

---

### Post by theozzlives on 2010-01-30
have you tried ```
sudo dpkg --configure -a
```

---

### Post by mushwars on 2010-01-30
> **theozzlives said:**
> have you tried ```
sudo dpkg --configure -a
```

Tried it, then tried removing the package, nothing new, same error. But thanks for the suggestion, it does look like it says something about not being able to configure.

---

### Post by infinitejones on 2010-01-30
If you reboot, then go into recovery mode from the grub menu, then drop to a root command line without network access (can't remember the exact wording but it's the option at the bottom of the list), can you then remove emodule-exalt? 

It looks like it can't remove it because it's running, and (for some reason that I don't understand) it can't stop it either. So hopefully if you re-boot and do the above, you can remove it before it even starts running.

---

### Post by NightwishFan on 2010-01-30
Try:
```
sudo apt-get -f install
```

Pay attention if it asks to remove any packages. I have found it is possible to really mess something up. I managed to break a system with PPA Nvidia drivers that never remove.

---

### Post by mushwars on 2010-01-30
> **infinitejones said:**
> If you reboot, then go into recovery mode from the grub menu, then drop to a root command line without network access (can't remember the exact wording but it's the option at the bottom of the list), can you then remove emodule-exalt? 

It looks like it can't remove it because it's running, and (for some reason that I don't understand) it can't stop it either. So hopefully if you re-boot and do the above, you can remove it before it even starts running.

I am chrooted into my brother system, NOTHING is running, I have tried removing it, it is a stubourn little thing.

---

### Post by mushwars on 2010-01-30
> **NightwishFan said:**
> Try:
```
sudo apt-get -f install
```

Pay attention if it asks to remove any packages. I have found it is possible to really mess something up. I managed to break a system with PPA Nvidia drivers that never remove.

[http://pastebin.com/m5c0692ae](http://pastebin.com/m5c0692ae)

Nope and nope.

---

### Post by infinitejones on 2010-01-30
> **mushwars said:**
> I am chrooted into my brother system, NOTHING is running, I have tried removing it, it is a stubourn little thing.

Alright, I'm really guessing here, but maybe it's the fact that you **are** chrooted in and therefore nothing is running.

Maybe (remember, I'm completely guessing) when you try and remove the package, the system assumes it ***is*** running, and tries to stop it, and throws an error when it can't.

---

### Post by NightwishFan on 2010-01-30
I found a resource that advised to remove the package manually, though I would not recommend such an action without someone more expert than I to consult.

[https://answers.launchpad.net/ubuntu/+question/14619](https://answers.launchpad.net/ubuntu/+question/14619)

---

### Post by mushwars on 2010-01-30
> **infinitejones said:**
> Alright, I'm really guessing here, but maybe it's the fact that you **are** chrooted in and therefore nothing is running.

Maybe (remember, I'm completely guessing) when you try and remove the package, the system assumes it ***is*** running, and tries to stop it, and throws an error when it can't.

Linux isnt like windows, when you dont have xorg-server running there is NOTHING running... at all. well except /bin/bash unless you have some init.d scripts. Whatever. I tried starting that service no errors. then I tried removing it same error. 

Word to the wise: Chroot in linux is THE SAME as running the actual system. The only difference is that you are running it inside another system. 

(that is how you can fix it.)

---

### Post by mushwars on 2010-01-30
> **NightwishFan said:**
> I found a resource that advised to remove the package manually, though I would not recommend such an action without someone more expert than I to consult.

[https://answers.launchpad.net/ubuntu/+question/14619](https://answers.launchpad.net/ubuntu/+question/14619)

Nah, I trust, you I was planning on doing that myself, yet I wasnt really sure what I was doing, so now that I have a guide it should be all good, thanks.

---

### Post by NightwishFan on 2010-01-30
Good luck. Please tell me if it works out.

---

### Post by mushwars on 2010-01-30
nope even that doesnt work


> root@ubuntu:/# sudo dpkg --purge --force-all exalt-daemon
sudo: unable to resolve host ubuntu
(Reading database ... 144589 files and directories currently installed.)
Removing exalt-daemon ...
invoke-rc.d: initscript exalt-daemon, action "stop" failed.
dpkg: error processing exalt-daemon (--purge):
 subprocess installed pre-removal script returned error exit status 1
update-rc.d: warning: exalt-daemon stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (S 0 1 6)
invoke-rc.d: initscript exalt-daemon, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 exalt-daemon
root@ubuntu:/#



EDIT: oops didnt read the whole post. >_< I am doing the rest of it now.

---

### Post by mushwars on 2010-01-30
YOU GUYS ARE THE BESTEST!


<3

THANKS!

all better. 

later

---

### Post by NightwishFan on 2010-01-30
Glad you got it working, enjoy.

---

