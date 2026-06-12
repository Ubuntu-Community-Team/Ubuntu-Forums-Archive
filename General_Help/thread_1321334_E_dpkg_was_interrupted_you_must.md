---
title: "E: dpkg was interrupted you must"
date: 2009-11-10
forum: General Help
---

### Post by T2av on 2009-11-10
When trying to install any updates or anything really from synaptic, or from the terminal I get 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

When I type "sudo dpkg --configure -a" I get the following

sudo dpkg --configure -a

dpkg: parse error, in file `/var/lib/dpkg/updates/0001' near line 26 package `man-db':
 duplicate pending trigger `/usr/share/man'

I'm stuck and have no idea how to fix this..
(*Ubuntu* 9.04)

---

### Post by DougieFresh4U on 2009-11-10
try 
```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by T2av on 2009-11-10
hmmm I have no idea..... I tried this aswell
sudo dpkg --clear-selections

---

### Post by T2av on 2009-11-10
tried that already..didnt work..
```
sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

---

### Post by ranch hand on 2009-11-10
You might want to look at synaptic under status and see if there are broken packages.  Synaptic is good for fixing them too.

Then try the "sudo dpkg --configure -a" again.

---

### Post by Jayferd on 2009-11-10
Have you tried Synaptic's Edit->Fix Broken Packages ?

---

### Post by T2av on 2009-11-10
Unable to do anything with synaptic, Just error, then crash.
[[IMG]http://img691.imageshack.us/img691/8148/screenshotcs.th.png[/IMG]]("http://img691.imageshack.us/i/screenshotcs.png/")
[http://img691.imageshack.us/i/screenshotcs.png/](http://img691.imageshack.us/i/screenshotcs.png/)

---

### Post by ranch hand on 2009-11-10
Wow, you are jammed up somehow.  I will watc this with interest and hope someone can straighten it out.

I hope so, it has all the makings of a keeper.

---

### Post by MelDJ on 2009-11-10
tried : [https://answers.launchpad.net/ubuntu/+source/apt/+question/43750](https://answers.launchpad.net/ubuntu/+source/apt/+question/43750) ?

---

### Post by T2av on 2009-11-10
> **MelDJ said:**
> tried : [https://answers.launchpad.net/ubuntu/+source/apt/+question/43750](https://answers.launchpad.net/ubuntu/+source/apt/+question/43750) ?

Tried, no avail......


> **ranch hand said:**
> Wow, you are jammed up somehow. I will watc this with interest and hope someone can straighten it out.

I hope so, it has all the makings of a keeper.

lol thanks for your *enthusiasm*

---

### Post by ranch hand on 2009-11-10
Well not all of us can be so lucky as to break something in an interesting way.

I am running an early 10.04testing version (on my test platform - nowhere near this, my main drive) after all the FUN we had around A4 through 5 of 9.10.

I never new how to chroot into a system before that.

---

### Post by Kevbert on 2009-11-10
Please try this:
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update
```

---

### Post by T2av on 2009-11-10
> **Kevbert said:**
> Please try this:
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update
```

```

stevekim@stevekim:~$ cd /var/lib/dpkg
stevekim@stevekim:/var/lib/dpkg$ sudo mv status status-bad
stevekim@stevekim:/var/lib/dpkg$ sudo cp status-old status
cp: cannot stat `status-old': No such file or directory
stevekim@stevekim:/var/lib/dpkg$ sudo cp status-old status
cp: cannot stat `status-old': No such file or directory
stevekim@stevekim:/var/lib/dpkg$ sudo apt-get update
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release
Hit http://us.archive.ubuntu.com jaunty Release
Hit http://us.archive.ubuntu.com jaunty-updates Release             
Hit http://security.ubuntu.com jaunty-security/main Packages        
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://security.ubuntu.com jaunty-security/restricted Packages
Hit http://security.ubuntu.com jaunty-security/main Sources
Hit http://security.ubuntu.com jaunty-security/restricted Sources
Hit http://security.ubuntu.com jaunty-security/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

---

### Post by T2av on 2009-11-10
> **Kevbert said:**
> Please try this:
```
cd /var/lib/dpkg
sudo mv status status-bad
sudo cp status-old status
sudo apt-get update
```

after doing this.. I get this now..

[[IMG]http://img694.imageshack.us/img694/9651/screenshotnb.th.png[/IMG]]("http://img694.imageshack.us/i/screenshotnb.png/")


This is new too. never got this till I did the above quote.

[[IMG]http://img40.imageshack.us/img40/9936/screenshot1kt.th.png[/IMG]](http://img40.imageshack.us/i/screenshot1kt.png/)

---

### Post by layingback on 2009-11-11
I have same original problem as OP.  But at least I know what CAUSED it.  But not how to fix.

Attempted to install a package using a script to add new repository to Sources, without realising that for a part of the package it was also adding getdeb's repo.  Now I am blocked from getdeb like all other O2 and Be customers, so Synaptic went into an UNINTERRUPTIBLE retry loop trying to add getdeb, all with Cancel button greyed out.  Eventually, as in 15 minutes later, I was forced to reboot or kill Synaptic process, nothing more gentle had any effect.

I could initially run the suggested sudo dpkg --configure -a command, except that just retries the add getdeb repo again, and I'm back to kill'ing Synaptic.  

But now there are updates waiting I can't even do that.

Anyone any ideas?  'Cos I can't update at mo' and 9.10 does need its updates ...

---

### Post by ranch hand on 2009-11-11
Well, maybe I had better add to this.

System crashed while updating.  This was not on 9.10.  It is on 10.04testing.

There is no difference, worth spit, between the two right now.

Got the same problem and couldn't boot in either.  Got to a terminal and ran "sudo fsck".  This should not be done from your Desktop.  Had all kinds aof thing wrong and just said yes to fixing everything  (no data to loose yet, can start over).  Ran "sudo dpkg --configure -a" almost came out clean.  Some giberish about /var/lib/dpkg/alternatives being screwy.

I haven't a clue as to what to do with that.  However, I have another testing install, slightly different, right next door on the drive.  Copied the file from there and replaced my old one after saving it to another location.  Went through the files and make them match by putting files in from my old one or just deleting them from the new.

Closed things up and, in terminal ran "sudo dpkg --configure -a" and just got the prompt back as a response.  Everything seems to work fine now.

It did take about an hour.

---

### Post by Rajesh_Marak on 2009-11-20
For Mini 910, I  was able to resolve the Customer's issue by running the same command in terminal
 
sudo dpkg --configure -a 
 
Thanks,
Rajesh Marak

---

