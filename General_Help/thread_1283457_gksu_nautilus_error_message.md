---
title: "gksu nautilus error message"
date: 2009-10-05
forum: General Help
---

### Post by knomaly on 2009-10-05
*Running Ubuntu 9.04 on laptop
*All software updated

*Open Gnome Terminal 2.26.0
*Type "gksu nautilus" cmd at shell prompt
*Result is as follows (excluding dashes to define terminal text):

------------------------------------------------------------------------------------------------
xyz@xyz-laptop:~$ gksu nautilus
Sense key: 0xf0 0x00 0x05 0x00 0x00 0x00 0x00 0x0b 0x00 0x00 0x00 0x00 0x20 0x03 0x00 0x00 0x00 0x00 0x00 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directoryPlease ask your system administrator to enable user sharing.

led: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
** (nautilus:5847): WARNING **: Unable to add monitor: Operation not supported
--------------------------------------------------------------------------------------------------

*Any ideas what may be happening, and how to effectively resolve this issue? Note: this error message is reproducible on several other machines I have running Ubuntu 9.04.

---

### Post by kanikilu on 2009-10-05
There are some proposed fixes/workarounds to this problem in this bug report: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211966](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/211966)

---

### Post by knomaly on 2009-10-05
Thanks for your response kanikilu. . .

I was hoping to change the "File access" permissions on an external HDD that I formatted to the ext3 filesystem with GParted, without having to use the cmd line. This has been accomplished in the past after executing the "gksu nautilus" cmd at the shell prompt. What I presently find, is that apparently because of a bug, "File access" permissions for a newly-formatted external drive can only be changed using shell commands, rather than through Nautilus with elevated permissions. Is this indeed true?

If it is true, then could you or someone else provide the necessary cmds, as well as one or more working examples, explaining how to establish permissions for an external usb drive so that it can be used as a backup medium* for one or more accounts residing on several computers running Ubuntu?

For instance, at the device level, is there a generic designation for u, g, and o**? How are folder and file access permissions best handled for the external device to permit maximum backup flexibility?

*backup medium: to support the copy and paste operations, or backup utilities like tar, simple backup, rsync, etc.
 **generic designation for u, g, and o: perhaps &#8220;backup&#8221;? That's an option for the Owner and Group settings under the Permissions tab of the device Properties dialog box for an elevated Nautilus.

---

### Post by knomaly on 2009-10-07
[SIZE=1]The following search results from various sources listed below provide answers to some of the questions raised above, but not necessarily in a concise, coherent or authoritative way. Hence, one might qualify this exercise as an approach to revealing the truth, with a few scraps thrown in. . .[/SIZE]

[SIZE=1]Ubuntu Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)[/SIZE]
[SIZE=2][SIZE=1]UD search results: 
[/SIZE][/SIZE]
[SIZE=2][SIZE=1]FilePermissions: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)[/SIZE][/SIZE]
[SIZE=2][SIZE=1]RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)[/SIZE][/SIZE]
[SIZE=1]Mount: [https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)[/SIZE]
[SIZE=1]MountUSB: [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)[/SIZE]

[SIZE=1]--------------------------------------------------------------------------------------------------[/SIZE]

[SIZE=2][SIZE=1]Wikipedia search results: [/SIZE][/SIZE]
[SIZE=2][SIZE=1]chmod: [http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)[/SIZE][/SIZE]

-------------------------------------------------------------------------------------------------

                                      [SIZE=1]Google search results: [/SIZE]
   [SIZE=1]ubuntu 9.04: usb drive file permissions[/SIZE]

    &#8220;[SIZE=1]Cannot access USB drive in Ubuntu&#8221;[/SIZE]
 [[SIZE=1]http://ubuntuforums.org/showthread.php?p=8066785[/SIZE]]("http://ubuntuforums.org/showthread.php?p=8066785")

    &#8220;[SIZE=1]change permissions on ext3 external hard drive&#8221;[/SIZE]
[SIZE=2][SIZE=1]http://wwww.ubuntuforums.org/showthread.php?t=1277062[/SIZE][/SIZE]

[SIZE=1]--------------------------------------------------------------------------------------------------[/SIZE]

[SIZE=1]Google search results: [/SIZE]
[SIZE=1]ubuntu: How to change external drive file permissions[/SIZE]

 &#8220;[SIZE=1]External drive will not give permission to write or read&#8221;[/SIZE]
 [[SIZE=1]http://ubuntuforums.org/showthread.php?t=705432[/SIZE]]("http://ubuntuforums.org/showthread.php?t=705432")

 &#8220;[SIZE=1]D[/SIZE][SIZE=1]rive Permissions for Opensuse/Ubuntu&#8221;[/SIZE]
 [[SIZE=1]http://www.linuxquestions.org/questions/linux-hardware-18/drive-permissions-for-opensuseubuntu-658591/[/SIZE]]("http://www.linuxquestions.org/questions/linux-hardware-18/drive-permissions-for-opensuseubuntu-658591/")

    &#8220;[SIZE=1]Re: change permissions on ext3 external hard drive&#8221;[/SIZE]
 [[SIZE=1]http://wwww.ubuntuforums.org/showthread.php?p=8025786[/SIZE]]("http://wwww.ubuntuforums.org/showthread.php?p=8025786")

    &#8220;[SIZE=1]Changing drive Permissions in Ubuntu Linux?&#8221;[/SIZE]
 [SIZE=1][make OSX/hfsplus drive readable on ubuntu][/SIZE]
 [[SIZE=1]http://answers.yahoo.com/question/index?qid=20081105191611AAxfNpy[/SIZE]]("http://answers.yahoo.com/question/index?qid=20081105191611AAxfNpy")

    &#8220;[SIZE=1]Trouble changing permissions on external HDD&#8221;[/SIZE]
 [[SIZE=1]http://art.ubuntuforums.org/showthread.php?p=7930039[/SIZE]]("http://art.ubuntuforums.org/showthread.php?p=7930039")

    [SIZE=1]-------------------------------------------------------------------------------------------------[/SIZE]

[SIZE=1]Ubuntu Technical Answers System (UTAS): [https://answers.launchpad.net/ubuntu](https://answers.launchpad.net/ubuntu)
UTAS search results: [/SIZE]
[SIZE=1]file permissions[/SIZE]
[SIZE=1]
&#8220;Need help using sudo to edit file permissions.&#8221;[/SIZE]
[SIZE=1][intro to globbing: [http://en.wikipedia.org/wiki/Glob_(programming)]("http://en.wikipedia.org/wiki/Glob_%28programming%29%5D")[/SIZE]
[SIZE=2][[SIZE=1]https://answers.launchpad.net/ubuntu/+question/25111[/SIZE]]("https://answers.launchpad.net/ubuntu/+question/25111")[/SIZE]

[SIZE=1]"How do I change permissions. I cannot copy files to my USB stick because it says you do not have permission as you are not root."[/SIZE]
[SIZE=2][SIZE=1][chmod octal numeric code generator/calculator]
[https://answers.launchpad.net/ubuntu/+question/14751](https://answers.launchpad.net/ubuntu/+question/14751)[/SIZE][/SIZE]
                       
[SIZE=1]File Permissions: Trash: cannot empty/delete files in[/SIZE]
 &#8220;[SIZE=1]How do I force the trash to empty?&#8221;:[/SIZE]
[SIZE=1]https://answers.launchpad.net/ubuntu/+question/55632[/SIZE]
       
   [SIZE=1]"Unable to change permissions&#8221;[/SIZE]
[SIZE=2][[SIZE=1]https://answers.launchpad.net/ubuntu/+question/61106[/SIZE]]("https://answers.launchpad.net/ubuntu/+question/61106")[/SIZE]

---

