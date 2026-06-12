---
title: "How do I install this .run file?"
date: 2010-03-03
forum: General Help
---

### Post by klasjosh30 on 2010-03-03
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.21&lang=English)

I just downloaded this since it says it works for my graphics card (ATI Radeon x1200 series) and I need this since my laptop is laggy playing flash games, youtube, compiz fusion. So I want to know how to install this? I tried 

Right click> Properties> Permissions tab> Check marked "allow executing file as program" I then double clicked the .run file and ran it in terminal, It did some things and I swore it installed! but I don't see or feel a difference, so how do I install this and how do I tell if its installed?

-Thanks :D

---

### Post by cariboo on 2010-03-03
If the file is on your desktop, open an Applications->Accessories->Terminal, and a the prompt type:

```
cd ~/Desktop
```

the above command changes directory to Desktop. Next at the prompt, make sure the file is executable:

```
chmod +x *run
```

This will make all the run files on your desktop executable, hopefully you only have the one file. Next at the prompt type:

```
sudo ./run
```

This should install the driver for you.

---

### Post by flippo on 2010-03-03
Unless you were running as root, I doubt it worked.  You can look though /var/log/Xorg.0.log to see if its using the driver you want (I'm not sure what the name of the proprietary ATI driver it).  

To ensure it installs correctly:

Open a terminal and cd to the directory the run file is then```
chmod +x <nameofrunfile>
sudo ./<nameofrunfile>
```

If the ATI installer is anything like the nvidia one, it will give you a curses terminal prompt (if these words are foreign you'll figure it out when you type it into a terminal) that will tell you how things are progressing.

If you have any issues please feel free to post them. :)

There may also be a "ubuntu way" to install the drivers, but I don't know it.  I usually install my (nvidia) drivers through a similar method.

Ooops, you beat me to the punch...

---

### Post by klasjosh30 on 2010-03-03
when I type sudo ./run

i get this

```
sudo: ./run: command not found
```

---

### Post by flippo on 2010-03-03
instead of ```
sudo ./run
``` it should be ```
sudo ./<nameofrunfile>
``` replacing <nameofrunfile> with the actual name of your run file.

---

### Post by klasjosh30 on 2010-03-04
```
joshua@joshua-linux:~$ cd ~/Desktop
joshua@joshua-linux:~/Desktop$ chmod +x ati-driver.run
joshua@joshua-linux:~/Desktop$ sudo ./ati-driver.run
Created directory fglrx-install.eoo4Fp
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 [COLOR=Red]ATI Technologies Linux Driver Installer/Packager [/COLOR]
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-19-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.eoo4Fp
joshua@joshua-linux:~/Desktop$

```

---

### Post by flippo on 2010-03-04
Bad news on that front :-/

[http://ubuntuforums.org/showthread.php?t=1221221]("http://ubuntuforums.org/showthread.php?t=1221221")

Someone else may have come up with a solution, but this is what a little googling popped up.

---

### Post by klasjosh30 on 2010-03-04
quote from that topic

> But....many people are very happy using the open source ati and raden drivers with that card so you should try them out before doing anything drastic.

where can I get that?

---

