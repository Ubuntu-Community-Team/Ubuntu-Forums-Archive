---
title: "Can I install Ubuntu over the top of Ubuntu?"
date: 2010-06-24
forum: General Help
---

### Post by Vampyer on 2010-06-24
Hey guys,

To cut a long story short, I messed up an install of Ubuntu (tis all part of the learning process) and I was wondering if I could install a fresh copy over the top of the old one?

Would it remove everything like themes, programs and drivers and stuff?

thanks

---

### Post by howefield on 2010-06-24
Yes, and yes.

Do you have something more specific to ask ?

---

### Post by Vampyer on 2010-06-24
No, thank you :)

I just wanted to have a fresh start and the best way to do that is from the beginning :)

Thanks again

---

### Post by VH-BIL on 2010-06-24
You can try and repair the old one.

---

### Post by DarkHellBird on 2010-06-24
If you choose not to format your partition in the installation process then your desktop will remain exactly as you have it right now.

Only the filesystem will be overwritten with the new install, btw, VH-BIL has a good point.

---

### Post by Vampyer on 2010-06-24
Well, I don't have anything important on it (nothing that can't be replaced) so either way it's all good :)

I just figured a fresh install would be better to remove some unwanted drivers, mainly ndiswrapper

---

### Post by VH-BIL on 2010-06-24
You will learn more and be able to solve issues (and other peoples in forums) by trying to repair it first.

---

### Post by Vampyer on 2010-06-24
ok cool, how would I go about a repair then? There's probably a HOWTO in the forum somehere... I'll have a look

---

### Post by VH-BIL on 2010-06-24
What is the problem with your Ubuntu install?

---

### Post by Vampyer on 2010-06-24
I want to remove ndiswrapper but I can't remember where I installed it :/

Careless, I know :P

I've looked around and lots of people are saying that there is no 'easy' way to remove ndiswrapper and you need to do lots of stuff to completely remove it. So I thought a complete reinstall of Ubuntu (8.10) would do the trick nicely and make my life a little easier :P

---

### Post by VH-BIL on 2010-06-24
Check in Synaptic (System > Administration > Synaptic Package Manager). Search for ndiswrapper then right click and select remove.

---

### Post by Vampyer on 2010-06-24
I think I've done it :D

```
 sudo ndiswrapper 
```

then

```
sudo ndiswrapper -l
```

then 

```
sudo ndiswrapper -r then type the driver name
```

I don't know for sure though, will test it tomorrow as it's getting late :)

---

### Post by VH-BIL on 2010-06-24
SO you wanted to remove a driver installed by ndiswrapper and not ndiswrapper itself. I hope it worked :)

---

### Post by Vampyer on 2010-06-24
I want to get the madwifi drivers working and I think ndiwrapper is conflicting with it. Even if it's not, there's no point having two sets of drivers :P

---

### Post by VH-BIL on 2010-06-24
If madwifi is not installed via ndiswrapper then you can uninstall that too.

---

### Post by Vampyer on 2010-06-24
I wouldn't know, I've tried to install them but they don't seem to be working :(

---

### Post by VH-BIL on 2010-06-24
Once you have uninstalled what you want to uninstall you can check out this thread [_*Howto Install Madwifi for Atheros in Lucid*_]("http://ubuntuforums.org/showthread.php?t=1484242")

---

### Post by dcstar on 2010-06-25
> **Vampyer said:**
> Hey guys,

To cut a long story short, I messed up an install of Ubuntu (tis all part of the learning process) and I was wondering if I could install a fresh copy over the top of the old one?

Would it remove everything like themes, programs and drivers and stuff?

thanks

If you have a separate /home partition all your user data will be preserved no matter how many installs you do.

---

