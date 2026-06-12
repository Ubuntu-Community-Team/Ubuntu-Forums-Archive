---
title: "In a GDM startup pickle"
date: 2010-10-24
forum: General Help
---

### Post by Sunships on 2010-10-24
Hi everyone, I have got myself into a bit of a mess, and though I have made some progress fixing the problem(s) on my own, the time has come to ask for the help of the community :D

It all started with me trying to fix my blocky Plymouth splash screen. None of the fixes that involved fiddling with resolution settings worked, and I came across one which suggested re-installing the graphics for my nVidia graphics card. This involved a "purge" command, and evidently was not a good idea. I have been able to restore the drivers for my graphics card, and the system is back to to its former glory, but currently the system will not automatically boot into gdm, and this is a major hassle. 

Instead, following grub, I am presented with a paragraph of text which describes various hardware checks, and ends with something similar to "Checking battery status". If I do nothing , the system remains at this point indefinitely. By hitting Alt-F2 I am able to bring up a login prompt, and after logging in I am able to use "sudo service gdm start" to bring up the familiar desktop environment (note that using startx at this point instead results in a blank screen, and my only recourse is to hit the power button to initiate a system shutdown). 

I have tried the usual culprits, ie the "login screen" manager and the other tweaks which all state that the system should be starting up using gdm, but something fundamental is preventing this from happening.

What have I missed? Is it possible to make the computer start up in gdm by default once more, without all this text-based hoop-jumping? I really, really do not want to completely re-install Ubuntu because of this because I just got everything working exactly the way I want it, and I am sure that the fix is something really simple, and that there is an expert out there who knows just what to do!

Thank you for reading this far! Any and all suggestions will be considered. I am happy to display the output of any diagnostic commands and even though I mentioned that most of the standard login managers don't show anything wrong, please do not be afraid to ask me to check these simple things, because I do not have an encyclopaedic knowledge of these menus and may well have missed something.

THANK YOU FOR YOUR TIME.

EDIT: I realise that this may be a very archaic problem to fix. Is there a way to reinstall the base system while keeping all my other files and things intact? I was considering using remastersys to make an installable cd of my current system, and using that to install over my current system. However, if this just copies the current configuration I might end up with the same problem again. I also have Civ4 installed through Wine (a very large game that runs in Windows), and doubt that this will also get included with any backup I make(!)

---

### Post by wojox on 2010-10-24
Try forcing a file system check

```
sudo touch /forcefsck
```

Then reboot.

---

### Post by katykat on 2010-10-24
Do you have a backup of /etc laying around anywhere? 

Backup your original and try replacing /etc/X11, and if that dont work, possibly the entuire /etc directory. 

I always keep a backup copy of a good working  /etc (/etc-working) in case things get putzed up. 

If you dont have a backup, you can compare your directory against that of a boot disk, especially /etc/X11/default-display-manager  which should have a single entry:
/usr/sbin/gdm (in Meerkat at least). 

Hope this helps....

---

### Post by Sunships on 2010-10-25
Thanks for posting, both of you.

```
sudo touch /forcefsck
``` didn't seem to do anything. I rebooted and had to go through the same procedure to reach the desktop.

Currently my default display manager reads: /usr/bin/gdm

Should I change this to: /usr/sbin/gdm?

---

### Post by Sunships on 2010-10-25
*bump*

---

### Post by Moozillaaa on 2010-10-25
> **Sunships said:**
> Is there a way to reinstall the base system while keeping all my other files and things intact? 

Possibly you can do this, by booting up Live, and copying gdm (/etc/gdm), and all its' sub-folders, from the Live load into your internal files' identical place. Just do 'Merge', and 'Replace', at the prompts.

I just did this with Karmic, and I don't imagine 10.10 is different.

I actually did it from another machine, not the live load, and it worked. The live load would be more likely to work perfectly too...

---

### Post by Sunships on 2010-10-25
> **Moozillaaa said:**
> Possibly you can do this, by booting up Live, and copying gdm (/etc/gdm), and all its' sub-folders, from the Live load into your internal files' identical place. Just do 'Merge', and 'Replace', at the prompts.

I just did this with Karmic, and I don't imagine 10.10 is different.

I actually did it from another machine, not the live load, and it worked. The live load would be more likely to work perfectly too...

Hm, I'll give it a go....be right back (I hope! ;))

---

### Post by Sunships on 2010-10-25
> **Sunships said:**
> Hm, I'll give it a go....be right back (I hope! ;))

I did it, and made it back to tell the tale...sadly this did not fix the problem.

---

### Post by Sunships on 2010-10-25
*bump*

---

### Post by Sunships on 2010-10-25
*bump*

---

### Post by Sunships on 2010-10-25
I found this link:

[http://ubuntuforums.org/showthread.php?t=1407060&highlight=reinstall+base+system](http://ubuntuforums.org/showthread.php?t=1407060&highlight=reinstall+base+system)

Apparently if you plug this into terminal it should re-install most of the packages:

```
sudo su root -c "echo apt-get clean && apt-get update --fix-broken && echo -e '#\x21/bin/bash\\n\\nfor pkg in \x60dpkg --get-selections | egrep -v deinstall | awk \x27{print \$1}\x27 | egrep -v \x27(x11-common|libc|libss2|libstdc|libpam|libgcc|liblaunch pad|libtext-wrap|lsb-base|passwd|upstart|dpkg|debconf|perl-base|python|apt|initscripts|sysv|coreutils|bash|my sql|virtuoso|mythtv|anjuta|dash|diff)\x27\x60 ; do pkgs=\"\$pkgs \$pkg\"; done\\necho \"The Following Apt-Get Command Was Run:\\\n--------------------------------------\\\n\\\napt-get -y -m --force-yes install --reinstall\$pkgs\\\n\\\nCommand Output Log:\\\n-------------------\\\n\" > reinstallationlog.txt\\napt-get -y -m --force-yes install --reinstall\$pkgs | tee -a reinstallationlog.txt' > reinstall.sh && clear && echo -e \"\\nSetting Script Permissions...\\\n------------------------------\" && chown -v root:root reinstall.sh && chmod +x -v reinstall.sh && echo -e \"\\nStarting Package Re-Installation Process...\\n-------------------------------------------\" && sh reinstall.sh && echo -e \"\\nThe re-installation process is complete. A log of the process can be found in the file called 'reinstallationlog.txt'.\""
```

Worth a shot?

---

### Post by katykat on 2010-10-25
Check /bin for gdm. 
I do not believe it would be there. 
(Very strange if it was).

Look under /user/sbin
or possibly 
/user/bin

And put the correct path in that file. 




> **Sunships said:**
> Thanks for posting, both of you.

Currently my default display manager reads: /usr/bin/gdm

Should I change this to: /usr/sbin/gdm?

---

### Post by Sunships on 2010-10-25
> **katykat said:**
> Check /bin for gdm. 
I do not believe it would be there. 
(Very strange if it was).

Look under /user/sbin
or possibly 
/user/bin

And put the correct path in that file.

You are absolutely right - the correct path was indeed /usr/sbin/gdm

I changed my default-display-manager file to match this, and voila; the system now boots directly into gdm. I must have edited it manually at some point in my experimentations and not done it correctly. Thank you so much katykat, and everyone else who posted!

---

