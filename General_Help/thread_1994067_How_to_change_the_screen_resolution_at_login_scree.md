---
title: "How to change the screen resolution at login screen"
date: 2012-06-02
forum: General Help
---

### Post by Nimbu on 2012-06-02
I am running ubuntu 12.04 64-bit (fully updated). I can change the screen resolution for when I am logged into my user account in ubuntu. However I cannot seem to find where to change the default login screen resolution. Can someone please help me with this?

---

### Post by TheFu on 2012-06-02
There are probably many ways to handle this. The graphics card driver probably has a GUI tool to manage this - I know nvidia uses "nvidia-xconfig."  Needs to be run with sudo.

---

### Post by Nimbu on 2012-06-03
> **TheFu said:**
> There are probably many ways to handle this. The graphics card driver probably has a GUI tool to manage this - I know nvidia uses "nvidia-xconfig."  Needs to be run with sudo.

It seems to be a bug with the current 12.04 release. I have an ati card which has very poor driver support anyway so that doesn't help.

---

### Post by pbrane on 2012-06-03
This is what I did to fix my initial screen resolution. I did this in 11.10 and upgraded to 12.04. It appears to be still working.
```

[COLOR="Red"]# fix the plymouth splash screen and VT resolution[/COLOR]

sudo apt-get install v86d
[COLOR="red"]# use any text editor you want to here.[/COLOR]
sudo **[COLOR="red"]emacs[/COLOR]** /etc/default/grub

[COLOR="red"]# add this[/COLOR]
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1440x900-24,mtrr=3,scroll=ywrap"
GRUB_GFXMODE=1440x900

[COLOR="red"]# save[/COLOR]

[COLOR="red"]# same here for the text editor[/COLOR]
sudo [COLOR="red"]emacs[/COLOR] /etc/initramfs-tools/modules

[COLOR="red"]# add:[/COLOR]
uvesafb mode_option=1440x900-24 mtrr=3 scroll=ywrap

[COLOR="red"]# save[/COLOR]

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash

sudo update-grub2

sudo update-initramfs -u

[COLOR="red"]# reboot ![/COLOR]

```
You should replace the 1440x900 and 1440x900-24 with your native screen resolution and bit depth. Also you can use any text editor instead of emacs that you want.

See this article for more info:
[http://byobu.info/wiki/Changing_Plymouth_Resolution_in_Ubuntu]("http://byobu.info/wiki/Changing_Plymouth_Resolution_in_Ubuntu")

---

### Post by Nimbu on 2012-06-03
> **pbrane said:**
> This is what I did to fix my initial screen resolution. I did this in 11.10 and upgraded to 12.04. It appears to be still working.
```

[COLOR="Red"]# fix the plymouth splash screen and VT resolution[/COLOR]

sudo apt-get install v86d
[COLOR="red"]# use any text editor you want to here.[/COLOR]
sudo **[COLOR="red"]emacs[/COLOR]** /etc/default/grub

[COLOR="red"]# add this[/COLOR]
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1440x900-24,mtrr=3,scroll=ywrap"
GRUB_GFXMODE=1440x900

[COLOR="red"]# save[/COLOR]

[COLOR="red"]# same here for the text editor[/COLOR]
sudo [COLOR="red"]emacs[/COLOR] /etc/initramfs-tools/modules

[COLOR="red"]# add:[/COLOR]
uvesafb mode_option=1440x900-24 mtrr=3 scroll=ywrap

[COLOR="red"]# save[/COLOR]

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash

sudo update-grub2

sudo update-initramfs -u

[COLOR="red"]# reboot ![/COLOR]

```
You should replace the 1440x900 and 1440x900-24 with your native screen resolution and bit depth. Also you can use any text editor instead of emacs that you want.

See this article for more info:
[http://byobu.info/wiki/Changing_Plymouth_Resolution_in_Ubuntu]("http://byobu.info/wiki/Changing_Plymouth_Resolution_in_Ubuntu")

I have tried to follow that guide you have posted. However when I issue the command.
```

sudo update-grub2

```

It outputs this and then seems to get stuck.
```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin

```
Any ideas on how to get it to work?

---

### Post by pbrane on 2012-06-03
I'm not sure what's happening there. **update-grub** or **update-grub2** should work. you could try running **update-grub** instead. No 2 at the end. Have a look at the link I posted, there is some info there about ubuntu 12.04 that might be pertinent.

---

