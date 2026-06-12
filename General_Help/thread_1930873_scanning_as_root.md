---
title: "scanning as root"
date: 2012-02-24
forum: General Help
---

### Post by dockalek on 2012-02-24
Hi, I have a Samsung CLX 3185 multifnkc printer. I did what this guy says, to download a driver, and it works 
[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)
With scanning I'm having troubles though. His advice is to scan as root. In ubuntu 11.10 there's no logging in as root, so I don't know what to do. I added myself to the "lp" group. But I don't know what to do next. So, my question is: how do you scan as root?

---

### Post by fcomstoc on 2012-02-24
In Ubuntu the root account has been disabled (I think it is stupid but that is just my opinion) You can get it back (kind of) by typing 

<snip>

in the command line. It will ask you to enter a new password twice and the root account is enabled. You then can type

su 

and enter the password to access it. 

If it is just a single or a few commands you can always sudo it if you do not need the root account.

I explained it better here:
[http://www.frankssite.com/hints.html](http://www.frankssite.com/hints.html)

---

### Post by fcomstoc on 2012-02-24
PM:

While we have nothing against you instructing someone to enable the root account, we ask that you also include a warning as to what can happen if a mistake is made while running as root. Also su no longer works as it used to in Ubuntu, it now works the way it does in other distribution where you have to enter a user name when using su. I have removed how to enable the root account from your post, and in the future when advising someone how to enable the root account, point them to the RootSudo ([https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)) wiki page instead.

Regards

cariboo907


So thats that.

---

### Post by dockalek on 2012-02-25
So, since I really don't need to create a root acccount to do anything more than scanning, I tried to run xsane as "gksudo xsane" and it tells me this:

(xsane:2750): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

What does it mean, and is there some more specific command that would be more successful in searching for the scanner?

Thank you

---

### Post by Lampi on 2012-02-25
Did you follow this wiki advice?

[https://help.ubuntu.com/community/ScanningHowTo#Permission_issues](https://help.ubuntu.com/community/ScanningHowTo#Permission_issues)

Maybe that's all you are missing, I had to add myself to the group as well when I installed my scanner.

---

### Post by dockalek on 2012-02-25
unfortunatelly not, it says saned is: 
The user `saned' is already a member of `scanner'.
the same with "lp" group.

---

### Post by dockalek on 2012-03-13
Well I read the advise there at [https://help.ubuntu.com/community/ScanningHowTo#Permission_issues](https://help.ubuntu.com/community/ScanningHowTo#Permission_issues)

But I don't know what he means by this ...and ls -al /dev/bus/usb/XXX/XXX to identify the group. I don&#7831; know what to put instead of the XXX's.

I sane-find-scanner and here is the result:

 # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04e8 [Samsung Electronics Co., Ltd.], product=0x343d [CLX-3180 Series]) at libusb:002:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

What shall I do next please? Does it say, that it is at port 002:002 so I should put it in the command where the X's are?

---

### Post by dandnsmith on 2012-03-13
Yes, that's obviously the thing to try first.

---

### Post by dockalek on 2012-05-08
I did, and tells me this:

georgi@georgi-Studio-1537:~$ ls -al /dev/bus/usb/002/005
crw-rw-rw- 1 root lp 189, 132 2012-05-08 12:23 /dev/bus/usb/002/005
georgi@georgi-Studio-1537:~$ 

What permission shall I add where now? Please. Thnxs.

---

### Post by smurphy on 2012-05-08
Why don't you use the provided tools of ubuntu ?

```

scanimage -f %d

```

will tell you hat scanner is installed.
All you have to do after, is to use the application to scan.

Newer version of ubuntu are creating the /dev directory on the fly at boot-up or when a device is plggued in -> udev - so whatever you will change there will only remain for your running session.

---

