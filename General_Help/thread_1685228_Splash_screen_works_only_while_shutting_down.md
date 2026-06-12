---
title: "Splash screen works only while shutting down"
date: 2011-02-10
forum: General Help
---

### Post by patelsagar on 2011-02-10
Hello guys :)

I can't see any boot splash while booting up, all I see is a black screen and then it directly lands on Login screen. But boot splash does work while shutting down the PC. My kernel version is 2.6.35-25.

I remember I tried to tweak grub.d (05_debian_theme specifically). But I just removed and reinstalled Grub2 and problem still persists.

Also, I have compiled kernel 2.6.37, and boot splash works on it fine.

Any idea what can be the problem?

Note: I am talking about boot splash and not the boot-time wallpaper (I had modified 05_debian_theme to have wallpaper working). But again, everything seems as per default settings as I removed and reinstalled Grub2.

---

### Post by Tyler27 on 2011-02-10
Are you in the grub folder trying change the grub file from quiet splash to text to boot in text mode? I don't understand what your trying to do. Other than see the splash on the boot up

---

### Post by deltaflow on 2011-02-10
Try this:

Open a terminal and enter:

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

then add the line: FRAMEBUFFER=y

Save that, and close it, then back to the terminal and enter:

```
sudo update-initramfs -u
```

I was having the same issue until about half an hour ago, and this worked :)

---

### Post by patelsagar on 2011-02-10
> **deltaflow said:**
> Try this:

Open a terminal and enter:

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```then add the line: FRAMEBUFFER=y

Save that, and close it, then back to the terminal and enter:

```
sudo update-initramfs -u
```I was having the same issue until about half an hour ago, and this worked :)

Hi, thanks for the quick help, but it didn't make a difference :(

Actually, that file had FRAMEBUFFER=y already written in it. It is the only thing written in that file, is that normal?
Also, the command ```
sudo update-initramfs -u
``` gave me following result:
```
update-initramfs: Generating /boot/initrd.img-2.6.37
```I guess it should show kernel version 2.6.35, isn't it? Yes, I am seeing that result while running 2.6.35.
```
uname -r
``` gives following result:
```
2.6.35-25-generic
```

---

### Post by patelsagar on 2011-02-10
All right guys, problem solved!

I just had to create kernel image of my 2nd kernel 2.6.35-25. I just issued this command: ```
sudo update-initramfs -c -k all
``` and problem solved!

Thanks for making this forum :)

---

