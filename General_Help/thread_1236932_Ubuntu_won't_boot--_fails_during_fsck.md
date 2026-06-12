---
title: "Ubuntu won't boot-- fails during fsck"
date: 2009-08-10
forum: General Help
---

### Post by Volt9000 on 2009-08-10
Had a major power outage yesterday, and now when I turn my computer on, Ubuntu won't boot properly. I can get to the boot menu and the logo and progress bar appear, but as the progress bar is going it says I have to do a mandatory file system check. So I let it run, and when it gets to about 4% I get dumped into a terminal telling me "fsck died with an exit status of 4." There's a bunch of more text about how fsck must be invoked manually and some more details about fsck which unfortunately I don't know how to capture to a file.

I have no idea what to do next. I doubt invoking fsck manually would do any good since my hard drive is mounted as read-only. Why, I have no idea.

I've posted here my outputs of dmesg, df, fdisk and my fstab file. I hope someone can help!
For the record, sdb is my primary hard drive, sda is my secondary, and sdc is the USB stick I inserted to copy over the file and program outputs.

I have another Ubuntu machine which seems to start up fine. No idea why this problem is plaguing my primary machine. The only thing I can think of is that I was in the middle of a very large download when the power outage happened.

---

### Post by merlinus on 2009-08-10
When it drops you to a cli, try

```
sudo fsck -y /dev/sdx
```

where x is the hdd to check (e.g. sdb).

You also might try unplugging the usb stick before booting.

---

### Post by Volt9000 on 2009-08-10
I fixed it! Thanks to the friendly fellows in #ubuntu on irc.freenode.net and directed me to this thread: [http://ubuntuforums.org/showthread.php?t=367644](http://ubuntuforums.org/showthread.php?t=367644)

Thanks, though. :)

---

