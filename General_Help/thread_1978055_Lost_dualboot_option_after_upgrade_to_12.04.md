---
title: "Lost dualboot option after upgrade to 12.04"
date: 2012-05-11
forum: General Help
---

### Post by GijsWillem on 2012-05-11
Hello forum,
Hope there is some one out there who can help me.
The issue: After upgrading to 12.04 I have lost my dualboot manager.
BTW I had a similar issue when upgrading to version 11.10. This post gives the details: [http://ubuntuforums.org/showthread.php?t=1930252](http://ubuntuforums.org/showthread.php?t=1930252)

However now after my upgrade to 12.04 I again don't have any OS choice. It just boots up in 12.04
Attached the output file from the bootinfoscript program I ran after the 12.04 installation.
Looking forward to hearing your suggestions.

---

### Post by howefield on 2012-05-11
Thread moved to the "*General Help*" forum.

---

### Post by ahso4271 on 2012-05-11
Hi
If you have multiple discs you might need to change the boot order. 
Otherways I suggest you simply update Grub. Google finds some tutorials for that.

---

### Post by wilee-nilee on 2012-05-11
In both ubuntu installs run this. First in the 10.04

```
sudo update-grub
```

---

### Post by GijsWillem on 2012-05-11
Hello Wilee-Nilee

You suggest to 1st run the sudo update-grub in the 10.04.
However my boot manager with 11.10 did allow me to select older versions. However under 12.04 I can't get to any older Ubuntu images.

You still recomment to run the upgrade-grub but directly in 12.04 or do you have another suggestion?


Thanks for all the help so far!

---

### Post by wilee-nilee on 2012-05-11
> **GijsWillem said:**
> Hello Wilee-Nilee

You suggest to 1st run the sudo update-grub in the 10.04.
However my boot manager with 11.10 did allow me to select older versions. However under 12.04 I can't get to any older Ubuntu images.

You still recomment to run the upgrade-grub but directly in 12.04 or do you have another suggestion?


Thanks for all the help so far!

So you have not run the update grub in the 12.04?

That is actually the OS that is controlling the grub boot, so if you have not, go ahead and do it.

Do you still have the startup manager installed, it is not compatible anymore, it wont follow a upgrade of the kernels, it needs to be removed before you run the update-grub in the 12.04.

When you run this command a app called os-prober looks for other operating systems and if found puts them in the grub menu.

---

### Post by GijsWillem on 2012-05-21
Hello,
under 12.04 I did run the grubupdate and it looks like it finds all the various OS on my system.
However after rebooting the system I would expect it to come up with a menu allowing me to chose the OS I want to run. Unfortunately it shows nothing and just comes up with 12.04.
Any suggestions on how I get this menu back before the OS loads?

Thanks
Gijs

---

### Post by GijsWillem on 2012-05-22
Hello forum,
slowly understanding it a little bit better. Eventually I did manage to locate the menu.lst file which indeed does exist. However in the menu.lst file the hiddenmenu command is active and clearly that way I will not see any screen nor have any choices at boot up.
Now I tried to add the # in front of this command but I have issues saving this file. The system tells me that I don't have the permissions necessary to save the file. Guess that this it pretty basic Linux stuff but not being too savvy here I would appreciate some help. 
As always many thanks for the help :)
Gijs

---

### Post by GijsWillem on 2012-05-22
Good, figured out how to log on as root and did manage to make the change in the menu.lst file in the \boot\grub\ directory. The change is adding a # in front of the hiddenmenu line, effectively disabling this command.
Now I hoped that after a boot-up I would be presented a choice menu but unfortunately the system just boots up in 12.04.
Bottom line I am somewhat stuck. Anyone out there who can give me some suggestions on how to fix this one?
Thanks,

Gijs     :sad:

---

### Post by GijsWillem on 2012-05-28
Issue solved.
Just reinstalled GRUB and changed the menu.lst file accordingly
Gijs

---

