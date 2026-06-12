---
title: "apt-get (dpkg) stuck; cannot update"
date: 2011-03-02
forum: General Help
---

### Post by raptor99 on 2011-03-02
So I've been going along, doing updates whenever I noticed, usually accepting everything... and today, the Ubuntu updater tells me [SIZE=2]**"The package system is broken"**[/SIZE]. That perhaps doing the cmd below, would do the trick. However:

user@localhost:~$ [SIZE=3][COLOR=Black]**sudo apt-get -f install**[/COLOR][/SIZE]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libfaad2
The following packages will be upgraded:
  libfaad2
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
19 not fully installed or removed.
Need to get 0B/171kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
[B][COLOR=Red]dpkg: parse error, in file '/var/lib/dpkg/status' near line 31873 package 'xserver-xorg-video-siliconmotion':
 `Conflicts' field, invalid package name ``xserver-xorg-driver-siliconmotion': must start with an alphanumeric[/COLOR][/B]

So, then **I tried to remove libfaad2 and other things that depend on it... but it just goes back to the same "xorg must start with alphanum" error.**

I'm not sure why the xorg package doesn't start with an alphanum, or how to get apt-get past the hangup.

I would image the xorg package is coming from the standard Ubuntu repos but I'm not sure.

Any ideas?

Thanks!

[COLOR=Red][B][COLOR=Black]_Things I've tried:_

[/COLOR][/B][COLOR=Black]** Ran apt-get update

**[/COLOR][/COLOR] I've looked for the apostrophe according to this post:

[http://ubuntuforums.org/showthread.php?t=1505850](http://ubuntuforums.org/showthread.php?t=1505850)

And I found a line like: Conflicts:**`**xserver-xorg-driver-siliconmotion

... but removing that apostrophe just makes the system complain for packages below that definition.
[U][B]
My Specs[/B][/U]

I'm running Ubuntu 10.10 Maverick, Kernel 2.6.35-25-generic, on an AMD-64 bit CPU, with a motherboard using an integrated ATI-Radeon 4200 graphics chip.

---

### Post by plucky on 2011-03-03
> ... but removing that apostrophe just makes the system complain for packages below that definition.

what are the errors now?

Depending on the errors you are getting now,you might have corruption on your status file.Can you post the error information.

You could try from a terminal ```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-backup
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```

The first line will move your status file to another file called status-backup,and the second line will change a file called status-old into status. 

Then run ```
sudo apt-get update
``` and see what happens.

Good Luck

---

### Post by raptor99 on 2011-03-03
Restoring status from status-old worked.

What would cause that type of corruption?

I don't usually ever play with the apt-get system so I'm surprised it became corrupted.

Thanks again!

---

