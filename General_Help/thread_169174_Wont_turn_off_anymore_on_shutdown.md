---
title: "Wont turn off anymore on shutdown"
date: 2006-05-02
forum: General Help
---

### Post by spacemonkey13950 on 2006-05-02
Hello, im new to linux and i have just installed kubuntu 5.10 onto my
W720-K7 laptop which has AMD 2600+, 512ram, and ati video.

i did an update to make everything current and installed emc2 found here:
[http://timeguy.com/cradek/emc/ubuntu](http://timeguy.com/cradek/emc/ubuntu)
i think it changed it to a real time version
i now have many boot choices in grub the latest being kubuntu magma (after emc2)

since then it does not shut down properly just says 'power down' and i have to hold the power button.

how can i fix this?

also..
can i get rid of the other boot choices and how?
it freezes randomly when used and while idle, can it be fixed
the cpu fan is always running at maximum and hot, is there something like a driver to automatically throttle it? (windows xp changes the cpu voltage and frequency depending on load)

i hope to find some answers, apart from these problems im having a super happy fun time in linux

---

### Post by geek.de.nz on 2006-05-02
Looks like this installs another kernel. Is that right? Well, if then it could be that ACPI is not working properly afterwards. Can you boot your old kernel?

---

### Post by spacemonkey13950 on 2006-05-02
Yes you are right, it installed a new kernel: Ubuntu, kernel 2.6.12-magma
i can boot kernel 2.6.12-10-386 and it shuts down and turns off properly
but i cannot run the emc2 program :-k

---

### Post by geek.de.nz on 2006-05-02
OK. try recompiling your own kernel with the options of the 2.6.12-magma:

Follow this guide:
[http://ubuntuforums.org/showthread.php?t=85064&page=9&highlight=howto+compile+kernel+newbies#1](http://ubuntuforums.org/showthread.php?t=85064&page=9&highlight=howto+compile+kernel+newbies#1)

Before you do
sudo make oldconfig (so as not to compile the entire kernel from scratch)

copy the config file for that kernel which should be in /boot
do
```
sudo -l
#enter password
cd /usr/src/linux #this should be the directory where your kernel sources are
ls -l /boot/config*
cp config-2.6.12-magma ./.config
make oldconfig
...

```

If that doesn't work, you might have to apply an additional patch related to magma. Just google around. I don't have time to do that for you.

Hope that helps, cheers.

---

