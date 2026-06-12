---
title: "full screen terminal"
date: 2011-10-02
forum: General Help
---

### Post by keymanu on 2011-10-02
question: I just installed ubuntu 11.04 and removed unity and installed gnome, cpu and vid card can't handle unity (so you know) i tried to ctrl-alt-F1 and got nothing. is there something that was not installed? I always liked that about linux.

I am thankful for nay help

---

### Post by spiky001 on 2011-10-02
Dose the desktop work ok? prehaps post details of pc

---

### Post by TeoBigusGeekus on 2011-10-02
That's why I don't use grub2: it makes my tty's disappear.

---

### Post by keymanu on 2011-10-02
> **spiky001 said:**
> Dose the desktop work ok? prehaps post details of pc

Yes the desktop works fine, had a problem with installing xnecc2c not showing up in menu's but taken care of..

it's a 975mz cup 387mb ram 

I have installed linux many time and never ran into this problem before. I am just trying to figure out if i missed something is all

---

### Post by ajgreeny on 2011-10-02
> **keymanu said:**
> Yes the desktop works fine, had a problem with installing xnecc2c not showing up in menu's but taken care of..

it's a 975mz cup 387mb ram 

I have installed linux many time and never ran into this problem before. I am just trying to figure out if i missed something is all
I am a bit surprised that Ubuntu 11.04 runs on that hardware, as the machine is lacking in ram, and also has a relatively slow, old cpu for a modern full gnome or unity distro.

I would recommend that you try Xubuntu or Lubuntu instead as they are both much lighter weight than gnome based Ubuntu, and should run a lot faster on that computer.

---

### Post by keymanu on 2011-10-02
> **ajgreeny said:**
> I am a bit surprised that Ubuntu 11.04 runs on that hardware, as the machine is lacking in ram, and also has a relatively slow, old cpu for a modern full gnome or unity distro.

I would recommend that you try Xubuntu or Lubuntu instead as they are both much lighter weight than gnome based Ubuntu, and should run a lot faster on that computer.

Thanks i'll pat myself on the back later

but i do need help with the ctrl+alt+F1 shell

---

### Post by spiky001 on 2011-10-02
My thoughts as well ajgreeny, I did find a problem with this as well
[http://ubuntuforums.org/showthread.php?t=1850667&highlight=ctrl+alt+f1](http://ubuntuforums.org/showthread.php?t=1850667&highlight=ctrl+alt+f1)  look at post #8 about changing GFXmode might be worth a go, But yes in the end it is a low spec machine

---

### Post by prodigy_ on 2011-10-02
> **keymanu said:**
> i tried to ctrl-alt-F1 and got nothing.
Most likely framebuffer driver defaults to an unsupported resolution. If you really need TTYs, here's a possible fix:

1. Run ```
sudo hwinfo --framebuffer
``` command to list supported resolutions.

2. Run the following script (needs root privs, so use sudo). Enter a supported resolution when prompted:
```
#!/bin/sh

cat << EOF

Screen resolution format is <width>x<height>,
for example: 800x600 or 1440x900 or 1920x1080.

EOF

printf "%s\n" "Enter the desired resolution (or press \"Ctrl+C\" to exit): "
read VBE_FBR

printf "%s" "$VBE_FBR" | grep -i '^[0-9]\{3,4\}x[0-9]\{3,4\}$' || f_ErrExit 1 "Wrong resolution format! " 1

aptitude install v86d

sed -i -e 's/\(GRUB_CMDLINE_LINUX_DEFAULT=\).*/\1"quiet splash nomodeset video=uvesafb:mode_option='${VBE_FBR}'-32,mtrr=3,scroll=ywrap"/' /etc/default/grub
sed -i -e 's/.*\(GRUB_GFXMODE=\).*/\1'${VBE_FBR}'x32/' /etc/default/grub

touch /etc/initramfs-tools/modules

if      [ -z "$(grep 'uvesafb ' /etc/initramfs-tools/modules)" ]
then
        printf "%s\n" "uvesafb mode_option=${VBE_FBR}-32 mtrr=3 scroll=ywrap" >> /etc/initramfs-tools/modules
else
        sed -i -e 's/.*\(uvesafb \).*/\1mode_option='${VBE_FBR}'-32 mtrr=3 scroll=ywrap/' /etc/initramfs-tools/modules
fi

touch /etc/initramfs-tools/conf.d/splash

if      [ -z "$(grep 'FRAMEBUFFER=' /etc/initramfs-tools/conf.d/splash)" ]
then
        printf "%s\n" "FRAMEBUFFER=y" >> /etc/initramfs-tools/conf.d/splash
else
        sed -i -e 's/.*\(FRAMEBUFFER=\).*/\1y/' /etc/initramfs-tools/conf.d/splash
fi

update-grub
update-initramfs -u
```

3. Reboot.

---

### Post by keymanu on 2011-10-02
> **spiky001 said:**
> My thoughts as well ajgreeny, I did find a problem with this as well
[http://ubuntuforums.org/showthread.php?t=1850667&highlight=ctrl+alt+f1](http://ubuntuforums.org/showthread.php?t=1850667&highlight=ctrl+alt+f1)  look at post #8 about changing GFXmode might be worth a go, But yes in the end it is a low spec machine

Yes that did the trick. Thank you

as for being a low spec machine= I have to work with what I have, this is the i386 version of 11.04, and by the ubuntu web page it should run on a 386 as long as it has over 256mb ram. I guess i proved that...hi hi 

Thanks to all who helped-- thank you

---

### Post by spiky001 on 2011-10-02
Glad to save pc:)

---

