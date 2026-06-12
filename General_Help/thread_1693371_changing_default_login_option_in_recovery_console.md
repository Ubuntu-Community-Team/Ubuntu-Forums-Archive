---
title: "changing default login option in recovery console"
date: 2011-02-22
forum: General Help
---

### Post by shugoshin on 2011-02-22
By mistake I set the default login to recovery console on the login screen options. Now I am stuck at the recovery console and don't know how to change the settings on the terminal screen to get back to desktop.  Looking forward for your help.

Ubunutu 10.10
2.6.35-generic
No grub screen at startup
auto-login to user account

thank you.

---

### Post by drs305 on 2011-02-22
"default login"  options being the Grub 2 entries?

Reboot and hold down the SHIFT key during the early stages of the boot process. Hopefully the Grub2 menu will display and you can select the normal entry.

After booting, change the default boot entry by editing /etc/default/grub, using StartUp-Manager, or Grub Customizer. See my signature line for links.

---

### Post by shugoshin on 2011-02-23
thank you for reply

pressing SHIFT brought grub options. I select the first one:
"Ubuntu, with Linux 2.6.35-25-generic" while the second line is followed with "(recovery mode)". 

Ubuntu login screen appears and asks for the user name and password. Next comes the blank screen (Ubuntu 10.10 default wallpaper) with a white terminal window on the upper-left corner...

I believe this happens because I selected "Recovery Console" instead of "Ubuntu Desktop Edition" as the default session (see attachment).

Unfortunately the login screen does not have other options available at the bottom bar (only universal access preferences, time and shut down options appear).

So, I am still stuck here.

---

### Post by drs305 on 2011-02-23
I believe this setting is controlled by the /etc/gdm/custom.conf file. If you can boot into any Ubuntu mode and then edit the following line in /etc/gdm/custom.conf:
> [s]DefaultSession=xterm[/s]
DefaultSession=gnome

If you aren't able to boot to a mode that let's you edit the file, boot the LiveCD, mount your Ubuntu partition, and try editing the file "/<Ubuntu mount point>/etc/gdm/custom.conf"

If this doesn't work for you perhaps you have a issue with gdm that is preventing you from logging on. There might be kernel options you could add to the kernel line in your Grub menuentry but I'll have to let others provide them if they exist.

---

### Post by shugoshin on 2011-02-23
Thank you again,

it would be to good to check & edit /etc/gdm/custom.conf but I had lost my patience and did a fresh installation. When I mounted the Ubuntu installation using LiveCD to save my files I had noticed that the owner of many folders and files under /etc had become user rather than root. I think I had a careless command to change ownership of some other files. I don't know if this might have contributed to the problem.

---

