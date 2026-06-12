---
title: "Problem with usplash, system won't boot"
date: 2010-02-23
forum: General Help
---

### Post by chevelleman71 on 2010-02-23
I switched by usplash theme to a new one then back to the standard ubuntu theme then restarted, everything was fine. Later I hibernated my machine, then when I tried to power it back on I was presented with a blank/black screen.

Now when I try to reboot in normal mode all I get is a black screen with flashing underscore. I can't type anything. When I do ctrl + alt + f2 this is what I see:

usplash: No usable theme found for 1280 x 1024
screen init failed

-- that's it, it just stops there.

When I try to reboot in recovery mode it does the same thing, except different data comes up when it do ctrl+alt+f2. Here's a picture of it: [**http://tinyurl.com/yfpsub7**]("http://tinyurl.com/yfpsub7")
At that point it just stops.

Basically can't even get to a console prompt, if I could I'm sure I could just change the resolution setting in grub since that's seems to be the problem. How can I get to console?

Can anyone help? I'm a life-long windows user that's moving over to linux (love it) but I'm still learning.

Thanks
-Luke

---

### Post by tom4everitt on 2010-02-23
There is one way that always work: boot from live cd. Then you get your console in a working system, you can mount the file system with the faulty menu.lst/grub.cfg, edit it and reboot :)

Its a very useful trick actually. Good luck!

---

### Post by chevelleman71 on 2010-02-23
Tom,

Ah, that's great,  i didnt think I could access the filesystem from the live cd. Great to know! Thanks!

I guess that brings me to another question, does it look like from the output on the screen that all I need to do is change the resolution setting grub? My usplash theme is the default ubuntu one that comes with Karmic, so I'm guessing I should set it to 1024 x 768?

Luke

---

### Post by tom4everitt on 2010-02-23
That is a lot harder question ;) I would say: Try it! But make a backup of the original settings first (just common sense really...)! 

If nothing else you'll get a new error :)

---

### Post by chevelleman71 on 2010-02-23
Thanks, I'll do that. Quick question (I'm obviously a newbie) - how do I backup my settings (via console)?

Thanks! This forum is awesome.

Luke

---

### Post by tom4everitt on 2010-02-23
Say you want to do a backup of /boot/grub/menu.lst

A backup is simply a backup, so what you do is:

cd /boot/grub  # Go to the directory
cp menu.lst menu.lst-backup  # An identical copy, menu.lst-backup, will be created.

cp is for copy. If you want to copy a folder you have to do it recursively by adding -r, so it will be:

cp -r <folder-to-copy> <copy-of-folder>

---

### Post by chevelleman71 on 2010-02-23
Great Tom, thanks for the info. Much appreciated :-)

---

### Post by tom4everitt on 2010-02-23
No problem! Tell me how it goes.

---

### Post by chevelleman71 on 2010-02-24
> **tom4everitt said:**
> Say you want to do a backup of /boot/grub/menu.lst


Tom, updating that config file is something that i've read might be able to solve my problem. Problem is that that file doesnt exist on my install. Maybe this is because it's Karmic?

Also, I'm running the live cd to try and fix this. I've edited the etc/usplash.conf file and I'm trying to commit my changes by running 
```
sudo update-initramfs -u
```but all I get is this:

```
update-initramfs is disabled since running on read-only media
```So how can I update the usplash config from the live cd then? Help anyone?

Luke

---

### Post by chevelleman71 on 2010-02-24
Something else I can't figure out, when i look in /etc/usplash.conf it says the res is 1024 x 768, but the booting output says a different one. Am I even looking in the right place to change the setting and fix the problem?

Luke

---

### Post by tom4everitt on 2010-02-24
Okay, if you're using karmic you have grub2.

Here's a guide to the main changes:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

One of the changes is that menu.lst is now called grub.cfg, and is auto-generated from some other config files. Also the syntax is slightly different. 

You can still edit grub.cfg manually (you're not supposed to, but sometimes its convenient). First you have to do

sudo chmod +w grub.cfg           # EDIT: Remember to edit "the right" grub.cfg, i.e not the one on the live cd.

to be able to do it. 


Your other problem is that when you try to run update-initramfs you're actually trying to update the initramfs of the live cd. If you first do

sudo chroot <mount-point-of-your-old-filesystem>

it will try update the initramfs that you want. I'm not sure updating initramfs will help though....

---

### Post by chevelleman71 on 2010-02-25
Tom,

Thanks for your help. Somehow in the process of my troubleshooting I jacked up Grub and the partition. :(

Re-install and now I'm about back where I was before, now without problems. Thanks for your help!

Luke

---

