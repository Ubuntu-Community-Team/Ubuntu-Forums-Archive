---
title: "Grub won't boot!"
date: 2010-07-23
forum: General Help
---

### Post by Nifty123 on 2010-07-23
I dual installed ubuntu 10.04 and windows 7 a while ago. it worked fine until i changed the grub setting for the wait time to '0' seconds, hoping to achieve a default boot into windows when i turn my computer on. Also i though this would give me the option to hold a button to get grub boot menu to come up so i can select linux if i wanted to. Now my computer just boots to windows, ive tryed holding down different buttons but it just boots to windows everytime. Can someone help me

---

### Post by utnubuuser on 2010-07-23
you could boot a liveCD and edit your grub menu from the live desktop

I think the esc button is supposed to interupt to a grub menu

---

### Post by garvinrick4 on 2010-07-23
Boot off of your Ubuntu CD and choose Try Ubuntu:
Mount drive:
Open a Terminal:

```
gksudo gedit /etc/default/grub
```#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Make the GRUB_TIMEOUT=X    (-1=no countdown) (0=boots to default OS)
Save then reboot:
When in Ubuntu:
```
sudo update-grub
```Anytime you change something in grub you must update-grub.

---

### Post by Nifty123 on 2010-07-23
Tryed doing it through the terminal, but the live cd does not recognise the drives with ubuntu installed. Can someone help me on this, im pretty amature with linux. Is there a way of making the live cd recognise my ubuntu installing on my hdd?

---

### Post by Nifty123 on 2010-07-23
Is there a button you can prett when the computer is trying to boot to bring up grub menu

---

### Post by oldfred on 2010-07-23
With old grub it was escape, with grub2 it is the shift key. But you cannot just press it you have to hold it from BIOS boot until menu comes up.

---

### Post by Nifty123 on 2010-07-24
> **oldfred said:**
> With old grub it was escape, with grub2 it is the shift key. But you cannot just press it you have to hold it from BIOS boot until menu comes up.

I hold shift down and the word 'grub' appears on the screen with dots next to it like it's loading and then it just starts loading windows.

---

### Post by linux18 on 2010-07-24
boot a live cd then type:
```
 sudo grub-install /dev/sda && sudo update-grub 
```

---

### Post by Nifty123 on 2010-07-24
> **linux18 said:**
> boot a live cd then type:
```
 sudo grub-install /dev/sda && sudo update-grub 
```

I tryed that, but it said this:

[IMG]http://i753.photobucket.com/albums/xx175/NickNZ125/Screenshot.png[/IMG]

?

---

### Post by linux18 on 2010-07-25
> **Nifty123 said:**
> I tryed that, but it said this:

[IMG]http://i753.photobucket.com/albums/xx175/NickNZ125/Screenshot.png[/IMG]

?
oops, my fault, I forgot to put the " sudo umount -a " command in there.
just run  " sudo umount -a  " then   
" sudo grub-install /dev/sda && sudo update-grub "

---

### Post by oldfred on 2010-07-25
If installing grub to the MBR from a liveCD you have to tell it which partition the grub files are in.

Install from LiveCD install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

linux18's command works if you are reinstalling from the copy you are in as then it knows which partition (the one you are in) to find the grub file.

---

