---
title: "Removing Old Linux Generics"
date: 2009-08-20
forum: General Help
---

### Post by glantela on 2009-08-20
i was just wondering if it was possible to remove the old linux kernels so it doesnt show up on my Grub boot loader.  Or is there any use to keeping the old ones?

Thanks!

---

### Post by Copernicus1234 on 2009-08-20
Yes, you can edit the /boot/grub/menu.lst file but you should google a bit and find out how it works first so you dont make mistakes. :)

You should keep at least one old kernel in the list however. Its good for the day when a updated kernel somehow doesnt work for you. Then you have a fallback alternative.

---

### Post by pedro_orange on 2009-08-20
> **glantela said:**
> i was just wondering if it was possible to remove the old linux kernels so it doesnt show up on my Grub boot loader.  Or is there any use to keeping the old ones?

Thanks!

Sure thing.

```
gksudo gedit /boot/grub/menu.lst 
```

You might want to keep a backup before editing it.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

If you want to stop certain kernel's booting, just comment them out at the bottom of the file.

---

### Post by drs305 on 2009-08-20
You can refer to the following link to learn about removing older kernels. I originally wrote it to provide assistance in limiting the number of kernels displayed and expanded it to include StartUp-Manager. SUM is a great GUI app that lets you tweak many grub settings without manually editing the system files.
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

The post details various ways to hide or physically remove older kernels, and provides tips if you wish to edit the menu.lst file manually as well.

---

### Post by glantela on 2009-08-20
That was quick! thanks guys!

---

### Post by sefs on 2009-08-20
I usually used synaptic to uninstall old kernerls, and it also cleanly removes them from the boot loader file as well.

---

### Post by nilarimogard on 2009-08-20
All you have to do is run this command:

dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge-*' 

From [here]("http://webupd8.blogspot.com/2009/06/10-linux-unix-useful-commands.html").

---

### Post by scouser73 on 2009-08-20
Visit this tutorial: [[COLOR="Red"]**Removing Old Kernels**[/COLOR]]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

---

### Post by Copernicus1234 on 2009-08-20
> **nilarimogard said:**
> All you have to do is run this command:

dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge-*' 

From [here]("http://webupd8.blogspot.com/2009/06/10-linux-unix-useful-commands.html").

That command is a bit basic but it will have to do I guess.

:P

---

### Post by glantela on 2009-08-20
seems kinda ridiculous :)!

---

### Post by oboedad55 on 2009-08-21
> **Copernicus1234 said:**
> That command is a bit basic but it will have to do I guess.

:P

Yeah, it looks a little primitive...

---

