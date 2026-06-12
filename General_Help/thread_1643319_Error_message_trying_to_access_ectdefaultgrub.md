---
title: "Error message trying to access /ect/default/grub"
date: 2010-12-11
forum: General Help
---

### Post by markcoronado on 2010-12-11
I just updated to 10.04 LTS & I would like to edit my grub menu to get rid of the unneeded entries.

When I enter /etc/default/grub into terminal It gives me bash: /etc/default/grub: Permission denied.

From what I have read I just need to put # in front of what I don't want to see in the menu, but I'm unable to access the file to make the changes.

How do I go about doing this?
I would also like to make a backup of the file first before editing it.

---

### Post by drs305 on 2010-12-11
You have to use admin/root privileges since it's a system file. You will be asked for a password. Enter your password. In a terminal command, you won't see your password as you type. 

The first command will make a copy. The second will open it for editing.
```

sudo cp /etc/default/grub /etc/default/grub.bak
gksu gedit /etc/default/grub
```

Here is a link explaining root & sudo:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Krytarik on 2010-12-11
You should also read this, about how to disable menu entries in the boot menu:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Because, even if you delete the entries manually (in /boot/grub/grub.cfg, not /etc/default/grub), the next time there is a kernel update the grub.cfg gets recompiled and all entries are there again!;)

---

### Post by markcoronado on 2010-12-12
Thanks for all the help drs305 & Krytarik.

I managed to delete the old 2.6.31-14 & that got rid of that from the grub along with the memery test from showing.

I would like to change the wording on my windows 7 & windows recovery partitions but after reading about creating a custom menu I'm kind of lost.
I can't even find the /etc/grub.d/40 custom file.

I'm not used to all the Linux terms & where to find things like directory.

Are there any directions written for Linux dummies?

---

### Post by Quackers on 2010-12-12
Take a look at the link below by drs305. It's not easy, but nothing worthwhile is :-)

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Krytarik on 2010-12-12
> **markcoronado said:**
> Thanks for all the help drs305 & Krytarik.

I managed to delete the old 2.6.31-14 & that got rid of that from the grub along with the memery test from showing.

I would like to change the wording on my windows 7 & windows recovery partitions but after reading about creating a custom menu I'm kind of lost.
I can't even find the /etc/grub.d/40 custom file.

I'm not used to all the Linux terms & where to find things like directory.

Are there any directions written for Linux dummies?
Did you only delete the entries in the file /boot/grub/grub.cfg or removed them according to the description I posted?

The memtest-entries can be removed by disabling the execute-permission of the respective file (20_memtest86+) in the directory /etc/grub.d .
There should also be the file 40_custom .

If there are entries in the boot menu of older kernels, which you don't use anymore, you should remove the respective packages via Synaptic, per kernel it frees ca. 180 MB!
Search for the version number, there are always three packages per kernel:
- linux-image-VERSION-generic
- linux-headers-VERSION-generic
- linux-headers-VERSION

---

### Post by markcoronado on 2010-12-13
> **Quackers said:**
> Take a look at the link below by drs305. It's not easy, but nothing worthwhile is :-)

[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

I did look at the tweaks & that is how I figured out how to do what I managed to do, but I just have a hard time trying to understand it all.
I guess I'm to used to windows.
Thanks.

---

### Post by drs305 on 2010-12-13
> **markcoronado said:**
> I did look at the tweaks & that is how I figured out how to do what I managed to do, but I just have a hard time trying to understand it all.
I guess I'm to used to windows.
Thanks.

I completely understand.

I did help out someone trying to change the Windows title in a couple of recent posts in this thread that may help you as well:
[http://ubuntuforums.org/showthread.php?t=1643927]("http://ubuntuforums.org/showthread.php?t=1643927")

---

### Post by markcoronado on 2010-12-13
> **Krytarik said:**
> Did you only delete the entries in the file /boot/grub/grub.cfg or removed them according to the description I posted?

The memtest-entries can be removed by disabling the execute-permission of the respective file (20_memtest86+) in the directory /etc/grub.d .
There should also be the file 40_custom .

If there are entries in the boot menu of older kernels, which you don't use anymore, you should remove the respective packages via Synaptic, per kernel it frees ca. 180 MB!
Search for the version number, there are always three packages per kernel:
- linux-image-VERSION-generic
- linux-headers-VERSION-generic
- linux-headers-VERSION

OK here's what I did.
For the old kernel I remover it via Synaptic.
For the memory test I entered this in terminal  sudo chmod -x /etc/grub.d/20_memtest86+

I'm happy with what is left on the menu screen but I would like to maybe change the order they are in & some of the wording, so I think that would be a custom menu.
All I have to do is figure out how to do it without screwing things up.

I think I made a backup of the /etc/default/grub file but I don't know where to find it.
I need to learn where everything is in Ubuntu.

---

### Post by markcoronado on 2010-12-16
I want to thank everyone for their help.
This thread by Cavsfan [http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338) was a big help.
I finally edited my Grub 2 menu & got rid of all of my unwanted entries & am now left with my custom menu with a lot less clutter.

I have one question.
Is it possible to reverse the order of my menu entries.
I followed Cavsfan's instructions & Ubuntu is first on the list & Windows 7 is 2nd.
Can I just reverse the order they are in by putting the Windows 7 entry first in the 06 custom file?

---

### Post by Krytarik on 2010-12-16
> **markcoronado said:**
> I want to thank everyone for their help.
This thread by Cavsfan [http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338) was a big help.
I finally edited my Grub 2 menu & got rid of all of my unwanted entries & am now left with my custom menu with a lot less clutter.

I have one question.
Is it possible to reverse the order of my menu entries.
I followed Cavsfan's instructions & Ubuntu is first on the list & Windows 7 is 2nd.
Can I just reverse the order they are in by putting the Windows 7 entry first in the 06 custom file?
You may try, I don't see how the order of the menu entries could have a negative side-effect.

---

