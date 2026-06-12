---
title: "File Permissions Problem"
date: 2011-11-19
forum: General Help
---

### Post by bigred1600 on 2011-11-19
On 11.10; I am unable to write to an NTFS partition on my hard drive.

When I check file permission on the drive, folder access is set to "Access Files"
When I attempt to change to  "Create & Delete" I get a Read Only Error.
I am having the same error with a 500Gb USB drive I have.

With only a few Gig left on my 80Gb hard drive and no way of offloading to the 500 im a little stuck. :confused:

Suggestions appreciated, beware, terminal is not my forte!

---

### Post by hwttdz on 2011-11-20
I think what it boils down to is that you'll have to add packages which allow writing to ntfs drives: [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

NTFS isn't an ideal filesystem for linux, but if you require the ability to access files from both linux and windows I believe your choices are either ntfs or fat32.  Though I think that at some point windows was able to write to ext2 or ext3 through the installation of additional drivers.

---

### Post by bigred1600 on 2011-11-20
I Really Shouldn't have to add anything, I have Been running the same setup since 10.04 without issue until recently.
Especially strange since the USB Hard drive is having the same trouble.
No issues reading/writing from windoze to partition or usb drive.
No problems reading/writing on usb harddrive on another 11.10 laptop.
Really don't want to entertain a re-install but it's lookin like a somewhat straightforward solution at the moment.

Just noticed that with the "check file system" command, it tells me that the USB drive is NOT clean. Same with the partition on the hard drive I cant write to.

Suggestions anyone?

---

### Post by fdrake on 2011-11-20
```

sudo aptitude install ntfs-3g libntfs-3g75
sudo reboot now

```
try again!

---

### Post by bigred1600 on 2011-11-20
**_Fixed..._** First class sir. Really appreciate the help.

But why did something that worked fine for months, suddenly stop working for no reason?


> **fdrake said:**
> ```

sudo aptitude install ntfs-3g libntfs-3g75
sudo reboot now

```
try again!

---

### Post by fdrake on 2011-11-20
> **bigred1600 said:**
> **_Fixed..._** First class sir. Really appreciate the help.

But why did something that worked fine for months, suddenly stop working for no reason?
you have probably installed an app that has removed Fuse due to dep issues. installing ntfs-3g you have also reinstalled missing dep with fuse.. i guess.
you r welcome

---

