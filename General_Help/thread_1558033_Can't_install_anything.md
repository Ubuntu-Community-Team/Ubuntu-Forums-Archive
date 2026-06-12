---
title: "Can't install anything"
date: 2010-08-21
forum: General Help
---

### Post by phase constant on 2010-08-21
Ok so I did some stupid stuff and tried to install some of the Backtrack 4 tools.  

Now when I tried to install VLC player in terminal I get this:

"ph@top:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libavcodec51 but it is not going to be installed
       Depends: libqt4-core but it is not going to be installed
       Depends: libqt4-gui but it is not going to be installed"


This may be of some use:

"ph@top:~$ cat /etc/apt/sources.list
deb [http://archive.offensive-security.com](http://archive.offensive-security.com) pwnsauce main microverse macroverse restricted universe multiverse"


I tried to uninstall by doing;

Sytem> Admin > Software Sources 

and then selected the "Other Software" tab.

Where I found:

[http://archive-offensive-security.com](http://archive-offensive-security.com) pwnsauce main microverse macroverse restricted universe multiverse

I checked the box and hit remove, however it would not go away.

Please help.

---

### Post by dagdeniz on 2010-08-21
try to remove in manually:

sudo nano /etc/apt/sources.list

---

### Post by scrooge_74 on 2010-08-21
you could manually install those dependencies you know

sudo apt-get install name_of_those_other_packages.

Or just use synaptic

---

### Post by phase constant on 2010-08-21
> **dagdeniz said:**
> try to remove in manually:

sudo nano /etc/apt/sources.list


Ok I did this and just deleted the whole line and then hit save.

Now this is what I get:

ph@top:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: vlc-nox (= 1.0.6-1ubuntu1) but it is not going to be installed
       Depends: libxcb-keysyms1 (>= 0.3.6) but it is not installable
       Recommends: vlc-plugin-pulse (= 1.0.6-1ubuntu1) but it is not going to be installed
E: Broken packages

---

### Post by phase constant on 2010-08-21
And my sources say:

ph@top:~$ cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe

---

### Post by dagdeniz on 2010-08-21
Looks like "main" is missing there, and "libxcb-keysyms1" which cannot be installed, is in the main repos. May this be the reason? 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe     multiverse

It should look like this. After editing the file, run "sudo apt-get update" and try to reinstall. If it doesn't install, that means the package collides with another package on our system.

---

### Post by phase constant on 2010-08-21
> **dagdeniz said:**
> Looks like "main" is missing there, and "libxcb-keysyms1" which cannot be installed, is in the main repos. May this be the reason? 
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main universe     multiverse

It should look like this. After editing the file, run "sudo apt-get update" and try to reinstall. If it doesn't install, that means the package collides with another package on our system.


Great I think this worked.

I got VLC installed.

Now I'm doing this:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

to install the restricted formats. 

I get these errors in VLC:

 p, li { white-space: pre-wrap; }  [COLOR=#FF0000]Playback failure:[/COLOR]
 [COLOR=#000000]VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.[/COLOR]

[COLOR=#000000][/COLOR]

p, li { white-space: pre-wrap; } 
[COLOR=#FF0000]No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this.[/COLOR]
 




I only really care about the sound, I could care less about a title.  Anyway to get a proper decoder?
[COLOR=#000000][/COLOR]

 [COLOR=#000000][/COLOR]

---

### Post by phase constant on 2010-08-21
Ok so I was able to play the previews on the DVD. However they all play individually, like 1-2 min each preview. VLC just closes by itself after the last preview.

---

### Post by ricardisimo on 2010-12-30
I have a DVD image which gives this error in VLC:
> Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disc.
No suitable decoder module:
VLC does not support the audio or video format "undf". Unfortunately there is no way for you to fix this.
Totem in command line gives this error:
> ** Message: Error: Could not read from resource.
resindvdsrc.c(1098): rsn_dvdsrc_step (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
Failed to read next DVD block. Error: Encrypted or faulty DVD

** Message: Error: No URI set
gstplaybin2.c(3475): setup_next_source (): /GstPlayBin2:play
I suspect the image file itself is corrupt, but am posting here on the off chance that maybe there's a quick fix. I've never had this issue with any of many, many other disc images.

---

