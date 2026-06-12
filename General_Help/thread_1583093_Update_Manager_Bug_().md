---
title: "Update Manager Bug (?)"
date: 2010-09-27
forum: General Help
---

### Post by sevenfactorial on 2010-09-27
Hello,

A strange thing happened to my Update Manager, and I would appreciate any advice on fixing it.  

I was installing some updates recently (I think it was the most recent kernel update) when I had a system freeze.

[DIGRESSION]
This frequently happens to me after I close and reopen my laptop and seems related to the hard drive ceasing to respond, but anyway that's beside the issue.  I don't think the problem was directly related to the update itself, because in retrospect I realize that the system was acting fritzy before I began the download/install.  In particular "plugin-container" from firefox was taking 40% of my CPU and firefox hogging resources is often a sign that my hard drive issue is acting up.  I digress!
[/DIGRESSION]

The system was frozen in mid-install (I waited!) so I did a hard reboot.  

Now when I start the Update Manager I get the following message:
> 
A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'When I try to run "sudo dpkg --configure -a" from the command line, I get

> 
dpkg: parse error, in file `/var/lib/dpkg/status' near line 1:
 field name `ssl_get_msg_callback_arg' must be followed by colonThis is totally beyond me, and I would appreciate any help.

Hunter

---

### Post by drs305 on 2010-09-27
Try changing to the 'backup' version of /var/lib/dpkg/status.

The following commands will rename the original file, make the backup the primary, and then attempt to update your repository lists.
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad # rename status file
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status # copy status backup file and name it status  
sudo apt-get update  # see if problem is solved

```

If not, return things the way they were:
```
sudo cp /var/lib/dpkg/status.bad /var/lib/dpkg/status
```
We may be able to repair the file manually if the first set of commands don't fix it.

---

### Post by sevenfactorial on 2010-09-27
Hi,  thanks!

I ran the commands.  It didn't fix the problem, but the error message changed.  When the backup was used, I got the message:

> $ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 field name `untu-dvd-live,' must be followed by colon

Thank you for helping.

Hunter

---

### Post by Soul-Sing on 2010-09-27
imo you have to "edit" the field name `untu-dvd-live,' ==> to
ubuntu-dvd-live,' via gksudo nautilus 
navigate to /var/lib/dpkg/updates/0000 (near line 1)

close nautilus.

```
sudo rm /var/lib/dpkg/lock
```
and a ```
sudo apt-get update
```
Is the "normal" way to unlock dpkg. and build it up again with this error : 
> 'E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

---

### Post by sevenfactorial on 2010-09-27
Hi,  thank you!

I tried those changes.  

Somewhat funnily, the error message is now:

> 
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 field name `ubuntu-dvd-live,' must be followed by colon

with "ubuntu" spelled out correctly.

I tried the lock remove command before I got the above error.

What do I do if nothing works out?  Reinstall?

H.

---

### Post by Soul-Sing on 2010-09-27
```
sudo dpkg --clear-avail && sudo apt-get update
```

any errors?

---

### Post by sevenfactorial on 2010-09-27
Thanks!

Yes, I get the following errors

> Fetched 2448B in 0s (3462B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C95C0E19386B7051
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

When I run dpkg --configure -a, I get 

> 
dpkg: parse error, in file `/var/lib/dpkg/updates/0000' near line 1:
 field name `ubuntu-dvd-live,' must be followed by colon

H.

---

### Post by Soul-Sing on 2010-09-27
```
sudo rm /var/lib/dpkg/updates/0000
```

```
sudo apt-get update
```

---

### Post by sevenfactorial on 2010-09-27
Brilliant!

I removed 0000 as you said and then I had an error with 0001  !

But after backing them up, I deleted all the numbered files (I think there were five or six of them).

Afterwards, update manager was fixed.

Thank you for all your help!

Hunter

---

### Post by Soul-Sing on 2010-09-28
Great, welldone! :)

---

