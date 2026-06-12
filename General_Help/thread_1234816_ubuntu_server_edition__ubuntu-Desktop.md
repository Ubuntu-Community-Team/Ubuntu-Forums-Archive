---
title: "ubuntu server edition / ubuntu-Desktop"
date: 2009-08-08
forum: General Help
---

### Post by Teh_Messiah on 2009-08-08
Hi everyone,
I built a file server using the bit tech forum "Build your own server" Tutorial last year. 

Recently i installed the Ubuntu server edition not realising that it had no GUI. So I apt-get install ubuntu-desktop.
Previously i had Xubuntu as per the instructions from the tutorial at Bit Tech.
I have most of my stuff back up and running however I am having problems getting several things to work.
[LIST=1]
[*]firefox wont start
[*]torrentflux I cant find the sql folder to move forward through the install
[*]Xine wont install
[*]I would also like to revert back to Xubuntu-desktop instead of Ubuntu
[/LIST]
Firefox wont work even though i removed it and reinstalled it. There is no lock file in the /home/username/firefox directory anywhere. The cursor does the busy animation while it tries to load but then it all disappears.

Instead of following their instructions I had to apt-get torrentflux since my firefox issue. I forgot to install the phpmyadmin and mysql-server-5.0. After installing these and reinstalling torrentflux via apt-get I can't find the sql folder. Where is it?

Also I want to install Xine to play my movie files as i have my plasma connected directly to the server.

Is there a way i can revert Ubuntu back to Xubuntu? I tried to apt-get install xubuntu-desktop and it ran through the install but it is still Ubuntu. 
Do I need to apt-get remove Ubuntu-desktop 

Please help.

---

### Post by SoftwareExplorer on 2009-08-08
What happens if you run ```
firefox
``` in a terminal? What does it say is wrong?

---

### Post by Teh_Messiah on 2009-08-08
Absolutely nothing happens! :(

---

### Post by SoftwareExplorer on 2009-08-09
Hmm. Can't help you with the firefox--I'm basically blind. When you log in, look for something like session, you can have multiple desktop environments installed and pick when you log in.

---

### Post by Teh_Messiah on 2009-08-09
I don't know what i have done but i am going to re-install the OS from the disk and start again! 
This is really annoying.
I think i messed up when i apt-get install ubuntu-desktop.
maybe i should have specified the version ubuntu-desktop_8.04_lts or something. 
Not really sure where i went wrong.
Any suggestions on the VNC thing? I have always had an issue with vnc and could never get it to work.

BTW, I love mdadm. So easy to re-build my raid-5 array for my files.

I'll let you know how the full re-install goes. Hopefully i don't need to unplug the power from my sata hdds this time.

---

### Post by SoftwareExplorer on 2009-08-09
> **Teh_Messiah said:**
> 
Any suggestions on the VNC thing? I have always had an issue with vnc and could never get it to work
Were you running 9.04 with compiz and trying to do VNC?

---

### Post by Teh_Messiah on 2009-08-09
I'm running xubuntu 8.04 and followed all the steps in the tutorial and VNC still doesn't work.
I used to have a problem setting the passwd but installed vncserver-common (cant remember exact name right now) and that fixed that problem. But i couldn't progress any further than that.

On another note. I managed to get xubuntu installed without unplugging the power from my raid-5 hdds. 
However it won't boot to the os and I get
```
Error 17: Cannot mount selected partition

Press any key to continue...
```
When i press a key it goes to the grub menu and i can't boot from any of the selections so i edit the first 1.
I press "C" to open a command line in grub.
root is set to (hd4,0) instead of (hd0,0) so i type the commands:
```
grub> root (hd0,0)
grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 16 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.

grub> reboot
```
It then reboots obviously and i get this again
```
Error 17: Cannot mount selected partition

Press any key to continue...
```
If i edit the 1st item in the menu i get
```
root (hd4,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=5f6594ac-6836-4ef0-->
initrd /boot/initrd.img-2.6.24-16-generic
quiet
```
If i just edit the root (hd4,0) to (hd0,0)
then press b to boot from root (hd0,0) it boots but i couldn't access the network last night but now i can :confused:

---

### Post by Teh_Messiah on 2009-08-09
Now i am getting the same error i had before the
> Error 17: Cannot mount selected partition

Press any key to continue...

```
Error 24: Attempt to access block outside partition

Press any key to continue...
```
And the grub menu is back to this again
```
root (hd4,0)
kernel /boot/vmlinuz-2.6.24-24-generic root=UUID=5f6594ac-6836-4ef0-->
initrd /boot/initrd.img-2.6.24-24-generic
quiet
```

---

### Post by SoftwareExplorer on 2009-08-10
What if you run ```
sudo blkid
``` figure out which one is your ubuntu partition. Then instead of using the root command, you can use ```
uuid <18ea-c23-&so-on-here>
```

Why use uuid? Well, that way, it doesn't matter weather the partition is 4,0 or 0,0. The uuid stays the same.

---

### Post by Teh_Messiah on 2009-08-10
LOL
I just had to edit the menu.lst file and now it works! YAY
I'm a n00b :(
Now for VNC!
Lets try that again!

---

