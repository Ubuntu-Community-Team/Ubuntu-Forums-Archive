---
title: "dpkg hangs on &quot;Reading database&quot; when using apt-get"
date: 2011-01-02
forum: General Help
---

### Post by garethppls on 2011-01-02
When I am using apt-get or Synaptic Package Manager it hangs on "Reading database ..." without doing anything more. 

Has anyone had such an issue before, or does anyone know how to resolve it?

It would be much much appreciated :)

---

### Post by fabricator4 on 2011-01-02
Perhaps the dpkg database has become corrupted or otherwise got out of whack, possibly because an update got interrupted at a critical time.  Open a terminal window and cd to /var/lib/dpkg.  There should be two files there called "status" and "status-old"

From my reading on this, it seems that you should be able to substitute the the status-old for the status file and cause dpkg to re-do the updates it got hung up on previously.

```
cd /var/lib/dpkg
sudo mv status status-bad
sudo mv status-old status
```

Then run update manager and see how you go.  Good luck!

Chris.

---

### Post by WlaadDyaab on 2011-01-02
Are you trying to use the "aptitude" command but it doesn't seem to work on Terminal?

---

### Post by matt_symes on 2011-01-02
Hi

Also, you could try

```
sudo apt-get install -f
```

and

```
sudo dpkg --configure -a
```

These commands might fix the issue.

Kind regards

---

### Post by garethppls on 2011-01-02
Thank you all for your replies.

The problem still remains unfortunately! :(

If there is any information that might make things clearer please ask!

---

### Post by matt_symes on 2011-01-02
Hi

can you?

```
sudo apt-get update && sudo apt-get uprgade
```

successfully?

Kind regards

---

### Post by happyhamster on 2011-01-02
Try running:
```

sudo apt-get autoclean
sudo apt-get update

```
And if that doesn't help, this command:
```

sudo dpkg --clear-avail 

```
might speed things up for you.

---

### Post by fabricator4 on 2011-01-02
Well, I'm certainly learning a lot.

It seems that even older backups of the status file are kept.  If the above excellent suggestions still don't work it might be useful to go back to a much earlier file.

look in /var/backups and you should see a series of files with names like:
dpkg.status.1.gz 
where the older the file is the higher the number it is given.  IOW the system renames each file every time, incrementing the number of each by one.

Pick one that goes back to the time _before_ you think you last had a good update and try replacing /var/lib/dpkg/status with that one.  You'll have to unpack the compressed file first of course.


```
cd /var/lib/dpkg
sudo mv status status.bak
cd /var/backups
sudo gzip -d dpkg.status.6.gz (for example only)
sudo cp dpkg.status.6 /var/lib/dpkg/status

```

Regards

Chris

---

### Post by garethppls on 2011-01-02
> **fabricator4 said:**
> Well, I'm certainly learning a lot.

It seems that even older backups of the status file are kept.  If the above excellent suggestions still don't work it might be useful to go back to a much earlier file.

look in /var/backups and you should see a series of files with names like:
dpkg.status.1.gz 
where the older the file is the higher the number it is given.  IOW the system renames each file every time, incrementing the number of each by one.

Pick one that goes back to the time _before_ you think you last had a good update and try replacing /var/lib/dpkg/status with that one.  You'll have to unpack the compressed file first of course.


```
cd /var/lib/dpkg
sudo mv status status.bak
cd /var/backups
sudo gzip -d dpkg.status.6.gz (for example only)
sudo cp dpkg.status.6 /var/lib/dpkg/status

```

Regards

Chris

I've done this, but yet it is still not going any further than "Reading database..." is the database itself corrupt in some way? Or does the system require a restart before this takes effect?

It doesn't list the number of packages, it is only stuck on the Reading database..

Matt: I can do apt-get update, but not apt-get upgrade.

---

### Post by garethppls on 2011-01-02
I don't mean to bump the thread, but I also tried following the instructions on [this thread]("http://ubuntuforums.org/showpost.php?p=4903403&postcount=5") for reconstructing the status file, but the hanging still continues. I wonder is it a deeper problem than just dpkg. 

For example output:
> gareth@gareth-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  bluetooth libgnokii6 banshee-extensions-common banshee-extension-soundmenu
  libindicate0.1-cil gnokii-common libqt3-mt
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-generic
The following packages will be upgraded:
  linux-headers-generic
1 upgraded, 0 newly installed, 0 to remove and 289 not upgraded.
Need to get 0B/5,026B of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 

---

### Post by garethppls on 2011-01-04
Extracted virtualbox from the deb (couldn't use apt-get). Ran it, started a new virtual machine with live cd, and copied /var/lib/dpkg and /usr/bin/dpkg and it is working now. I will probably try it with my old status file before long. Much thanks for all the help here, it seems my problem is partly resolved.

---

