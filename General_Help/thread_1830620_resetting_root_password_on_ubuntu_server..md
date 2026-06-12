---
title: "resetting root password on ubuntu server."
date: 2011-08-22
forum: General Help
---

### Post by chait on 2011-08-22
Hi All,
   I have installed ubuntu 10.04 Lucid on one of my workstations. I have not installed any GNOME or KDE on this server. So its all command line. Now I want to reset the root password. How to do it in this scenario?
I can change root password on the systems with gnome/kde installed. How to display the boot menu in this case?

Thanks.

---

### Post by asomad on 2011-08-22
Log in to your root account. (if it's enabled, I think it's supposed to be disabled by default)

type: passwd

---

### Post by stefangr1 on 2011-08-22
> **asomad said:**
> Log in to your root account.

type: passwd

If you forgot your root password, you can login as a normal user, and then reset the root password by typing

```
<snip>
```

---

### Post by Primefalcon on 2011-08-22
Go and read this! It'll explain how to enable the root password (as well as how to change it). And why you really shouldn't

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by chait on 2011-08-22
Hi All,
  Thanks for giving such quick responses. I have lost my root password. Also the other user's password which was in the sudoers list. Now is it possible to reset root's password? How do I display the boot menu, so that I can boot the kernel in single user mode, and would be able to change root's password?

Thanks.:confused:

---

### Post by fdrake on 2011-08-22
> **chait said:**
> Hi All,
  Thanks for giving such quick responses. I have lost my root password. Also the other user's password which was in the sudoers list. Now is it possible to reset root's password? How do I display the boot menu, so that I can boot the kernel in single user mode, and would be able to change root's password?

Thanks.:confused:

boot, press shift untill u see the grub menu,  press shift again untill u see the recovery menu, select root

```
passwd your-user-name
```

---

### Post by sisco311 on 2011-08-22
> **chait said:**
> Hi All,
  Thanks for giving such quick responses. I have lost my root password. Also the other user's password which was in the sudoers list. Now is it possible to reset root's password? How do I display the boot menu, so that I can boot the kernel in single user mode, and would be able to change root's password?

Thanks.:confused:

You have to hold down the Shift key during the boot. If the root account password is enabled, then you will be prompted for it in Recovery Mode. If you don't remember it, then highlight the Recovery Mode menu item, press e for edit, delete the **ro single** kernel parameters from the end of the *linux* line and replace them with **rw init=/bin/bash**, then press Ctrl+x to boot the system. 

You might have to remount the root partition before you change the passwords:
```
mount -o remount,rw /
passwd root
passwd user
reboot #Press Ctrl+Alt+Del if this command doesn't work.

```

Or boot a Live CD, mount the root partition and change the passwords. Assuming that sda1 is the root partition, run:
```

sudo mount /dev/sda1 /mnt
sudo chroot /mnt
passwd username
exit

```

If one of your users has full sudo rights, then you can lock the root account password, see: [uhelp]community/RootSudo[/uhelp]

---

### Post by chait on 2011-08-23
Thank you all for replying. Issue solved.
Thanks again.:P

---

