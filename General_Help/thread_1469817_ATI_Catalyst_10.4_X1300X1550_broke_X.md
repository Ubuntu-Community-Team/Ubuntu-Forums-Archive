---
title: "ATI Catalyst 10.4 X1300/X1550 broke X?"
date: 2010-05-02
forum: General Help
---

### Post by leveliv on 2010-05-02
i am on 10.04 using an X1300 with 10.4 Catalyst.

But little did I know the drivers don't support my card. now I can't get back to default OSS drivers. I could reinstall but I don't want to, I like my system the way it looks now minus the driver problems.

I've tried reconfiguring Xorg but it just asks for my password and doesn't do anything. 

Also when I kill X my monitor just goes out of sync.

---

### Post by quadproc on 2010-05-02
> **leveliv said:**
> i am on 10.04 using an X1300 with 10.4 Catalyst.

But little did I know the drivers don't support my card. now I can't get back to default OSS drivers. I could reinstall but I don't want to, I like my system the way it looks now minus the driver problems.

I've tried reconfiguring Xorg but it just asks for my password and doesn't do anything. 

Also when I kill X my monitor just goes out of sync.
I am not sure of what you have tried, but if you edit the driver section section of the xorg.conf file to say driver "ati" then it should use the default open source driver.

If you don't have an xorg.conf file then you may need to create one.  It probably doesn't need very much in it; mine has 112 lines but about half of that is comments.

There is a fairly new capability in 10.04 called KMS.  I think that this may be causing a lot of trouble for a lot of people because it tries to pull many graphics functions into the kernel and I do not think that the capability has been debugged yet.  You may need to take some action to disable KMS.  This page may be useful: [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

You also may need to go to a previous driver version.  I am using 10.3 with Ubuntu 9.10 and that works well.  I don't know the dependencies of Ubuntu 10.04; if it requires the ATI 10.4 driver then you may have to revert to Ubuntu 9.10 until things get fixed.

quadproc

---

### Post by leveliv on 2010-05-02
hmm I was hoping I wouldn't have to write a new xorg.conf. Oh well I will do it. 

10.04 doesn't requuire 10.4 Driver. I just installed it to see what was up. I just want to revert back to normal. 

Thanks

---

