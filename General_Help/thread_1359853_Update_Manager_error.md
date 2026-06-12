---
title: "Update Manager error"
date: 2009-12-20
forum: General Help
---

### Post by irv on 2009-12-20
After trying to install a print driver for a Brothers printer, I can't use my update manager. I believe this is where the problem started. I am including a couple of screen shots to help. the first one tells me my software index is broken, so I ran the command "sudo apt-get install -f" but this did not work. I have the package dcp1000pr marked for complete removal but it will not remove it. Is there a way to manually remove it? Is there a way to fix this problem? Any help would be great.
[ATTACH]140634[/ATTACH]

[ATTACH]140635[/ATTACH]

Thanks
Irv

---

### Post by scragar on 2009-12-20
What is the output of ```
sudo apt-get install -f
```

---

### Post by irv on 2009-12-20
Here is the out put:
```
irv@irv-new-laptop:~$ sudo apt-get install -f
[sudo] password for irv: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dcp1000lpr
0 upgraded, 0 newly installed, 1 to remove and 37 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 337639 files and directories currently installed.)
Removing dcp1000lpr ...
/var/lib/dpkg/info/dcp1000lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing dcp1000lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 dcp1000lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
irv@irv-new-laptop:~$ 

```

---

### Post by lrcaballero on 2009-12-20
Try this:

System/Administrator/Synaptic Package Manager

in the left hand side window click BROKEN, see if there's anything there that needs attention and just follow-through.

Luis

---

### Post by irv on 2009-12-20
Nothing Broken.

---

### Post by irv on 2009-12-21
I really need to find an answer to this problem because I can't install any programs, and I need to do so.

---

### Post by irv on 2009-12-21
This is the output when I try to install a program with apt-get:
```
irv@irv-new-laptop:/media/disk/Stem_Publishing$ sudo apt-get install tree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  dcp1000lpr
The following NEW packages will be installed:
  tree
0 upgraded, 1 newly installed, 1 to remove and 37 not upgraded.
2 not fully installed or removed.
Need to get 0B/30.1kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 337639 files and directories currently installed.)
Removing dcp1000lpr ...
/var/lib/dpkg/info/dcp1000lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing dcp1000lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 dcp1000lpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
irv@irv-new-laptop:/media/disk/Stem_Publishing$ 

```
As you can see I am getting an error status 127 and the removing of dcp1000lpr causes the process to stop so noting gets removed or installed.

---

### Post by Soul-Sing on 2009-12-21
source "plucky":
dcp1000lpr is going wilde....

> Open a terminal and ```
gksudo gedit /var/lib/dpkg/status
```
Click on Search, rightcorner of the screen, and then Find and search for dcp1000lpr

This is what you should find Package: dcp1000lpr
Status: deinstall reinstreq half-installed
Maintainer: Brother Industries, Ltd.
Architecture: i386
Version: 1.1.2-1
Description: Brother lpr Printer Definitions
Copyright: 2003 Brother Industries, Ltd. All Rights Reserved
Brother printer Driver

Delete it all then Save the file and then exit from gedit.


You can now use Synaptic Package Manager again.

Synaptic search for dcp-1000 and you will find the LPR and Cupswrapper drivers for the DCP-1000 printer.Mark both for installation and apply.

---

### Post by irv on 2009-12-21
> **leoquant said:**
> source "plucky":
dcp1000lpr is going wilde....




You can now use Synaptic Package Manager again.

Synaptic search for dcp-1000 and you will find the LPR and Cupswrapper drivers for the DCP-1000 printer.Mark both for installation and apply.

This post really helped. I can now install software again and I did the updates. 35 updated but then I get an error because the print driver is still half installed. I did a search for the dcp-1000 in the package manger but it does not find it. I also have Cupswarpper2170w. I did try to uninstall the Cupswarpper2170w, it did uninstall but I still get the error.

---

### Post by Soul-Sing on 2009-12-21
In this stadium what is the exact errormessage you get?
(that would be really helpful)

---

### Post by irv on 2009-12-21
[ATTACH]140786[/ATTACH]
This is the error I get.

---

### Post by Soul-Sing on 2009-12-21
```
sudo dpkg --remove hl1270nlpr
```

prob. you get an /etc/init.d/< >: Permission denied

---

### Post by bodhi.zazen on 2009-12-21
Simply make a 'dummy" file

```
sudo nano /etc/init.d/lpd
```

Put soem code in there:

```
#!/bin/sh

/bin/true
exit 0
```

Then re-run apt-get install -f or remove the package.

---

### Post by Soul-Sing on 2009-12-21
Or uninstall it also via post #8

---

### Post by irv on 2009-12-22
> **leoquant said:**
> ```
sudo dpkg --remove hl1270nlpr
```

prob. you get an /etc/init.d/< >: Permission denied

When I run the code, I get this:
```
irv@irv-new-laptop:~$ sudo dpkg --remove hl1270nlpr
[sudo] password for irv: 
(Reading database ... 338964 files and directories currently installed.)
Removing hl1270nlpr ...
/var/lib/dpkg/info/hl1270nlpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl1270nlpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1270nlpr
irv@irv-new-laptop:~$ 

```

---

### Post by irv on 2009-12-22
> **bodhi.zazen said:**
> Simply make a 'dummy" file

```
sudo nano /etc/init.d/lpd
```

Put soem code in there:

```
#!/bin/sh

/bin/true
exit 0
```

Then re-run apt-get install -f or remove the package.
Ok, I tried this and here is what happen:
```
irv@irv-new-laptop:~$ sudo gedit /etc/init.d/lpd
irv@irv-new-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  hl1270nlpr
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 338951 files and directories currently installed.)
Removing hl1270nlpr ...
/var/lib/dpkg/info/hl1270nlpr.postrm: 3: /etc/init.d/lpd: Permission denied
dpkg: error processing hl1270nlpr (--remove):
 subprocess post-removal script returned error exit status 126
Errors were encountered while processing:
 hl1270nlpr
E: Sub-process /usr/bin/dpkg returned an error code (1)
irv@irv-new-laptop:~$ 

```

---

### Post by Soul-Sing on 2009-12-22
```
sudo gedit /var/lib/dpkg/info
```
remove hl1270nlpr
(use the search option)

```
sudo gedit /var/lib/dpkg/status
```
remove hl1270nlpr
(use the search option)

sudo apt-get update
sudo apt-get upgrade

---

### Post by irv on 2009-12-22
> **leoquant said:**
> ```
sudo gedit /var/lib/dpkg/info
```
remove hl1270nlpr
(use the search option)

```
sudo gedit /var/lib/dpkg/status
```
remove hl1270nlpr
(use the search option)

sudo apt-get update
sudo apt-get upgrade

On the command sudo gedit /var/lib/dpkg/info I get the following:
[ATTACH]140844[/ATTACH]
It appears to be a directory and not a file.
If I go into the info directory I find these files:
[ATTACH]140845[/ATTACH]
I did run the sudo gedit /var/lib/dpkg/status and removed the entry that had the hl1270nlpr in it.
That's as far as I went, I didn't run the update and I am not sure I want to upgrade yet. I am working on some big projects and I don't want to screw up my computer by doing a upgrade at this time.

---

### Post by Soul-Sing on 2009-12-22
navigate via ```
gksudo nautilus
``` to /var/lib/dpkg/info
sorry its a file indeed..

This is howfar my knowlegde goes....
Maybe another member of this forum could take a look at this.....

---

### Post by irv on 2009-12-22
> **leoquant said:**
> navigate via ```
gksudo nautilus
``` to /var/lib/dpkg/info
sorry its a file indeed..

This is howfar my knowlegde goes....
Maybe another member of this forum could take a look at this.....

I really appreciate all the help. Thanks.
I know you are saying it is a fil indeed. but all I see is the directory. Inside the directory there are some files with the name info, so I took a screen shot of the dpkg and the info directories. 
 [ATTACH]140851[/ATTACH]   [ATTACH]140852[/ATTACH]
Do you see the file I am to edit.

---

### Post by Soul-Sing on 2009-12-22
it is as said (sorry for the dutch/english file/direct. confusing)
[COLOR="Red"]/var/lib/dpkg/info[/COLOR] not the info-file within it. so the right picture of the attachment is the place to be.

> That's as far as I went, I didn't run the update and I am not sure I want to upgrade yet. I am working on some big projects and I don't want to screw up my computer by doing a upgrade at this time.

I would be glad, for the above reason, if someone else could look at this thread. I hope you understand this.....(although a sudo apt-get update would give needed additional information)

---

### Post by irv on 2009-12-22
> **leoquant said:**
> it is as said (sorry for the dutch/english file/direct. confusing)
[COLOR="Red"]/var/lib/dpkg/info[/COLOR] not the info-file within it. so the right picture of the attachment is the place to be.



I would be glad, for the above reason, if someone else could look at this thread. I hope you understand this.....(although a sudo apt-get update would give needed additional information)

I deleted all the files starting dealing with the 1270 driver as seen in post number 18 screen shot and this fixed the error that kept coming up. Everything seems to be working fine again so we can put this thread to rest. 
Thanks again for the time and all the help on this one. I put the word [Solved] in the title on this one.

---

### Post by Soul-Sing on 2009-12-22
Glad I could help

---

### Post by conradin on 2010-02-11
> **leoquant said:**
> source "plucky":
dcp1000lpr is going wilde....

```

gksudo gedit /var/lib/dpkg/status

```



Yes, this post was helpful, I had a partial upgrade fail part way through, with lucid Lynx. I deleted Everything in the status file. Now I have a fresh list of updates! THIS was helpfull to fix my broken updater. Nothing was working before, ubuntu one, synaptic, and update mgr were all failing. 
Thanks sooooo MUCH!

---

