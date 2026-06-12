---
title: "Full Grub after reinstalling 9.04 next to XP"
date: 2009-07-25
forum: General Help
---

### Post by jlesseig on 2009-07-25
After battling the HAL.DLL issue with XP, I decided to enlarge my partition for 9.04 and reinstall.

The first installation next to XP asked for only XP or Ubuntu.

With this reinstall with bigger partition, everything is running great except...

When Grub launches it has multiple Ubuntu entries and defaults to something other than XP which is not good as far as household harmony goes....

I have searched through these forums but confess much of it is a bit confusing as I have just caught the Ubuntu bug.

Ideally I would like to have only two options when booting - XP first and Ubuntu second - so my family can continue to use what they prefer.

Thanks in advance!

---

### Post by merlinus on 2009-07-25
The multiple ubuntu options are for different kernels, if you look closely.

A good solution might be to install startup-manager, which is a gui that will allow you to select which os is the default, etc.  You can do this via Applications/Add/Remove.

---

### Post by synapsys on 2009-07-25
> **merlinus said:**
> The multiple ubuntu options are for different kernels, if you look closely.

A good solution might be to install startup-manager, which is a gui that will allow you to select which os is the default, etc.  You can do this via Applications/Add/Remove.

In startup-manager you can remove the other ubuntu entries and make windows the default so that your family will be less confused.

---

### Post by jlesseig on 2009-07-26
Thank you both for the advice. Worked great.

Now I have to figure out how to get rid of the second OS selection screen I believe may have been created when 9.04 was installed "within Windows". 

When the second screen comes up, I have the XP or Ubuntu choices. XP loads just fine, however, Ubuntu throws the HAL.DLL error I thought I had fixed. 

Off to do more research unless anyone has advice for me.

Thanks again for the help! :D

---

