---
title: "in big trouble"
date: 2006-05-11
forum: General Help
---

### Post by gos1 on 2006-05-11
Hi ; 
 While playing (learning) to play with kernel  I crushed my system. and now want to completely remove that kernel (gdm doesnt work just the console) and want to install again a standart kernel what should I do to do this. I need this immediately because got some important software and codes in that partition and want to continiue using with the same settings. Can anyone help me please ? ?? ? ?

---

### Post by Ramses de Norre on 2006-05-11
Did you delete the previous kernel? Otherwise you can just select it in grub and boot it. Press esc to see the grub menu when it's not showed by default.

---

### Post by gos1 on 2006-05-11
I have only one choice on the grub menu. I had the preempt50kerneland removed it. now messed up with the last one I had :(

---

### Post by Ramses de Norre on 2006-05-11
But did you actually deleted the previous kernel? 
Otherwise press e on the kernel line and make the section to this: ```
title           Ubuntu, kernel 2.6.12-10-k7
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot

```
Don't change the root partitions (I assume they'll stay the same), but do change k7 to 686 or 386 if you were using that.

---

### Post by gos1 on 2006-05-11
yes unfortunately I deleted the old kernel I had. I have only one and now and it doesnt work...
can you please tell me step by step how to download and compile the latest kernel from console....?????

---

### Post by Ramses de Norre on 2006-05-11
Maybe you can get it from the install cd and paste it in /boot/ but I'm not sure whether it will be that simple.. You'll need a live cd or another pc to do the pasting.

---

### Post by gos1 on 2006-05-12
I found out that my problem is from the XGL packages or nvidia drivers how can I remove them all. and re install them ? (from console ofcorse)

---

### Post by tseliot on 2006-05-12
[QUOTE=gos1]I found out that my problem is from the XGL packages or nvidia drivers how can I remove them all. and re install them ? (from console ofcorse)[/QUOTE]
Try my script. 

1) Type:

```
wget http://www.albertomilone.eu/ubuntu/nvidia/scripts/nvidia_script_8756_32
```

2) Make the script executable:

```
sudo chmod a+x nvidia_script_8756_32
```

3) sudo /etc/init.d/gdm stop

(it doesn't matter if it complains, just go ahead)

4) Run the script:

```
sudo ./nvidia_script_8756_32
```

(DON'T forget the "." before the "/" )

Then answer the questions the installer asks you.

That should solve your problems

P.S. It can take a while for my script to install the driver, so please be patient.

---

### Post by az on 2006-05-12
You can also boot the installer and pick the rescue option.  It will ask which partition you want to chroot into.

Once you are at the command line, run

apt-get install linux-image-386 (or whatever arch you want) and that will install the ubuntu kernel.  You will have to reinstall your nvidia driver afterwards.

You should also recofigure X before rebooting into your kernel

dpkg-reconfigure -phigh xserver-xorg

reboot

---

### Post by steve.horsley on 2006-05-12
If the nvidia driver is your only problem, you should be able to fix it by changing the the nv driver instead. At your command line:
**sudo nano /etc/X11/xorg.conf**
under Section "Device" change Driver "nvidia" to Driver "nv"
Save and restart X:
**sudo /etc/init.d/gdm restart**

---

