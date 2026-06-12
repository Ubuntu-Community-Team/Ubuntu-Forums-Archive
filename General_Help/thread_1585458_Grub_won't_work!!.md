---
title: "Grub won't work!!"
date: 2010-09-30
forum: General Help
---

### Post by SeamusC on 2010-09-30
I have Windows 7 and Ubuntu 10.04 on my laptop and I have a grub to choose which OS to use when it boots up. When I click on the Ubuntu option the grub normally gives me more detailed options like recovery mode or normal mode etc but now when i click on Ubuntu its changed. I can still get on to Windows though and it works fine. The grub stopped working after i downloaded the updates from the update manager on Ubuntu today. The screen that comes up looks like this,

[B]GNU GRUB version 1.98-1ubuntu7

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions

grub>[/B]

When I press TAB to look at the possible commands it says

[B]Possible commands are:
. [ badram boot cat chainloader clear configfile cpuid dump echo exit export halt help initrd insmod linux list_env load_env loopback ls lsmod normal normal_exit parser.grub parser.rescue reboot rmmod root save_env search search.file search.fs_label search.fs_uuid  set sleep source terminal_input terminal_output test unset[/B]

Please help! I don't want to lose all my files on Ubuntu!

---

### Post by andrewthomas on 2010-09-30
Read this:

[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)

---

### Post by oldfred on 2010-09-30
Because you mention a first menu then a second it sounds like wubi. Wubi has separate issues but is a full install in a file within the windows NTFS partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You can run this to see your entire configuration. But with wubi we may not be able to see the exact issue.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by EdCole on 2010-10-02
I have problems with my Wubi after every upgrade; see [http://ubuntuforums.org/showthread.php?t=1540062](http://ubuntuforums.org/showthread.php?t=1540062) for the gory details (the final resolution is on page 2).  There was a bug in the version of WUBI that I installed, so it won't load the latest version of the Linux kernel; I have to start the older version.  Here's what I do to boot it up, which might or might not work for you.

```

root (loop0) 
linux /boot/vmlinuz-2.6.31-14-generic \
    root=/dev/sda1 loop=/ubuntu/disks/root.disk ro 
initrd /boot/initrd-2.6.31-14-generic 
boot

```(The \ at the end of the line allows me to split the command over two lines.)

 Check my original thread to for more information.  I hope this helps you.

Ed.

---

