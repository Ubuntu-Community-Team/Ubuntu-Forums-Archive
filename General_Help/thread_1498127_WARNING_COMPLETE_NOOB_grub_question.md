---
title: "WARNING COMPLETE NOOB grub question"
date: 2010-05-31
forum: General Help
---

### Post by kup_kake on 2010-05-31
So when i boot up into grub why dose it show 2 versions of ubuntu something like this
Ubuntu, with linux 2.6.32-22- generic 
Ubuntu, with linux 2.6.32-22- recovery
ubuntu, with linux 2.6.32-21- generic
ubuntu, with linux 2.6.32-21- recovery

---

### Post by warri0r on 2010-05-31
its the new kernel update. 2.6.32-22- generic is the kernel version. whenever a kernel update is released from ubuntu update server, it will be added to the existing ones so that u can boot onto anything u wish. for more info on kernel go [http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

u may also remove them when u have a huge list.

---

### Post by cfalzone on 2010-05-31
If you want to clean up your Grub menu you can-- if you want to remove the old kernels from your system first boot using the kernel that you want to keep (probably the most current one) and then once you've gotten to desktop you can start the Synaptic Package Manager.

In Synaptic, enter the search term "linux-image" (without quotes) and find the older kernel and select it for removal or complete removal.  Apply the removal and the next time you boot up it won't be on your menu any more.

For more information on Grub2 you should check out [http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by Ginsu543 on 2010-05-31
It's generally a good idea to have two kernels installed in case something goes wrong with one, because then you can at least boot with the other. However, if you wish to remove a kernel version, you need to remove the following three files (where, of course, XX-XX is the version you want to remove):

1) linux-headers-2.6.XX-XX
2) linux-headers-2.6.XX-XX-generic
3) linux-image-2.6.XX.XX-generic

---

### Post by warri0r on 2010-05-31
may be this could help, but having 2 kernels is highly advised.

[http://www.fixthecode.com/remove-huge-kernel-lists-in-ubuntu/](http://www.fixthecode.com/remove-huge-kernel-lists-in-ubuntu/)

---

### Post by tad1073 on 2010-05-31
> **kup_kake said:**
> So when i boot up into grub why dose it show 2 versions of ubuntu something like this
Ubuntu, with linux 2.6.32-22- generic 
Ubuntu, with linux 2.6.32-22- recovery
ubuntu, with linux 2.6.32-21- generic
ubuntu, with linux 2.6.32-21- recovery

Those are kernels not versions of Ubuntu. A kernel is the backbone of the OS, it allows interaction of your hardware with the OS.

I suggest you use "Ubuntu Tweak" to remove the extra, but I would take the advice of warri0r.

copy and paste these commands in your terminal

```
[COLOR=#666666][COLOR=Black]sudo add-apt-repository  ppa:tualatrix/ppa[/COLOR]
[/COLOR]
sudo aptitude update

sudo aptitude install ubuntu-tweak

```

---

### Post by kup_kake on 2010-05-31
Thanks, its on a comp with vista and ubuntu 10.04 so i should probably keep both kernals?
this comp is also being shared with family members, it also shows to vista options, and way to make this simpler for family members?

---

### Post by tad1073 on 2010-05-31
> **kup_kake said:**
> Thanks, its on a comp with vista and ubuntu 10.04 so i should probably keep both kernals?
this comp is also being shared with family members, it also shows to vista options, and way to make this simpler for family members?

One of the vista partitions is the Recovery partition, the other is Vista that is being used by your family.
One way to make it easier is to set Vista as the default OS.

---

### Post by warri0r on 2010-06-01
> **kup_kake said:**
> Thanks, its on a comp with vista and ubuntu 10.04 so i should probably keep both kernals?
this comp is also being shared with family members, it also shows to vista options, and way to make this simpler for family members?

make vista as the default choice on the boot menu. for this get into ubuntu and edit the grub.cfg file (assume u using grub2)

1. open terminal and issue
sudo nano /boot/grub/grub.cfg
2. change the "set default=0" entry to the value for vista. 0 corresponds to the first entry on the menu, if vista is the third entry then you have to choose 3 as the value.
3. press ctrl+o and ctrl+x reboot the machine.

ps. be careful while editing the file and these values will be restored to defaults, once there is a kernel update. you have to manually do the above process again to make vista default, Kernel updates are not frequent though.

---

### Post by Ginsu543 on 2010-06-02
Instead of editing the grub.cfg file directly, you should make the change suggested by warri0r in the /etc/default/grub file. The first line you'll see is GRUB_DEFAULT=0. As warri0r said, change this value to one that corresponds to your entry for Vista. Save the file, and then in Terminal run the command:

```

sudo update-grub

```

That will make the appropriate changes in the grub.cfg file for you. The grub.cfg file is not meant to be changed directly because those changes are not permanent (every time the update-grub command is issued or there is a kernel update, the grub.cfg file is overwritten). So to make the changes permanent, you have to change the /etc/default/grub file.

---

