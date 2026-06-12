---
title: "Crashed during update"
date: 2012-02-25
forum: General Help
---

### Post by ipin on 2012-02-25
Well, I have a kinda old notebook that was running Ubuntu 10.7 or 10.10 (I really don't remember). I didn't accessed it for a while then, last week, I decided to update it and, hopefully, boost my old computer. The problem is that, during the update, when the patches were being installed or something, the computer crashed. It was pretty normal for it to crash and I assumed that it was because the processor it's not very good and all. So, as I aways did, I turned the computer off by pressing the power button. Now the computer starts normally, but when it reaches the login screen, it gives me the regular login screen except for the users box. It has no user, only a box with the Ubuntu logo on it. And all I can do at this point is to turn off by pressing the power button, because, despite the regular appearance, nothing seems to work.
I have some important files on it, I don't mind if I have to install an OS all over again, but I really would like to have that files back. I tried to format it with Ubuntu and Windows 7, but both didn't showed me an option that could keep my old files. I think that it couldn't find them.

Any ideias how I can fix my computer and recover my files?

---

### Post by 2F4U on 2012-02-25
Did you try booting into a liveCD and then mount the harddrive to access those files?

---

### Post by philinux on 2012-02-25
> **ipin said:**
> Well, I have a kinda old notebook that was running Ubuntu 10.7 or 10.10 (I really don't remember). I didn't accessed it for a while then, last week, I decided to update it and, hopefully, boost my old computer. The problem is that, during the update, when the patches were being installed or something, the computer crashed. It was pretty normal for it to crash and I assumed that it was because the processor it's not very good and all. So, as I aways did, I turned the computer off by pressing the power button. Now the computer starts normally, but when it reaches the login screen, it gives me the regular login screen except for the users box. It has no user, only a box with the Ubuntu logo on it. And all I can do at this point is to turn off by pressing the power button, because, despite the regular appearance, nothing seems to work.
I have some important files on it, I don't mind if I have to install an OS all over again, but I really would like to have that files back. I tried to format it with Ubuntu and Windows 7, but both didn't showed me an option that could keep my old files. I think that it couldn't find them.

Any ideias how I can fix my computer and recover my files?

After the bios hit the shift key to get Grub menu. choose the second item down Recovery mode. Choose the root prompt with networking.

Use these commands one at a time.

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get upgrade

```

```
sudo reboot
```

---

### Post by ipin on 2012-02-25
> **2F4U said:**
> Did you try booting into a liveCD and then mount the harddrive to access those files?

Yes, it says it can't be mounted. I tried more than once, and one time a message appeared saying that they couldn't get a reply from it.


> **philinux said:**
> After the bios hit the shift key to get Grub menu. choose the second item down Recovery mode. Choose the root prompt with networking.

Use these commands one at a time.

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get upgrade

```

```
sudo reboot
```

Tried that. The first time I hit shift key it said that the Grub menu was being accessed on a black screen. But then the same login screen showed up. Now every time I try this it doesn't say anything and goes to the login screen either way.

---

### Post by ipin on 2012-02-25
> **philinux said:**
> After the bios hit the shift key to get Grub menu. choose the second item down Recovery mode. Choose the root prompt with networking.

Use these commands one at a time.

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get upgrade

```

```
sudo reboot
```

Somehow, I could finally manage it to work! I simply hit shift randonly till it worked. My system is working pretty well now. Thank you so much!

---

