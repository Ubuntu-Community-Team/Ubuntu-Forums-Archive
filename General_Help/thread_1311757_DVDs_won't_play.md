---
title: "DVDs won't play"
date: 2009-11-02
forum: General Help
---

### Post by Deverell on 2009-11-02
Okay, 

A while ago I installed the restricted extras package using the instructions on the following [link]("https://help.ubuntu.com/community/RestrictedFormats").
I also rand the script file as directed. 

I can play mp3 files and run flash no problem and I made the assumption that DVDs worked too. 

I have a numerous working DVDs all of which refuse to play. 

Movie player reports the following error:
> Could not open location; you might not have permission to open the file

VLC opens the screen for a split second and flashes black before returning to the small toolbox. 

Any suggestions?

---

### Post by soni1770 on 2009-11-02
try out medibuntu
google mediabuntu and follow the instructs, prob work

---

### Post by coffeecat on 2009-11-02
Or more specifically, go to [http://www.medibuntu.org/](http://www.medibuntu.org/) .

Either by adding it as a repository, or by downloading the package, try installing libdvdcss2. You need that to be able to read commercial encrypted DVDs.

---

### Post by x C0MMAND0 x on 2009-11-02
```
 sudo apt-get install libdvdread4
```

Then

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

That should work.

---

### Post by Deverell on 2009-11-02
Nope, no change regarding the medibuntu link. I followed the instructions. Perhaps I haven't done something right.

Regarding the post above:
```
sean@sean-laptop:~$  sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sean@sean-laptop:~$ 

```
```
sean@sean-laptop:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2009-11-02 22:47:51--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb
Resolving packages.medibuntu.org... 88.191.82.11, 88.191.79.39
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 36812 (36K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-TsOlbS/libdvdcss.deb'

100%[======================================>] 36,812       107K/s   in 0.3s    

2009-11-02 22:47:52 (107 KB/s) - `/tmp/dvdcss-TsOlbS/libdvdcss.deb' saved [36812/36812]

(Reading database ... 158174 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.2medibuntu1 (using .../dvdcss-TsOlbS/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

Could this be a problem with VLC, would removing and reinstalling make a difference do you guys think?

---

### Post by Maheriano on 2009-11-02
This will work.

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update
```

then

```
sudo apt-get install libdvdcss2
```

You might need to reboot then but I don't think so. Anyway, that does fix your permissions issue, if it still doesn't work then you messed up something unusual.

---

### Post by Deverell on 2009-11-02
```
sean@sean-laptop:~$ sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
>  --output-document=/etc/apt/sources.list.d/medibuntu.list &&
> sudo apt-get -q update &&
> sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
> sudo apt-get -q update
--2009-11-02 22:53:38--  http://www.medibuntu.org/sources.list.d/jaunty.list
Resolving www.medibuntu.org... 87.98.242.110
Connecting to www.medibuntu.org|87.98.242.110|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 280 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 280         --.-K/s   in 0s      

2009-11-02 22:53:38 (26.6 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [280/280]

Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_IE
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_IE
Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_IE
Hit http://ie.archive.ubuntu.com jaunty Release.gpg
Ign http://ie.archive.ubuntu.com jaunty/main Translation-en_IE
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com stable/main Translation-en_IE
Ign http://ie.archive.ubuntu.com jaunty/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com jaunty/universe Translation-en_IE
Ign http://ie.archive.ubuntu.com jaunty/multiverse Translation-en_IE
Hit http://ie.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://ie.archive.ubuntu.com jaunty-updates/main Translation-en_IE
Ign http://ie.archive.ubuntu.com jaunty-updates/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com jaunty-updates/universe Translation-en_IE
Ign http://ie.archive.ubuntu.com jaunty-updates/multiverse Translation-en_IE
Get:2 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_IE
Get:3 http://dl.google.com stable Release [2540B]
Hit http://ie.archive.ubuntu.com jaunty Release
Get:4 http://ppa.launchpad.net jaunty Release [74.7kB]
Ign http://ppa.launchpad.net jaunty Release
Hit http://ie.archive.ubuntu.com jaunty-updates Release
Get:5 http://dl.google.com stable/main Packages [665B]
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_IE
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://packages.medibuntu.org jaunty Release.gpg
Ign http://packages.medibuntu.org jaunty/free Translation-en_IE
Hit http://ie.archive.ubuntu.com jaunty/main Packages
Hit http://ie.archive.ubuntu.com jaunty/restricted Packages
Hit http://ie.archive.ubuntu.com jaunty/main Sources
Hit http://ie.archive.ubuntu.com jaunty/restricted Sources
Hit http://ie.archive.ubuntu.com jaunty/universe Packages
Hit http://archive.canonical.com jaunty Release
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_IE
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_IE
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_IE
Hit http://ie.archive.ubuntu.com jaunty/universe Sources
Hit http://ie.archive.ubuntu.com jaunty/multiverse Packages
Hit http://ie.archive.ubuntu.com jaunty/multiverse Sources
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_IE
Hit http://packages.medibuntu.org jaunty Release
Hit http://ie.archive.ubuntu.com jaunty-updates/main Packages
Hit http://ie.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://ie.archive.ubuntu.com jaunty-updates/main Sources
Hit http://ie.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://ie.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://ie.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://archive.canonical.com jaunty/partner Packages
Hit http://packages.medibuntu.org jaunty/free Packages
Hit http://archive.canonical.com jaunty/partner Sources
Hit http://security.ubuntu.com jaunty-security Release
Hit http://packages.medibuntu.org jaunty/non-free Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://ie.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://ie.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Fetched 3702B in 1s (3253B/s)
Reading package lists...
[B]W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8DB7F87A2B97B7B8
W: You may want to run apt-get update to correct these problems[/B]
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_IE
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_IE
Hit http://ie.archive.ubuntu.com jaunty Release.gpg
Ign http://ie.archive.ubuntu.com jaunty/main Translation-en_IE
Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_IE
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://ie.archive.ubuntu.com jaunty/restricted Translation-en_IE
Ign http://ie.archive.ubuntu.com jaunty/universe Translation-en_IE
Ign http://ie.archive.ubuntu.com jaunty/multiverse Translation-en_IE
Hit http://ie.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://ie.archive.ubuntu.com jaunty-updates/main Translation-en_IE
Ign http://ie.archive.ubuntu.com jaunty-updates/restricted Translation-en_IE
Ign http://dl.google.com stable/main Translation-en_IE
Ign http://ie.archive.ubuntu.com jaunty-updates/universe Translation-en_IE
Ign http://ie.archive.ubuntu.com jaunty-updates/multiverse Translation-en_IE
Hit http://archive.canonical.com jaunty Release
Hit http://ie.archive.ubuntu.com jaunty Release
Get:2 http://dl.google.com stable Release [2540B]
Hit http://ie.archive.ubuntu.com jaunty-updates Release
Hit http://archive.canonical.com jaunty/partner Packages
Get:3 http://dl.google.com stable/main Packages [665B]
Hit http://ie.archive.ubuntu.com jaunty/main Packages
Hit http://ie.archive.ubuntu.com jaunty/restricted Packages
Hit http://ie.archive.ubuntu.com jaunty/main Sources
Hit http://ie.archive.ubuntu.com jaunty/restricted Sources
Hit http://ie.archive.ubuntu.com jaunty/universe Packages
Hit http://archive.canonical.com jaunty/partner Sources
Hit http://ie.archive.ubuntu.com jaunty/universe Sources
Hit http://ie.archive.ubuntu.com jaunty/multiverse Packages
Hit http://ie.archive.ubuntu.com jaunty/multiverse Sources
Hit http://ie.archive.ubuntu.com jaunty-updates/main Packages
Hit http://ie.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://ie.archive.ubuntu.com jaunty-updates/main Sources
Hit http://ie.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://ie.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://ie.archive.ubuntu.com jaunty-updates/universe Sources
Get:4 http://ppa.launchpad.net jaunty Release.gpg [307B]
Ign http://ppa.launchpad.net jaunty/main Translation-en_IE
Hit http://packages.medibuntu.org jaunty Release.gpg
Ign http://packages.medibuntu.org jaunty/free Translation-en_IE
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_IE
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_IE
Hit http://ie.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://ie.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_IE
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_IE
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_IE
Hit http://packages.medibuntu.org jaunty Release
Hit http://security.ubuntu.com jaunty-security Release
Hit http://packages.medibuntu.org jaunty/free Packages
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://packages.medibuntu.org jaunty/non-free Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Get:5 http://ppa.launchpad.net jaunty Release [74.7kB]
Ign http://ppa.launchpad.net jaunty Release
Hit http://ppa.launchpad.net jaunty/main Packages
Hit http://ppa.launchpad.net jaunty/main Sources
Fetched 3702B in 1s (2890B/s)
Reading package lists...
[B]W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8DB7F87A2B97B7B8
W: You may want to run apt-get update to correct these problems[/B]

```

What do these errors mean? I will run apt-get update now and report back in a few secs.

```
sudo apt-get update
```

Produces the following error as well.

```
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8DB7F87A2B97B7B8
W: You may want to run apt-get update to correct these problems

```

---

### Post by coffeecat on 2009-11-02
That means that you haven't added the gpg key for Launchpad. That must be a repo you added earlier. That's nothing to do with Medibuntu. But from your output I can see that you've imported the Medibuntu gpg key and the Medibuntu package metadata, but I can't see that you've installed libdvdcss2. You need libdvdcss2 for DVD playback.

---

### Post by Deverell on 2009-11-02
> **coffeecat said:**
> **That means that you haven't added the gpg key for Launchpad.** That must be a repo you added earlier. That's nothing to do with Medibuntu. But from your output I can see that you've imported the Medibuntu gpg key and the Medibuntu package metadata, but I can't see that you've installed libdvdcss2. You need libdvdcss2 for DVD playback.


I don't know what the highlighted text means. 

I've installed libdvdcss2, just not through the terminal. I got the packages off the medibuntu site and opened them using my GUI package manager. Is it saying that it isn't installed? Very strange. 

What is the best course of action?

---

### Post by coffeecat on 2009-11-02
> **Deverell said:**
> I don't know what the highlighted text means. 

A gpg key validates that the packages you are downloading are genuine. It's a security measure. You have to import a gpg key for each repository that you enable - basically to tell the system that the repo is trustworthy - otherwise you get that message. To suppress the error you need to go back to the howto that you used to add the Launchpad repo - there *should* be instructions to import the gpg key.

> **Deverell said:**
> I've installed libdvdcss2, just not through the terminal. I got the packages off the medibuntu site and opened them using my GUI package manager. Is it saying that it isn't installed? Very strange.

No that's OK. I couldn't see the 'sudo apt-get install libdvdcss2' in your post. Three of us were giving different instructions to get the same end result. :) If you've installed libdvdcss2 through the GUI it will be installed OK, and will show up in Synaptic now as installed.

Did libdvdcss2 fix the DVD playing problem? I've slightly lost the plot here. :p

---

### Post by Deverell on 2009-11-02
> **coffeecat said:**
> 
No that's OK. I couldn't see the 'sudo apt-get install libdvdcss2' in your post. Three of us were giving different instructions to get the same end result. :) If you've installed libdvdcss2 through the GUI it will be installed OK, and will show up in Synaptic now as installed.

Did libdvdcss2 fix the DVD playing problem? I've slightly lost the plot here. :p

No, problems remains. I will take the following steps. 

1. Restart my Computer. 
2. Sort our the gp key thingermabobber
3. Report back here.

---

### Post by Deverell on 2009-11-02
Back, I just noticed that the code supplied should handle the gpg key. Specifically this line. 
```
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring
```

Any reason why this one line of code may have produced my stated output.

---

### Post by Maheriano on 2009-11-02
Can you go to System - Administration - Software Sources and post here which sources you have listed in the Other Software tab? A screenshot would be best but you can copy and paste.

---

### Post by Deverell on 2009-11-03
[IMG]http://img59.imageshack.us/img59/214/screenshotsoftwaresourc.png[/IMG]

I followed your instruction as accurately as I could. I didn't see an "other" tab.

---

### Post by batterybaby on 2009-11-03
it might be not the right pattern that  it could read. some DVDcannot be suitable with the laptop.

---

### Post by Deverell on 2009-11-08
Embarrassing as it may seem the problem was simple. 

The DVDs I had were all *Region 1* i.e. American. My *Region 2* DVDs did play no problem. 

Thanks to all those who contributed, 
Sorry.

---

### Post by Maheriano on 2009-11-09
Run the 9to5 converter, that might do it. I seem to remember that being a location converter maybe I'm wrong.

---

