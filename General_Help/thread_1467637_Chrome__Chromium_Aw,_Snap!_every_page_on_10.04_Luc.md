---
title: "Chrome / Chromium: Aw, Snap! every page on 10.04 Lucid Lynx"
date: 2010-04-30
forum: General Help
---

### Post by halfsoul on 2010-04-30
Chromium no longer functions after I upgrading to 10.04 (official release).

Problem statement: Every page displays Aw, Snap! rendering error

History:
1. I had previously been using Google Chrome with 9.10 for a long time (since Linux Beta release)
2. Added Ubuntu Studio 1 week ago... Chrome still functioned
3. Upgraded to 10.04... Chrome broken
4. Removed Chrome via Synaptic
5. Installed Chromium via Software Center
6. Chromium still broken (same symptoms)

I am at a complete loss as to what I should do to troubleshoot this.  Any suggestions?

---

### Post by Marogian on 2010-05-01
Same problem, also the same with Chromium Browser from Ubuntu Software Centre...

I should add, this is a fresh install of Ubuntu 10.04 x64. I installed Chrome when I first got it and it worked okay, however I noticed after it running for an ~hour it developed an extremely bad memory leak (it ate 8GB of RAM). I force quitted it and continued. Left it running overnight (forgot about the problem) and it had nearly killed the OS. Force killed it again and decided to reboot to see if this would solve the leak.

Since rebooting neither Chrome nor Chromium will work... I can't get into the extensions options to disable them either, but I doubt this is the problem.

I have Chrome running on my netbook with a fresh Netbook Remix x32 install and it works fine- no memory leak and...yeah it works fine, so I believe this is an issue just with x64.

Hope that helps...

---

### Post by lessmemorelove on 2010-05-01
reinstall chrome if you need to back up your bookmarks.

uninstall chrome.

delete ~/.config/google-chrome or ~/.config/chromium

reinstall. reload your bookmarks. you should be set.

---

### Post by Marogian on 2010-05-01
> **lessmemorelove said:**
> reinstall chrome if you need to back up your bookmarks.

uninstall chrome.

delete ~/.config/google-chrome or ~/.config/chromium

reinstall. reload your bookmarks. you should be set.

This has no effect.

---

### Post by jamesremuscat on 2010-05-01
I've just started having the same issue. I upgraded to Kubuntu 10.04 last night and after rebooting Chrome is now "Aw, Snap"ping on every page...

Just tried running it from the console and got the error

> 7056:7072:4438293356:ERROR:/usr/local/google/b/slave/chrome-official-linux-64/build/src/base/shared_memory_posix.cc(192) Creating shared memory in /dev/shm/com.google.chrome.pPyPIs failed: No such file or directory. This is frequently caused by incorrect permissions on /dev/shm.  Try 'sudo chmod 777 /dev/shm' to fix.

Doing as the error message suggests fixes the problem - not sure I'm convinced that /dev/shm should be world-read/writeable but it gets the browser working.

---

### Post by Marogian on 2010-05-01
That got it working for me...seems a bit of an odd fix. I still have a very bad memory leak...can you check yours?

Chrome is up to 690MB and rising... :S

---

### Post by uve25 on 2010-05-01
Same problem, on karmic it works perfect. But today after fresh Lucid and Chromium installation, Chrome doesn't work. Removing of all config files won't help.

---

### Post by halfsoul on 2010-05-01
Strange, after a reboot today Chrome is suddenly working.  I'll keep that folder's permissions in mind if it starts acting up today.

> **Marogian said:**
> I still have a very bad memory leak...can you check yours?

Chrome is up to 690MB and rising... :S
Here's my info (one tab open):
chromium-browse 28.8 MiB
chromium-browser 8.8
chromium-browser 0.8
chromium-browser 12.6

---

### Post by CodPair on 2010-05-01
I found a solution(Sort of)
Chrome is a little buggy in 10.04 though, but it prevents the "Aww Snap" error.

The problem is that the old build of chrome isn't compatible with 10.04 and during the upgrade, the installer commented the chromium repositories out of sources.list

To fix it, edit sources.list:
```
sudo gedit /etc/apt/sources.list
```

Change:
```
# deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu karmic main # disabled on upgrade to lucid
```

To:
```
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu lucid main
```

Note that you may be using a different repository to get Chromium than I am so your sources.list may vary
Also note that this repository isn't trusted(I don't know why) so you'll get some scary warning messages.

After that, save and close sources.list and run:
```
sudo apt-get update
sudo apt-get upgrade
```

That got it working for me, but its rather buggy. It won't load gmail correctly(Gmail is unusable) and a few other random websites.

---

### Post by Marogian on 2010-05-03
Uh, I don't think this is solved. The previous fix doesn't really apply if you have a fresh install and install Chromium from the repos...

Memory leak is still huge- It eats about 1GB/hour.

---

### Post by parn on 2010-05-03
Have the same issue about Chromium a couple of hours ago the very moment I upgraded Chromium to 5.0.393 build.

I actually find that it is the upgrade that killed my Chromium browser. I can load "some" pages but pages with flash will definitely die.

I remove Chrome and manually installed he 5.0.391 build and I am fine now...

Just curious, is there anyone running Chromium 5.0.393 smoothly?

---

### Post by LostInBrittany on 2010-05-03
Same memory leak here.

I installed Lucid last Friday (a fresh install, I don't like dist upgrades) and everything worked right. Today I did an upgrade (including last Chromium daily) and Chromium began to act oddly : "Aw , Snap!"s, memory leak...

Edit: Yes, it worked great with 5.0.391, it is 5.0.393 that kills it...

---

### Post by Marogian on 2010-05-03
I'm using build 5.0.342.9 for both Chrome and Chromium :o

Odd. Why is my build so behind? Chrome is from the Google website and Chromium from Ubuntu Software Center.

Could someone explain how to directly install 5.0.391?

---

### Post by LostInBrittany on 2010-05-03
[quote=Marogian]
I'm using build 5.0.342.9 for both Chrome and Chromium

Odd. Why is my build so behind? Chrome is from the Google website and Chromium from Ubuntu Software Center.

Could someone explain how to directly install 5.0.391?
[/quote]

I think your build is the "official" one, the one you get from normal ubuntu repositories.
The problem is with the 5.0.393, the one from the daily chromium builds ppa repository.

To install the 5.0.391 you need to add the repository to your sources list :
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main

---

### Post by LostInBrittany on 2010-05-03
I uninstalled 5.0.393 and then I recovered my 5.0.391 debs from /var/cache/apt/archives, and I reinstalled them with dpkg. 

Everything looks good now :)

---

### Post by Chromagnum on 2010-05-03
> **parn said:**
> Have the same issue about Chromium a couple of hours ago the very moment I upgraded Chromium to 5.0.393 build.

I actually find that it is the upgrade that killed my Chromium browser. I can load "some" pages but pages with flash will definitely die.

I remove Chrome and manually installed he 5.0.391 build and I am fine now...

Just curious, is there anyone running Chromium 5.0.393 smoothly?

Yup, exactly. Upgrade to 5.0.393.0 (46027) also killed my Chromium. I'm waiting for another update. In a meantime, I installed Google Chrome 5.0.342.9 beta, and it's working perfectly great.

---

### Post by zenarcher on 2010-05-03
I'm having the same issue here (Kubuntu 10.04 64 bit) and nothing seems to fix it.  The same Chromium version is working fine with Mandriva 2010.1

Cheers,
zenarcher

---

### Post by nixIT on 2010-05-03
> **LostInBrittany said:**
> I think your build is the "official" one, the one you get from normal ubuntu repositories.
The problem is with the 5.0.393, the one from the daily chromium builds ppa repository.

To install the 5.0.391 you need to add the repository to your sources list :
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main

I too am having the Chromium problem.  I removed the chromium repositories I had, added the one above, and the chromium version in synaptic is showing 5.0.393, not 3.0.391.  :(

Any way for me to install 3.0.391?

--nixIT

---

### Post by Marogian on 2010-05-03
Yeah, instructions on how to install a specific build would be most welcome!

---

### Post by xdevnull on 2010-05-03
It's seems like these daily ppa's should have some easy commands to revert to a previous version.  This isn't the first time I've gotten a really buggy chromium and wished I could roll back to a previous version.

---

### Post by c-shadow on 2010-05-03
I did it like this:
1. disabled the daily PPA
2. uninstalled chromium-browser_5.0.393
3. from /var/cache/apt/archives/ installed chromium-browser_5.0.391

I was lucky to have this in cache :)

---

### Post by kenrowe410 on 2010-05-04
The latest update to 5.0.396 on Lucid seems to be working fine...

---

### Post by Xarijus on 2010-05-04
Can you please provide the information on how you updated to  5.0.396 version? I have  5.0.393 at the moment and repositories doesn't seem to have  5.0.396.

---

### Post by jondodson on 2010-05-04
The ppa updates can break chromium every now and then.  I prefer chromium over chrome because it's open, but I don't like being at the bleeding edge with daily 12mb updates.  Have you considered using the chromium beta channel?
[https://launchpad.net/~chromium-daily/+archive/beta](https://launchpad.net/~chromium-daily/+archive/beta)
from what I understand, it is the exact chromium equivalent of chrome, ie beta but stable.
All you have to do is delete chromium in synaptic, delete your daily ppa's from software sources, and then add the two sources given in the above link and Reinstall, you are then on the chromium beta channel.  Daily updates will no longer break your chromium.

---

### Post by kenrowe410 on 2010-05-04
> **jondodson said:**
> The ppa updates can break chromium every now and then.  I prefer chromium over chrome because it's open, but I don't like being at the bleeding edge with daily 12mb updates.  Have you considered using the chromium beta channel?
[https://launchpad.net/~chromium-daily/+archive/beta](https://launchpad.net/~chromium-daily/+archive/beta)
from what I understand, it is the exact chromium equivalent of chrome, ie beta but stable.
All you have to do is delete chromium in synaptic, delete your daily ppa's from software sources, and then add the two sources given in the above link and Reinstall, you are then on the chromium beta channel.  Daily updates will no longer break your chromium.

This is a great idea!  I'd been using the daily ppa's for a few months and never had a problem--until the latest bug.  Good to know there's an alternative...

---

### Post by nixIT on 2010-05-04
> **Xarijus said:**
> Can you please provide the information on how you updated to  5.0.396 version? I have  5.0.393 at the moment and repositories doesn't seem to have  5.0.396.

I second that.  Just installed chromium (again) via synaptic and it's still showing 5.0.393.

--nixIT

---

### Post by Marogian on 2010-05-04
I've tried 5.0.396, 5.0.393, and 5.0.342 and they all have the memory leak. This only applies to x64- my 32 bit laptop is fine for all of them.

Leave it running with a couple tabs for a few hours and the memory usage will be ~GB, leave it running overnight and it'll use up all your RAM.

This did not happen on 9.10, only **x64 10.04**.

No one else is having this?

---

### Post by halfsoul on 2010-05-04
> **Marogian said:**
> Uh, I don't think this is solved. The previous fix doesn't really apply if you have a fresh install and install Chromium from the repos...

Memory leak is still huge- It eats about 1GB/hour.
My original problem statement was "Aw, snap!" on every page, which has had several solutions posted.  Memory leak is a different issue that I am not having.  Feel free to continue discussion on that topic here, but I still consider my problem "solved".

---

### Post by Nphyx on 2010-05-13
Still having the Aw, Snap! problem as of 6.0.402 from today's nightly. Tried deleting config files, tried present version from beta repo, tried official ubuntu repo version, no luck on any of them. Also tried suggestions found elsewhere - change language & font settings. 

Must be some deeper issue here. I've noticed poor performance since updating to Lucid beta back in early April, but never crashing like this. Judging by affected sites, it seems to have something to do with javascript.

---

### Post by c-shadow on 2010-05-13
> **Nphyx said:**
> Still having the Aw, Snap! problem as of 6.0.402 from today's nightly. Tried deleting config files,  


What config files?
Did you delete the whole ~/.config/chromium folder?
Rename it if you want backup. At some point my profile got also corrupted, and this was the only option that worked.

---

### Post by Nphyx on 2010-05-13
> **c-shadow said:**
> What config files?
Did you delete the whole ~/.config/chromium folder?
Rename it if you want backup. At some point my profile got also corrupted, and this was the only option that worked.

Sorry, I should have been more specific. Yes, I deleted the entire ~/.config/chromium folder. Same results - gmail inaccessible, Ning inaccessible, several other sites. Each crashes somewhere early in the page load process. It's hard to say exactly where as the developer tools don't function either. I did restore the old settings after testing. Have tried several combinations of deleting config, removing & reinstalling different versions to no avail.

---

### Post by c-shadow on 2010-05-13
If it's not the profile then I'm all out of ideas :(
Maybe the problem is not the profile, but the installation? Look trough apt log (/var/log/apt/history.log) and see what packages got upgraded at a time chromium stopped working. Maybe some other lib causes a problem?
I would also try purging all chrome related packages and installing latest stable beta version. Stay away from nightly builds, they break things from time to time.

---

### Post by Nphyx on 2010-05-14
Oddly, purging the nightlies and moving to the older beta versions (5.0.375 I think it was) didn't seem to help me, which indicates to me that this may be something independent of Chromium. I don't know the exact day when this started happening - I tend to write off strange behaviour in Chromium as growing pains until it becomes intolerable - so I am not sure whether I can associate it with another package update. I will try that though, thanks for the suggestion.

---

