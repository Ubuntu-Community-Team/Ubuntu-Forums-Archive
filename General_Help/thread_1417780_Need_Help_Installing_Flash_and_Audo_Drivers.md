---
title: "Need Help Installing Flash and Audo Drivers"
date: 2010-02-27
forum: General Help
---

### Post by tpho2500 on 2010-02-27
When Ubuntu attempts to install Adobe Flash it says it is not the right architecture (i386) which I assume means 32bit. I am using a 64 bit OS but there were no options to download the 64 Bit version. 

I am quite new to Ubuntu (my 2nd day on it) so if you do give help can you please use simple terms? I am computer literate in Windows. 

Audio Drivers: 
I tried downloading the Realtek High Defintion Audio Drivers for Linux but they do not work, they were last updated in 2004. After installation I cannot hear any of my songs through Amarok.

---

### Post by garvinrick4 on 2010-02-27
Copy and paste this Code into a terminal.

sudo apt-get install ubuntu-restricted-extras


Should load all you need.

Make sure your partners repository is checked in System/Admin/Software Sources and
then the other software tab.

---

### Post by darolu on 2010-02-27
If restricted extras doesn't work (by the way, you can also look for this package in the Software Center), you can try installing the flash plug in with (in command line):
```
sudo apt-get install flashplugin-nonfree
```

For your sound problem, check this guide: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

If you do see a speaker icon (top right corner) it's probable that your sound card is already configured. A lot of users in IRC have solved the sound issue by choosing the right sound output, they had Digital output enable when using the analog output, chances are good this is your problem. Double click the icon and browse the options.

---

### Post by lovinglinux on 2010-02-27
> **garvinrick4 said:**
> sudo apt-get install ubuntu-restricted-extras

> **darolu said:**
> ```
sudo apt-get install flashplugin-nonfree
```

Both methods above will install the 32bit.

For 64bit see [this](http://ubuntuforums.org/showthread.php?t=1358591).

You can also remove any conflicting plugins and install the appropriate version of flash with an [automated installer created by carlee](http://ubuntuforums.org/showthread.php?t=1414595).

For additional tips and instructions see the [COLOR="Sienna"]**Flash Optimization**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by tpho2500 on 2010-02-27
> **garvinrick4 said:**
> Copy and paste this Code into a terminal.

sudo apt-get install ubuntu-restricted-extras


Should load all you need.

Make sure your partners repository is checked in System/Admin/Software Sources and
then the other software tab.

> **darolu said:**
> If restricted extras doesn't work (by the way, you can also look for this package in the Software Center), you can try installing the flash plug in with (in command line):
```
sudo apt-get install flashplugin-nonfree
```

For your sound problem, check this guide: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

If you do see a speaker icon (top right corner) it's probable that your sound card is already configured. A lot of users in IRC have solved the sound issue by choosing the right sound output, they had Digital output enable when using the analog output, chances are good this is your problem. Double click the icon and browse the options.

Got this error

```

Setting up sun-java6-doc (6-15-1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by tpho2500 on 2010-02-27
Bump?

---

### Post by lovinglinux on 2010-02-27
> **tpho2500 said:**
> Bump?

See my previous post.

---

### Post by tpho2500 on 2010-02-28
> **lovinglinux said:**
> See my previous post.
I still have the sound problem. It's driving me nuts.
This is the 2nd day I've been spending solving all my problems.

---

### Post by garvinrick4 on 2010-02-28
go to add-remove programs and add your Java's or which ever way you load your programs. After that then try sudo apt-get install ubuntu-restricted-extras


ubuntu-restricted-extras has a lot of things including your codecs to make all your media play. 

first work on the java problem. Never seen it myself but sure looking like it wants it installed. Its in your repositorys you need to load them.

Then worry about sound if it is not working post here. Keep working at it. Ubuntu is worth the learning curve. If I can get it, any one can. 

Now it seems a good problem is actually fun. There is always a reason why.

---

### Post by tpho2500 on 2010-02-28
> **garvinrick4 said:**
> go to add-remove programs and add your Java's or which ever way you load your programs. After that then try sudo apt-get install ubuntu-restricted-extras


ubuntu-restricted-extras has a lot of things including your codecs to make all your media play. 

first work on the java problem. Never seen it myself but sure looking like it wants it installed. Its in your repositorys you need to load them.

Then worry about sound if it is not working post here. Keep working at it. Ubuntu is worth the learning curve. If I can get it, any one can. 

Now it seems a good problem is actually fun. There is always a reason why.
What do you mean by "go to add-remove programs"
Do you mean Ubuntu Software Center or Synaptic Package Manager?
And how do I load the Java into my repositories? What link do I add to the sources.list?

---

### Post by tpho2500 on 2010-02-28
Ok that solved my Flash problem, but that still didn't fix the sound..
when I try to change the output it doesn't list anything.

---

### Post by 3rdalbum on 2010-02-28
> **tpho2500 said:**
> When Ubuntu attempts to install Adobe Flash it says it is not the right architecture (i386) which I assume means 32bit. I am using a 64 bit OS but there were no options to download the 64 Bit version.

There is a 64-bit version at Adobe Labs, or you can use the Flash Player PPA:

```
sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install flashplugin64-installer
```

Always look for software in the repositories (or in third-party repositories/PPAs) first, before trawling the web for software.

Also note that it's possible to do those three commands entirely with a GUI, but it's much quicker to use the terminal for this.

> Audio Drivers: 
I tried downloading the Realtek High Defintion Audio Drivers for Linux but they do not work, they were last updated in 2004. After installation I cannot hear any of my songs through Amarok.

I'm not surprised. Current Realtek drivers are already in the kernel and you've replaced them with ancient ones. In fact I'm surprised they installed at all. I don't know how to reverse what you've done - maybe try reinstalling your kernel? (use Synaptic to reinstall the "linux-image-2.6.31-19-generic" package, or to install it if it's not already installed).

I don't know about your other problem with the Java documentation. Can you not just remove that package?

---

### Post by tpho2500 on 2010-02-28
Adobe - Installed but the issue I have now is that I can watch videos on youtube for example but I can't navigate through the videos

Java - Removed the doc installation

Audio - doing what you said now

---

### Post by garvinrick4 on 2010-02-28
> **tpho2500 said:**
> What do you mean by "go to add-remove programs"
Do you mean Ubuntu Software Center or Synaptic Package Manager?
And how do I load the Java into my repositories? What link do I add to the sources.list?
Well I guess you do not have that installed. It is in your repositorys, just use what ever
system you use to download and install your Java. There are 3 or 4 just do them all so you
do not go wrong. And then on to ubuntu-restricted-extras to install.

---

### Post by tpho2500 on 2010-02-28
> **garvinrick4 said:**
> Well I guess you do not have that installed. It is in your repositorys, just use what ever
system you use to download and install your Java. There are 3 or 4 just do them all so you
do not go wrong. And then on to ubuntu-restricted-extras to install.

Java is Solved so thank you

Audio - Reinstalled the linux-image whatever you call it, still no sound

When I do ubuntu-restricted-extras to install i get 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Sound is still not working. Btw I'm testing on Youtube and the Rhythmbox Music player.

Adobe Flash:

Error when doing sudo apt-get update
```

W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: Duplicate sources.list entry http://archive.canonical.com karmic/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_karmic_partner_binary-amd64_Packages)

```

Last command worked fine but now all youtube videos show a blank white box

Ok everything is working, here's the guide i followed

```

http://ubuntuforums.org/showthread.php?t=1316634

```

THANKS FOR YOUR HELP EVERYONE.

---

