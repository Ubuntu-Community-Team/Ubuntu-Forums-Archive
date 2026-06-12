---
title: "What are the first things you need to install straight after first install of 9.10"
date: 2010-02-28
forum: General Help
---

### Post by msrie on 2010-02-28
I am new to ubuntu and linux. I have seen from playing with it for a week you need to install various apps after install, like autoconf and make.   
Can anyone name all the apps you need to install for ubuntu to run smooth and for other installations to go ahead without adding more afterwards, if you know what i mean. 
     
So you need. 
   1) Autoconf.      

What others need to be installed for your os to be good to go.  
p.s i am not talking about general apps, i am talking about apps needed to make ubuntu good to go, and to make sure all installations of future apps and patches and things, go ahead without errors.

---

### Post by aklo on 2010-02-28
I think only the restricted extras for playing different formats of media files and flash.

---

### Post by lijcam on 2010-02-28
Other the restricted formats I install libdvdcss and w64codecs for dvd and wmv playback.

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

sudo apt-get install libdvdcss2 w64codecs
``` (or w32codecs is running 32bit)

---

### Post by elliotn on 2010-02-28
> **aklo said:**
> I think only the restricted extras for playing different formats of media files and flash.

Yes ubuntu comes complete except for the restricted extras, ofcoz maybe some optional stuff, like vlc, xine but movie player can do the trick

---

### Post by zine92 on 2010-02-28
Depending on what you need but the provided software are good enough for normal usage. But this does not restrict you from installing other software. Say if you need other browser, you can go for chrome or the likes. Music player, personally i think there are a lot out there which support a variety of good codecs but i recommend songbird. And if you need to use windows software or play windows game, you can try Wine/Playonlinux. Document wise, you have a good open office unless you use microsoft office, use wine. Not sure though. And if you use msn and like me prefer other clients. you can go for amsn. And for mail client and such, you can try thunderbird. Hope that helps.

---

### Post by ajgreeny on 2010-02-28
> **msrie said:**
> I am new to ubuntu and linux. I have seen from playing with it for a week you need to install various apps after install, like autoconf and make.   
Can anyone name all the apps you need to install for ubuntu to run smooth and for other installations to go ahead without adding more afterwards, if you know what i mean. 
     
So you need. 
   1) Autoconf.      

What others need to be installed for your os to be good to go.  
p.s i am not talking about general apps, i am talking about apps needed to make ubuntu good to go, and to make sure all installations of future apps and patches and things, go ahead without errors.
Just a comment about your statement on Autoconf:  I have been using Ubuntu for 5 years now and have never once added or needed to add Autoconf, neither have I once felt the need to compile a program from source.

I just wonder if you, as a new linux and ubuntu user, are aware of just how many packages and applications are available from the repos without needing to go elsewhere for them.

The moral of this post is really to tell you always to look first in the official repos, secondly in any ppa repos that may be available, thirdly in the website of the application ityself, which may have .deb packages available, and only then maybe think about compiling a new package, if you can not find it in any of those.

---

### Post by CharlesA on 2010-02-28
Image the drive.

Then install the restricted junk.

---

### Post by azertyh on 2010-02-28
hi,
i'm new to ubuntu too. but i didnt install new applications after the installation.
as posted below, it depends on your requirements and differs from everyone.
in my case, after 2 months, i installed aptoncd, gparted (i use xubuntu), and ripper x.

---

### Post by Easy Limits on 2010-02-28
Run your Update Manager.

---

### Post by waloshin on 2010-02-28
Sudo aptitude  ufw

Sudo aptitude k3b

---

