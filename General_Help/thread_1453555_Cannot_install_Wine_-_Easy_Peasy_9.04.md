---
title: "Cannot install Wine - Easy Peasy 9.04"
date: 2010-04-13
forum: General Help
---

### Post by bakagaijin on 2010-04-13
I am running Easy Peasy 9.04 on an EeePC 901.

[B]I am trying to run Wine in order to install a wireless client for my university- they blocked Linux from ALL wireless because they have no one to support Linux (I.E only a windows client, no iPod or iPhone support, as they used to have). I want Wine to get me on the network while being able to work using Easy Peasy.

1. Will Wine allow me to use the wireless network in this way?[/B] 


When I try to install Wine, using the WineHQ guide ([http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)) nothing works. 

I have tried to "trust  the repository", install Wine with sudo apt-get update and all other instructions. I just keep getting:

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
paradox@paradox-laptop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libopenal1 but it is not installable
        Recommends: ttf-liberation but it is not installable
        Recommends: ttf-mscorefonts-installer but it is not installable
E: Broken packages
I am told my packages are broken and I really don't understand, as I am a noob. 

[QUOTE][wine:
 Depends: libopenal1  but it is not installable
 Recommends: ttf-liberation  but it is not installable
 Recommends: ttf-mscorefonts-installer  but it is not installable/QUOTE]

If anyone can help, I would GREATLY appreciate it. Please describe in noob terms.

---

### Post by drpjkurian on 2010-04-13
What on the world do they have to block ALL wireless to Linux... How do they do that. It seems to be impossible....

---

### Post by bakagaijin on 2010-04-14
There is no way to do a VPN, according to them and no one I've spoken with has found a way, there is no client, and there is no support, though there used to be. I used to be able to set up a VPN, but it's been changed so it cannot be done (at least easily).

When I say "blocked" I mean in the sense of being c__k blocked, not like via IP or MAC address. All windows machines are REQUIRED to pass a test (CAT) to even use the network. This includes forcing users to install updates they may not want to,  but makes everything "safer." You cannot pass the test without having EVERYTHING the scan says you need. The computer support center had a heavy flow of traffic when a "required" update for Vista caused dozens of PCs to have video issues and some could not reboot. Problems most users couldn't fix.

Anyway, is it possible to bridge easy peasy and wine to use the internet in the first place or am I wasting my time with this idea? Either way, I can't seem to install wine.

---

### Post by bakagaijin on 2010-04-16
Ok. So thanks to this thread: [http://ubuntuforums.org/showthread.php?t=1197739](http://ubuntuforums.org/showthread.php?t=1197739)   I was able to fix some things.

The issue was that I couldn't update the repository becuase it needed to pull the data from a different server. 

I was able to install WINE after that..

The only problem is that now the internet drops (literally) every minute. This is even when I have a 95% connection. There is no reason for this...is this some issue with authentication even though the netbook talks to and connects to the VPN?

---

