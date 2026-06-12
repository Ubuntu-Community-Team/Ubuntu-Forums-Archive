---
title: "Kubuntu-Desktop Removed"
date: 2006-04-15
forum: General Help
---

### Post by Intell on 2006-04-15
Somehow, kubuntu-desktop was removed from my system. Although I can still use the computer, many programs, I do not have, and neither apt-get nor aptitude are working to install or remove some packages. Is there any way to reinstall kubuntu-desktop without reinstalling kubuntu?

---

### Post by aysiu on 2006-04-15
What happens when you try to use apt-get? What error do you get?

That's the far more concerning thing. Kubuntu-desktop does not need to be installed. apt-get *should* work, though.

---

### Post by Elif Tymes on 2006-04-15
apt-get reinstall kdm kubuntu-desktop

should work?

---

### Post by aysiu on 2006-04-15
You may also want to try, if apt-get isn't working for your admin user, rebooting into **recovery mode** and trying ```
apt-get update
apt-get install --reinstall kubuntu-desktop
```

---

### Post by Intell on 2006-04-15
Yesterday I installed frozen-bubble to play with my cousins. Here's a log of me trying to remove it.
```

~$ sudo apt-get remove frozen-bubble
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  frozen-bubble
0 upgraded, 0 newly installed, 1 to remove and 106 not upgraded.
Need to get 0B of archives.
After unpacking 365kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2949 package `libtool':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
~$

```
That answers your question aysiu. :)

Should I go for reinstalling in recovery mode? You are right that kubuntu-desktop doesn't need to be reinstalled.

---

### Post by Elif Tymes on 2006-04-15
Ouch. So it looks like dpkg is dead... goto your /var/lib/dpkg directory, and copy status to status-backup and then copy status-old to status.

---

### Post by Intell on 2006-04-15
I tried that, and I got a very similar error to the first one. 
```

~$ sudo apt-get remove frozen-bubble
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  frozen-bubble
0 upgraded, 0 newly installed, 1 to remove and 120 not upgraded.
Need to get 0B of archives.
After unpacking 365kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2949 package `libtool':
 missing version
W: Encountered status field in a non-version description
W: Encountered status field in a non-version description
W: Encountered status field in a non-version description
W: Encountered status field in a non-version description
W: Encountered status field in a non-version description
W: Encountered status field in a non-version description
W: Encountered status field in a non-version description
W: Encountered status field in a non-version description
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (2)
~$

```

After running apt-get update, I get the first error again.

If it helps:

/var/lib/dpkg/status:
```

2944: Package: libtool
2945: Status: purge ok installed
2946: Priority: optional
2947: Section: devel
2948: Architecture: i386
2949:

```

---

### Post by Elif Tymes on 2006-04-15
could you do apt-get install --reinstall --force-yes dpkg?

you'll need your kubuntu CD for this.

---

### Post by Intell on 2006-04-15
To be short: no. I get the same line 2949 error.

It seems as though every package except for 'libtool' has a version number. Dpkg is complaining about that. What probably would be a temporary solution is to remove the libtool block from the status file, but that would cause me not to be able to install libtool if I needed to.

---

### Post by Mr. Swiveller on 2006-04-15
Dear Intell,

Kubuntu-desktop is a meta-package which has been linked against many of the programs that come with Kubuntu. Unfortunately, when you try to uninstall one of these programs through Adept, Kubuntu-desktop will tend be uninstalled as well - taking many other programs (such as OpenOffice) with it.

One way of preventing this variety of 'dependency hell' is by removing Kubuntu-desktop with the dpkg tool. In order to remove a package with dpkg, open a terminal and type *sudo dpkg -r [package name]*. Using --purge instead of -r will remove the package's configuration files as well. 

What is probably more relevant to your current situation, though, is that you can also use dpkg to install programs. *sudo dkpg -i [path]* will install all the deb files that are found in a particular directory, including its subdirectories. Since you've probably got the Kubuntu install CD, you could use this command to reinstall all of the packages that came with Kubuntu. Be sure to back up any crucial data in advance, though - you'd effectively be reinstalling the entire OS. An alternative would be to just select the directories you needed (if I'm not mistaken, they're all in the *pool *directory).

Cheers,

Swiveller

---

### Post by Mr. Swiveller on 2006-04-15
Oops - if dpkg is dead, much of the above is of little use...

---

### Post by Elif Tymes on 2006-04-15
Could you Delete the libtool block, then try and reinstall dpkg?

---

### Post by Intell on 2006-04-15
There are errors with the "missing version" all over my status file. With over 25000 lines in my status file, there's no way to get rid of all of them. Sadly, it won't tell me all of the errors at once.

---

### Post by Elif Tymes on 2006-04-15
Hmmm, could you do a repair off of your kubuntu CD then?

Otherwise, looks like a reinstall is in order....

---

