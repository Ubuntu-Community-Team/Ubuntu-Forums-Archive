---
title: "a minor, annoying problem"
date: 2010-05-26
forum: General Help
---

### Post by sirwilliamrowanhamilton on 2010-05-26
hello.

whenever i right-click on a mounted usb drive, i have the option to "safely remove" it.  however, it i choose this option, I inevitably get the following error message:

-----
Unable to stop drive
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6)
SYNCHRONIZE CACHE: synchronize cache(10):  Fixed format, current;  Sense key: Key=9
 Additional sense: Logical unit not ready, cause not reportable
  Info fld=0x0 [0] 
FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: start stop unit: transport: Host_status=0x07 [DID_ERROR]
Driver_status=0x00 [DRIVER_OK, SUGGEST_OK]

FAILED: No such file or directory
-----

Well, I don't like this.  Is there any way to fix configure things so that this doesn't happen?  I'm currently using Lucid, but this happened on Karmic as well.  The way I see it, the result I would like would be either:

1.  the "safely remove drive" command just unmounts the drive (I can't imagine what else it does anyways, besides give me this stupid error)
2.  there is no "safely remove drive" option

I would be happy knowing how to do either, or both.

Thanks.

---

### Post by 2hot6ft2 on 2010-05-26
> **sirwilliamrowanhamilton said:**
> hello.

whenever i right-click on a mounted usb drive, i have the option to "safely remove" it.  however, it i choose this option, I inevitably get the following error message:

Hi sirwilliamrowanhamilton and welcome to the forum.

When you right click on it you create activity same as left clicking so it wont unmount. Instead go to Places > Home folder then on the left side you will see the drive with and eject icon next to it (see pic). Simply left click on the eject icon and it should unmount it without the error.
The unmount icon will disappear.

Naturally make sure it's not open and in use at the time.
:popcorn:

---

### Post by sirwilliamrowanhamilton on 2010-05-26
Yes, thank you 2hot6ft2.  However, I already know of various methods I can use to get the usb drive to unmount without showing me an error message.  That was not the issue I was getting at.  The issue was that there's this option there that inevitably will give me an error if chosen.  I just don't want that particular option to result in an error, or I want a way to avoid having the option at all.  I realize that it's more aesthetics than anything, but it seems silly to have an option that does this, and I don't want to run a silly system.  I seem to remember (though I could be wrong) having an "unmount" option instead on older versions of Ubuntu, and it always worked just fine.  
 
Basically, I just want to somehow edit the menu that gets displayed when you right-click on the usb drive icon on the desktop.  I don't even know how to look up information on this (I haven't yet found a set of words that will entice Google to point me in the relevant direction).  Hell, I don't even know if it's possible without, say, editing the code for some part of gnome directly, in which case it's way too much of a hassle to deal with.  But if there's a .conf file or something that I can edit, well, then I'd like to hear about it.

---

### Post by cariboo on 2010-05-27
I would suggest you check if there is a problem with the drive, how is it formatted? I looks like an unclean shutdown issue.

---

### Post by sirwilliamrowanhamilton on 2010-05-27
cariboo907, the usb drive is formatted as FAT32.  just now, i've tried reformatting it in windows (without the "quickformat" option) and that doesn't change anything.  for fun, i tried formatting the thing to ext3, and then to reiserfs, but still no change: i get the same error.

---

### Post by sirwilliamrowanhamilton on 2010-05-27
well, ok, i guess at this point, all i really want to know is what actually happens when you choose the 'safely remove drive' option.  i.e. what commands get executed.  

oh, and, for the record, it is metacity that i'm interacting with when i right-click on an icon "on the desktop", yes?

---

### Post by Claus7 on 2010-11-06
Hello,

I have exactly the same problem with a drive formatted as ext3. This drive failed me once, I recovered all my data, I formatted it again as ext3, I run disk integrity checks:
sudo e2fsck -C0 -p -f -v /dev/sdb1

and finally checked it with smart tool (Applications-> System Tools -> GSmartControl - installed from synaptic-).

Always I get the same error when trying unmount it from the Desktop, having full Desktop effects and 10.10 ubu. I do not face the same error message with other drives. 

The drive seem to be old, yet it passes the tests. I think that this message has to do with a too old drive. 

The option expressed here on how to unmount it works though, without producing any errors.

It is a maxtor 1TB usb external hdd.

Regards!

---

