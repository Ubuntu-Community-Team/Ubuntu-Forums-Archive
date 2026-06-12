---
title: "Firefox 3.6.6 help!"
date: 2010-06-30
forum: General Help
---

### Post by starcraftmaster on 2010-06-30
Hi.
I today tried to install Firefox 3.6.6.
After finding out , it did not get all plugin(flash , java and so on) so I wanted to put back the oringinal firefox.
But because I uninstalled it it wont work and Firefox 3.6.6 works.
I tried to uninstall and reinstall it throught Synaptic Package Manager but it still wont work.

Please help , I dont feel like installing flash and all them plugins all over again.

There is two firefox icons , both go to Firefox 3.6.6

---

### Post by Scunnered on 2010-06-30
Having just finished with the Update Manager today I was asked to restart Firefox. On checking FF it is the version that you are looking for.

I would imagine that if you update you might get lucky.

Best of luck

---

### Post by okplayer02 on 2010-06-30
Which two versions are you talking about? 
do you mean 3.6.4 and 3.6.6?
Give us clearer picture what you mean and how did you install 3.6.6 version was it via synaptic?

---

### Post by starcraftmaster on 2010-06-30
Ok
I uninstalled Firefox 3.5.9.
I did this [https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds](https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds) 
which would not work as I needed root to run it( I tried it a few times , putting the Firefox unzip folder in my root user folder and putting it in the main filesystem and it not have all the plugins.
I updated it (the folder was 3.6.3) , still needed root and did not have all the the plugins(dont feel like reinstalling them)


I then installed it from a website that had Firefox 3.6.6 it converted in a .deb package.
I then forced AMD64 in Terminal as it was i386 file.
It worked fine , but in addon part it said it had no plug ins.
So I tried uninstalling it , but could find out how to uninstall it and 
[https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds](https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds)
 said to just delete the folder , so I did.( there is a lot of FF folders on my filesystem harddrive, but I did take away the firefox 3.6.6).
Then I tried installing 3.5.9 back via Synaptic Package Manager which did not work as when I click on the FF icon it starts 3.6.6.

I really dont know what I have done.
Im quite a Linux noob but can get myslef around.

---

### Post by chrisccoulson on 2010-06-30
> **starcraftmaster said:**
> Ok
I uninstalled Firefox 3.5.9.
I did this [https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds](https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds) 
which would not work as I needed root to run it( I tried it a few times , putting the Firefox unzip folder in my root user folder and putting it in the main filesystem and it not have all the plugins.
I updated it (the folder was 3.6.3) , still needed root and did not have all the the plugins(dont feel like reinstalling them)


I then installed it from a website that had Firefox 3.6.6 it converted in a .deb package.
I then forced AMD64 in Terminal as it was i386 file.
It worked fine , but in addon part it said it had no plug ins.
So I tried uninstalling it , but could find out how to uninstall it and 
[https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds](https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds)
 said to just delete the folder , so I did.( there is a lot of FF folders on my filesystem harddrive, but I did take away the firefox 3.6.6).
Then I tried installing 3.5.9 back via Synaptic Package Manager which did not work as when I click on the FF icon it starts 3.6.6.

I really dont know what I have done.
Im quite a Linux noob but can get myslef around.

I'm assuming you are running Ubuntu 9.10 (karmic)? If that's the case, and you can wait 1 more week or so, then you will get 3.6.6 automatically anyway

---

### Post by starcraftmaster on 2010-06-30
> **chrisccoulson said:**
> I'm assuming you are running Ubuntu 9.10 (karmic)? If that's the case, and you can wait 1 more week or so, then you will get 3.6.6 automatically anyway

How ?
Ubuntu going to update to that ?
What if all my plugins are not there ?
Do I have to reinstall flash and vlc player and so on ?

---

### Post by philinux on 2010-06-30
I'm running 10.04 and firefox just got updated though update manager to 3.6.6

All plugins and addons working fine.

---

### Post by okplayer02 on 2010-06-30
> **starcraftmaster said:**
> How ?
Ubuntu going to update to that ?
What if all my plugins are not there ?
Do I have to reinstall flash and vlc player and so on ?

Like he said just wait for the new release to come out for Karmic and its better always to install via Synaptic. I mean since you are new its better in the end. Even for me i dont install any other way :) just easier to keep track what is on your machine. you can also install the flash, java plugins via synaptic also.

---

### Post by MacHaddock on 2010-06-30
> **philinux said:**
> I'm running 10.04 and firefox just got updated though update manager to 3.6.6

All plugins and addons working fine.

My firefox doesn't work at all after the update.

[http://ubuntuforums.org/showthread.php?t=1520924]("http://ubuntuforums.org/showthread.php?t=1520924")

---

### Post by yeleek on 2010-06-30
> **philinux said:**
> I'm running 10.04 and firefox just got updated though update manager to 3.6.6

All plugins and addons working fine.

+1 No problems here - and using:
Adblock Plus
Downthemall
NoScript
Webdeveloper

---

### Post by Deadite81 on 2010-06-30
After my update to 3.6.6 on Ubuntu 10.04 32bit Flash playback no longer works.  There is just a gray box.  The Flash plugin is installed, enabled, and the lastest version.

Everything was working fine in FF 3.6.3.  Should I just downgrade, or has someone found a fix?  Why would an update be pushed that breaks my video playback?

---

### Post by apteryx7369 on 2010-07-09
> **Deadite81 said:**
> After my update to 3.6.6 on Ubuntu 10.04 32bit Flash playback no longer works.  There is just a gray box.  The Flash plugin is installed, enabled, and the lastest version.

Everything was working fine in FF 3.6.3.  Should I just downgrade, or has someone found a fix?  Why would an update be pushed that breaks my video playback?

I've having the same problem as yours, have you find a solution to it yet? anyone? thanks!

---

### Post by Deadite81 on 2010-07-09
I have found a solution, but it might not help you much.

Are you using the repositories for the experimental GNOME Shell or RGBA Transperancy?

If so, purge GNOME Shell and disable rgba system wide.  If not, try installing the Flash AID Firefox extension.

---

