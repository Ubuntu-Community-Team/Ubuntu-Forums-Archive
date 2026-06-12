---
title: "Ubuntu Software Center not working"
date: 2011-05-03
forum: General Help
---

### Post by Fungle10 on 2011-05-03
Hi, I recently installed ubuntu 11.04 after testing it on a live usb. When I tested it on live USB the software center worked as it should, However, Now I've installed it, it doesnt search or get any apps it just keeps the loading animation going!

My internet works fine and connects fine so I dont know what is wrong with it.

Also, The update manager doesnt work I get this error:

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

---

### Post by jmmeyer on 2011-05-03
> **Fungle10 said:**
> Hi, I recently installed ubuntu 11.04 after testing it on a live usb. When I tested it on live USB the software center worked as it should, However, Now I've installed it, it doesnt search or get any apps it just keeps the loading animation going!

My internet works fine and connects fine so I dont know what is wrong with it.



I have the exact same problem. during the evaluation, I installed several packages, and everythng worked fine. once I committed and let U take over the whole disk, I can't seem to load any or even see a listing beyond the initial categories.

 I tried a few things I found online, including 
"sudo apt-get update && apt-get upgrade" and even tried to use "apt-cdrom" to try and load software from the USB stick, but I really didn't know what I was doing. I did add the "cdrom" repository in the "sources" dialog in the software center, but nothing I try gets the software center to do anything but spin the little icon.

---

### Post by odysseus2k7 on 2011-05-03
> **Fungle10 said:**
> Hi, I recently installed ubuntu 11.04 after testing it on a live usb. When I tested it on live USB the software center worked as it should, However, Now I've installed it, it doesnt search or get any apps it just keeps the loading animation going!

My internet works fine and connects fine so I dont know what is wrong with it.

Also, The update manager doesnt work I get this error:

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

I'm having the same problem.  It worked perfectly this afternoon.  Also, it won't connect to the Ubuntu Cloud, which is really annoying as I use that all the time.

---

### Post by GoldNugget on 2011-05-03
Same problem here. Apt-get build-dep says:
"Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages"
It also complains about no header:
"Encountered a section with no Package: header"

Ideas?

I wonder if I replace the offensive MergeList with a 'clean' one, It might fix the problem. 

Can anyone copy their working copy of /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages" and post it? 

Other suggestions welcome.

---

### Post by jmmeyer on 2011-05-03
I don't know if this is relevant, but I just tried to use synaptic pkg manager and got this error:

"E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report."

---

### Post by pAsM on 2011-05-03
Hello,
[INDENT]Can you try a 
```
sudo apt-get clean
sudo apt-get autoclean
```
[/INDENT]

---

### Post by GoldNugget on 2011-05-04
sudo apt-get clean returns me to the command line.
sudo apt-get autoclean gives me this:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by odysseus2k7 on 2011-05-04
> **pAsM said:**
> Hello,
[INDENT]Can you try a 
```
sudo apt-get clean
sudo apt-get autoclean
```
[/INDENT]

Tried it.  Got the following error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive/ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

I should add that this problem only affects my netbook.  My desktop accesses the cloud and software center just fine.

odysseus2k7

---

### Post by jmmeyer on 2011-05-04
I didn't have a lot invested in my install, so I decided to try again, just in case something had gone wrong with the process.   I forgot to mention that when I tried to install from the ubiquity tool while running on the live USB, it failed to work. So I had rebooted to the boot menu and chose &quot;install to hard drive&quot;.  I'm guessing that maybe something got wonked on the USB from either running off of it and adding software, or something got over written when I tried to install from the running live USB.  I re-wrote the USB stick from the iso, and then chose the &quot;install to hard drive option&quot; from the start. I told it to erase and re-install 11.4. Once the install was done, it tried to reboot, but after it got all the processes stopped it hung and I had to power down and restart with the switch. (I remember now that it did that on my first install as well).    It came up from the hard drive and software center is now working. I just installed chromium with no problem. So it looks like it may be working ok. I am going to mess with it for a while and see what happens.  I have no idea what went wrong, but there is definitely something not right with the ubiquity installer running from the USB. I hope this info helps someone figure out what the bug might be.   Edit: I am also using a netbook, in particular an HP mini 1030r

---

### Post by Mohammad Ansarin on 2011-05-04
> **Fungle10 said:**
> Hi, I recently installed ubuntu 11.04 after testing it on a live usb. When I tested it on live USB the software center worked as it should, However, Now I've installed it, it doesnt search or get any apps it just keeps the loading animation going!

My internet works fine and connects fine so I dont know what is wrong with it.

Also, The update manager doesnt work I get this error:

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

I had the same two problems. I managed to fix the second one; read this guys: [http://ubuntuforums.org/showthread.php?p=10760591#post10760591](http://ubuntuforums.org/showthread.php?p=10760591#post10760591)
The first (About the software center not functioning) I still haven't been able to get my head around.

It's absolutely unprofessional to release a new upgrade before certain bugs are fixed. Unity's got many, and they're major; not the little tiny kinds you see running up your backpack every now and then :)

---

### Post by odysseus2k7 on 2011-05-05
So, to summarize:  The errors we are experiencing are
1 - Synaptic won't work
2 - Update Manager won't work and returns an error
3 - Ubuntu One refuses to connect
4 - Ubuntu Software Center is not functional
 
Our internet connections are unaffected.
 
Are we all using netbook/notebooks?  Is the problem replicated on desktop systems?  My netbook's connectivity to the four services above is pretty much hosed, but my HP desktop appears to work fine.  
 
odysseus2k7
 
The final question is, how many of us are going to switch to a different release because of this?

---

### Post by da_buddar on 2011-06-01
[SOLVED]
> **plucky said:**
> ```
sudo rm /var/lib/apt/lists/*
```

It will complain about removing a "partial" directory,just ignore it.Then run ```
sudo apt-get update
``` to reload the index files.

Good Luck
[http://ubuntuforums.org/showthread.php?t=1727282](http://ubuntuforums.org/showthread.php?t=1727282)

Dunno if any of you found this. Solved the same issue you were having with all same specs and as a notebook user.

I followed the suggested rerun on sudo apt-get update

If not another user suggested the edit of the dir that the error message mentioned 
with gksu gedit /(the directory mentioned in the error) and remove the offending term listed (usually a update source)

---

### Post by jdlangel on 2011-06-02
Hi, I had the same problem and I did exactly what the comment #4 says in [http://ubuntuforums.org/showthread.php?p=10760591#post10760591](http://ubuntuforums.org/showthread.php?p=10760591#post10760591)
And problem solved!

---

