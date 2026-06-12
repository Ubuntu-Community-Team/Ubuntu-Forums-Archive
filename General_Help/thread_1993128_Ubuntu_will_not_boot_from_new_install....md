---
title: "Ubuntu will not boot from new install..."
date: 2012-06-01
forum: General Help
---

### Post by biokuk on 2012-06-01
Sorry if I'm in the wrong place to ask this, but I am simply trying to install and run Ubuntu on a new PC. I install the latest version 12.?? and the previous 11.??. Both install apparently, but will not boot afterwards. I install XP and it runs no problem. 

Ubuntu works fine, without difficulty from live CD, but won't boot and run from a full install. I'm close to giving up here...
I'm no way fully PC savvy, but just really pxxxed off with Windows. I can't even search my install problem on this forum, for whatever reason.

Would really appreciate some basic advice here!

John.

---

### Post by pmheideman on 2012-06-01
What happens when you try to boot?  Does it say no OS installed or something like that?

---

### Post by biokuk on 2012-06-01
No. It definitely installs and tells me install is complete, then, when I try to re-boot/re-start it simply gives me a list of code which I do not understand, and freezes. I've now installed/re-installed two versions of Ubuntu, followed by one of XP Pro. Only the latter boots.

I bought another PC recently to use as a dedicated Ubuntu machine (instead of using a biggish partition on my usual PC) I'm sure the problem is something simple, but it mystifies me.

---

### Post by pmheideman on 2012-06-01
Any chance of getting some of that code?  I realize you can't copy and paste it, but get something like the first line of it?

---

### Post by oldfred on 2012-06-02
Do you get to a grub menu or if you hold shift down do you get grub menu? Or does grub> or grub rescue> come up?

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

If you get grub menu, it can be a video issue. What video card do you have? With nVidia you need nomodeset. Sometimes other parameters are needed, but usually you would need those on liveCD also.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

