---
title: "Lost access to ubuntu."
date: 2011-09-02
forum: General Help
---

### Post by creata.physics on 2011-09-02
Okay, so I ran into a huge problem the other day and I'm not sure what to do.

I was running ubuntu 11.04 along with windows xp pro, well the other day I messed up some main dll files in windows and had to reformat it.  Windows had two partitions, one had the install on it, the other stored misc data.  Well, I wanted to merge those two partitions, so when I was getting ready to install Windows, I firstly deleted those two partitions, and thought I'd be able to boot into ubuntu to either delete both partitions, and create a new one, or merge them together.

Well, it turns out I was horribly wrong about being able to delete the windows partition and then boot into ubuntu to do the mentioned tasks.  After deleting the partitions( well, erasing them actually as there are still two NTFS partitions ) I rebooted, I had gotten a black screen that said:

F1 to retry reboot or F2 for system setup

So I figured I was screwed.  What I did was just not worry about it, install Windows XP Pro, and I figured once that was done I'd be able to have the option of which OS I could boot into, like how it was previously after installing Ubuntu alongside windows.

Anyways, that's how I got to the problem I'm currently battling, I have Windows XP Pro installed along with my same old Ubuntu 11.04, I just don't know what I can do to get the OS chooser menu  like I had before after first installing Ubuntu.  Please keep in mind that my problem is that I have **no** choice of choosing which OS I can boot into at start up, It just automatically loads Windows.

Thanks in advance
/Matt

---

### Post by vaslat29 on 2011-09-02
I could not easily find a way to post my queries here so I have used this reply option to post it.

When I use the wubi tool to install, I note that it only downloads 64bit - but I need the 32 bit.

---

### Post by creata.physics on 2011-09-02
I'm sorry, but what does this have to do with my issue?

---

### Post by claracc on 2011-09-02
I think you have to reinstall the grub loader in order to select which os tou are going to run (xp or ubuntu), since after installing xp only win loader is present.

You can follow the steps indicated in this link: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5), special attention to step 5 : restoring grub loader.

Also, there is very good information about recovering grub loader in this link:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by creata.physics on 2011-09-03
Thanks. 

Ended up having to insert the 11.04 cd, and do an "upgrade" which re-installed grub and I only lost about 2 or 3 programs, so no big deal with that.

Thanks a bunch, a mod can go ahead and change the topic prefix to SOLVED.

---

### Post by claracc on 2011-09-03
You are welcome. I am glad you have solved the problem.

Only you can mark the thread as solved ( I think with thread tools), as you are the "owner" of the thread.

---

