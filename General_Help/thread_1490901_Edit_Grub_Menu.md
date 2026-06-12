---
title: "Edit Grub Menu"
date: 2010-05-22
forum: General Help
---

### Post by Gixxer420 on 2010-05-22
Hello,

I'm trying to edit the grub menu loader, a client of mine has many old OS entries that he'd like me to remove. I'm familiar doing this on other versions of Linux, but I think he may have a different grub version that I'm not familiar with because he's missing the menu list.

I'd like to remove everything except the 1st (Ubuntu 10.04) and 7th (Windows Vista) entries, how would I accomplish this? I've attached a link to an image.

Thank you.

[http://img156.imageshack.us/img156/5383/img6914x.jpg](http://img156.imageshack.us/img156/5383/img6914x.jpg)

---

### Post by efflandt on 2010-05-22
The correct way to remove old kernels from the grub2 menu is to remove the old kernels and related files "from the system".  Then update-grub will no longer find them.

For example in Synaptic Quick search "linux", and uninstall any earlier kernels and headers other than the current one and the one before that.

See /etc/default/grub and the files in /etc/grub.d for customization.

---

### Post by drs305 on 2010-05-22
You can remove recovery mode entries, if desired, by uncommenting (removing the # symbol) the following line in /etc/default/grub:
> **#**GRUB_DISABLE_LINUX_RECOVERY="true"
You can disable the memtest86+ entries by making the script unexecutable via a file browser or this command
```
sudo chmod -x /etc/grub.d/20_memtest86+
```
Then in a terminal, run:
```
sudo update-grub
```

Those are the major and simple changes. After that it takes a bit more work....

You could play with the scripts in /etc/grub.d and alter them so particular partitions were skipped. See the Title Tweaks link in my signature.

The easiest thing to do would be to just make a custom menu and put exactly what you want in it. Here is a good link for that:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")

Grub 2 is quite different than Grub legacy. To learn more, check out the links in my signature line.

---

### Post by Gixxer420 on 2010-05-22
> **efflandt said:**
> The correct way to remove old kernels from the grub2 menu is to remove the old kernels and related files "from the system".  Then update-grub will no longer find them.

For example in Synaptic Quick search "linux", and uninstall any earlier kernels and headers other than the current one and the one before that.

See /etc/default/grub and the files in /etc/grub.d for customization.

$ dpkg --list 'linux-image*' 
To see the kernels

$ sudo apt-get remove linux-image-xx.xx.xx-xx-generic
Is this the appropriate way to remove said kernels?

> **drs305 said:**
> You can remove recovery mode entries, if desired, by uncommenting (removing the # symbol) the following line in /etc/default/grub:

You can disable the memtest86+ entries by making the script unexecutable via a file browser or this command
```
sudo chmod -x /etc/grub.d/20_memtest86+
```
Then in a terminal, run:
```
sudo update-grub
```



Perfect, thank you that's exactly what I needed.

---

### Post by Gixxer420 on 2010-05-24
I have one last question since I have everything working exactly as I want it. Is there a way to make Vista load first by default? After 10 seconds Ubuntu loads every time, my client would prefer it the other way around.

Thanks.

---

### Post by drs305 on 2010-05-24
> **Gixxer420 said:**
> I have one last question since I have everything working exactly as I want it. Is there a way to make Vista load first by default? After 10 seconds Ubuntu loads every time, my client would prefer it the other way around.

Thanks.

You set the default with this line in /etc/default/grub:
```
GRUB_DEFAULT=0
```
The next time you boot, find out the number of the item you want to boot (or count the number of 'menuentry' lines in /boot/grub/grub.cfg). Start counting with 0.

If Windows is the third menu item, set the default as "GRUB_DEFAULT=2". The run "sudo update-grub".

You can also set it with startupmanager, a GUI app you can install.

---

