---
title: "Problem with Hibernation"
date: 2011-11-10
forum: General Help
---

### Post by marsgorski on 2011-11-10
Hi everyone. Ever since I upgraded to 10.10 about a week ago, my  hibernation feature is not working. The computer (Dell Inspiron 1545)  seems to go into hibernation without problems, but when I want to resume  a get an error message saying 
> The system snapshot could not be read.
This might be a result of booting a wrong kernel or typing in a wrong passphrase.

You can continue to boot the system and lose the saved state or reboot and try again.

[Notice that you may not mount any filesystem between now and successful resume That would badly damage affected filesystem.]

Do you want to continue boot (Y/n)?                      I answer yes to the question and Ubuntu boots up, without the windows I left open when I hibernated.

I saw some posts from people with similar problems ([here]("http://ubuntuforums.org/showthread.php?t=1712372"), and [here]("http://ircanswers.com/ubuntu/561269/snapshot-eventually-continue-nothing-guessing")),  but the difference is that they are not able to boot into Ubuntu at  all, even if they answer "yes" to continue booting, while I am able to.

Any help will be much appreciated.

---

### Post by marsgorski on 2011-11-11
I just realized something that probably explains the hibernation problem: When booting up, after the GRUB menu loads, my 3 options appear to be "ubuntu 11.04 kernel 2.6.38-8 generic" "Windows" and "memtest"

Notice ubuntu 11.10 doesn't appear, and the kernel version is not the most current one (i believe it is 3.X?). This must have been caused by the problem I encountered during the upgrade from 11.04 to 11.10 that I described in my first post.

I guess I have a bigger problem, and the hibernation problem is really just a "symptom". Should I create a new thread regarding the kernel problem? Please help!

---

### Post by marsgorski on 2011-11-12
I was able to solve this problem by installing the newest Linux kernel, per [these steps]("http://ubuntuforums.org/showthread.php?t=1872537&highlight=upgrade+kernel"), which for some reason did not install during the upgrade to 11.10.

---

