---
title: "Help with java! Getting very frustrated"
date: 2011-08-07
forum: General Help
---

### Post by Tlrlvll on 2011-08-07
Okay so here's the story....
I attempted the get the rpm version of java 34 bit. THis was working to no avail because i was constantly getting this message when i tried to execute it
Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50&#65279; of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu). inflating: jre-6u26-linux-i586.rpm
./jre-6u26-linux-i586-rpm.bin: 160: rpm: not found
then someone suggested using the 64 bit version. When i treid to execute than it prompted me to uss apt-get rpm. Now when i try to excuted either size files i get this error message 
Unpacking...
Checksumming...
Extracting...
UnZipSFX 5.50 of 17 February 2002, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-6u26-linux-i586.rpm  
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: Failed dependencies:
	/bin/basename is needed by jre-1.6.0_26-fcs.i586
	/bin/cat is needed by jre-1.6.0_26-fcs.i586
	/bin/cp is needed by jre-1.6.0_26-fcs.i586
	/bin/gawk is needed by jre-1.6.0_26-fcs.i586
	/bin/grep is needed by jre-1.6.0_26-fcs.i586
	/bin/ln is needed by jre-1.6.0_26-fcs.i586
	/bin/ls is needed by jre-1.6.0_26-fcs.i586
	/bin/mkdir is needed by jre-1.6.0_26-fcs.i586
	/bin/mv is needed by jre-1.6.0_26-fcs.i586
	/bin/pwd is needed by jre-1.6.0_26-fcs.i586
	/bin/rm is needed by jre-1.6.0_26-fcs.i586
	/bin/sed is needed by jre-1.6.0_26-fcs.i586
	/bin/sort is needed by jre-1.6.0_26-fcs.i586
	/bin/touch is needed by jre-1.6.0_26-fcs.i586
	/usr/bin/cut is needed by jre-1.6.0_26-fcs.i586
	/usr/bin/dirname is needed by jre-1.6.0_26-fcs.i586
	/usr/bin/expr is needed by jre-1.6.0_26-fcs.i586
	/usr/bin/find is needed by jre-1.6.0_26-fcs.i586
	/usr/bin/tail is needed by jre-1.6.0_26-fcs.i586
	/usr/bin/tr is needed by jre-1.6.0_26-fcs.i586
	/usr/bin/wc is needed by jre-1.6.0_26-fcs.i586
	/bin/sh is needed by jre-1.6.0_26-fcs.i586
PLEASE HELP

---

### Post by Wim Sturkenboom on 2011-08-07
Any reason why you're trying to install a RPM? Isn't it in the repositories?

Did you see the below message in the output (specifically the first line)?
```

rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...

```

Further, please provide the command that you used and place the results between [noparse]```
 and 
```[/noparse]. The latter makes it easier to read.

Note:
Ages ago I had this dependency hell with RPMs (not sure which distro); not sure under which distro it was. The trick (in those days) was not to install the single rpm, but using a wildcard instead; this works if there are multiple RPMs that each provide a different part.

---

### Post by decrepit on 2011-08-07
Ubuntu out of the box is not set up to use rpm packages. If you don't know what you're doing it's best not to use them.
Most stuff is in the ubuntu repos via synaptic package manager.

---

### Post by ~!geek!~ on 2011-08-07
As you are posting on ubuntuforums, so I am assuming you are using ubuntu.
Try to avoid rpm packages for ubuntu as they are not meant for ubuntu. They are for red hat linux. Get the other .bin packages instead for ubuntu.

If you are not choosy about sun's latest java, you may install java from repositories. 

But if you are like those who try to work with latest java, you would have to install java manually, For this, you follow tutorial at this link (Its for java 6 update 13, a bit outdated but you should be able to follow it without any problem.)
[http://ubuntuforums.org/showthread.php?p=6991957](http://ubuntuforums.org/showthread.php?p=6991957)

One more thing, "Relax!!! no need to get frustrated!! Learning working with linux means learning by spending time with it. You are progressing with an active community. Believe that there is very less chance, you getting stuck with a problem, 'no one else has faced before'.

---

### Post by darthvader39560 on 2011-08-07
try the .deb package or look in the package manager
for Java.

---

### Post by Zill on 2011-08-07
Tlrlvll:  As others on this thread have suggested, unless you are a Linux "expert" you shouldn't try to install rpm packages on Ubuntu, which uses the Debian (deb) packaging system.

If you are new to both Ubuntu and Linux then I suggest you should stick to *only* installing deb packages **for your particular distro**, either from the Software Center, the GUI package manager Synaptic, or apt-get via the terminal.  This is far easier than trying to install software from source and is far more reliable than downloading packages from dubious internet sites.

The quickest and easiest way to install useful functionality (including Java) is by installing the package ubuntu-restricted-extras:
```
sudo apt-get install ubuntu-restricted-extras
```

This single package pulls in support for MP3 playback and decoding, support for various other audio formats (GStreamer plugins), Microsoft fonts, [COLOR="Red"]Java runtime environment[/COLOR], Flash plugin, LAME (to create compressed audio files), and DVD playback.

---

