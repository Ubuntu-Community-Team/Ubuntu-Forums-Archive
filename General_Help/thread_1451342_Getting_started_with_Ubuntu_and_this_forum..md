---
title: "Getting started with Ubuntu and this forum."
date: 2010-04-10
forum: General Help
---

### Post by Nomoore15074 on 2010-04-10
Hello all!

Well, I have always wanted to go away from the windows word and try out Linux full scale.  Over the last couple years, I have had a dual boot with xp and fedora core 3.  I found that while I wanted to learn more about linux, I'd always end up booting to windows because its the os that I know and can accomplish what I need to pretty effectively.

Recently my computer crashed and I used ubuntu 9.10 running from the cd to retrieve files from my hard drive which worked like a champ.  Since I am basically starting over, I am going make an attempt at running ubuntu and NOT loading windows...yet

SO that said, I have ubuntu 9.10 installed and I am able to do basic stuff.  I have evolution set up for mail, and am able to browse the web easily.

There are a few things I need to get figured out.

1.  I am running this on my desk top where I have a separate NTFS partition for all of our data, be it pictures spreadsheets, what ever.  I need to figure out how to share this partition so that it can be accessed by a local network ie our laptop, which we connect wireless...

2.  Some videos run slowly.  Sound is good, but the picture is a frame a second, while others seem to play fine.  I don't know where to start

3. I wnat to install thunderbird.  I downloaded the file, it archived.  In windows it would be as simple as double clicking setup.exe, but I am sad to report i don't know how to do it in linux.  I assume, I need to go to \downloads\thunderbird.whatever and issue an install command, but I honestly am not sure what to do.


I am 100% new to the forum and it's pretty technical here so a dabbling user may not know what he's looking at.  lol, I'm tryin darnit.  Can you point me in any directions at all and I'll take it from there?

---

### Post by oldos2er on 2010-04-10
This might help with Thunderbird: [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

---

### Post by lego399 on 2010-04-10
You should get to know how to use the package managers (packages are software). You should also read this: [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

---

### Post by partloer on 2010-04-10
Hi Nomoore15074,

1. For sharing across a network I would use Samba [https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba") you might be able to start by right clicking on the folder you want to share and click Sharing Options

2. What type of video are you trying to watch DVD, Online Flash, video from your hard drive, etc?

Good luck...let me know how this goes.

---

### Post by gordintoronto on 2010-04-10
First, you don't share a partition, you share a folder. Or lots of folders.

Second, you need to use Administration/Synaptic to install things, if possible. This is not Windows, you don't go to a web site and install from there. The first thing to install is the "Restricted Extras." Second is VLC media player.

Get Thunderbird via Synaptic.

Your Ubuntu installation should have full access to the Windows partition(s) by opening Places/Computer.

---

### Post by blueridgedog on 2010-04-10
Win32 codecs may help with video playback and you can get the DVD playback library at the same time:

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update &&
sudo apt-get install libdvdcss2 &&
sudo apt-get install w32codecs
```

You should be able to copy and paste the above into a terminal found at applications - accessories - terminal.

---

