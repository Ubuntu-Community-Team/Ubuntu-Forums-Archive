---
title: "&gt;grub issue"
date: 2011-10-29
forum: General Help
---

### Post by sublimestyle on 2011-10-29
ive been messing around with the MBR trying to get my windows to boot after installing 11.10 on my thinkpad, and now when i boot i get a grub> command prompt, heres the log i got from grub repair 
[http://paste.ubuntu.com/721802/](http://paste.ubuntu.com/721802/)
anyone know how to fix this?

---

### Post by garvinrick4 on 2011-10-29
Yes you have somehow install grub legacy (grub) into the mbr instead of grub2 (grub-pc)
Use live cd (install cd using Try Ubuntu) open a terminal:
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```Boot into Ubuntu
```
sudo update-grub
```Now both should work if not we will have to purge all things grub and reinstall with a few
more lines of code:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by sublimestyle on 2011-10-29
everything installed well, but the grub that was there before with the list is replaced by "press esc to view list", then automatically boots ubuntu if you dont press esc. the list is the same as on the GNU grub when choosing an OS, but windows is not even listed anymore. ill try the purge and reply when done

---

### Post by garvinrick4 on 2011-10-29
> but windows is not even listed anymoreIt will not show until you boot into Ubuntu and do the sudo update-grub
> ill try the purge and reply when done
If you need the code let me know.
When installing grub it go's in sda not anything else.
Might have to use arrows,enter and tab to navigate with.

---

### Post by sublimestyle on 2011-10-29
after purging and reinstalling the grub, everything was back to normal, the original grub loaded and windows and ubuntu were both listed as usual. 
thanks garvin!

though that hurdle is now out of the way, theres a deeper issue with my windows.
after i repartitioned my disk to give more space to ubuntu when i installed 11.10, i seemed to have lost some ciritcal files in windows 7. Windows 7 (on /dev/sda1) loads with a black screen and blinking underscore and Windows 7 (on /dev/sda2) boots Windows Error recovery, then claims \Windows\system32\ntoskrnl.exe is in status 0xc000000f and Windows failed to load because the kernel is missing, or corrupt..

edit: would you know anything about solving this issue?
i made a new thread for this: [http://ubuntuforums.org/showthread.php?t=1871883](http://ubuntuforums.org/showthread.php?t=1871883)

thanks a lot!

---

### Post by garvinrick4 on 2011-10-29
> after purging and reinstalling the grub, everything was back to normal,  the original grub loaded and windows and ubuntu were both listed as  usual. 
thanks garvin! You are welcome a user by the name of drs305 wrote the tutorial.
> though that hurdle is now out of the way, theres a deeper issue with my windows.
after i repartitioned my disk to give more space to ubuntu when i  installed 11.10, i seemed to have lost some ciritcal files in windows 7.  Windows 7 (on /dev/sda1) loads with a black screen and blinking  underscore and Windows 7 (on /dev/sda2) boots Windows Error recovery,  then claims \Windows\system32\ntoskrnl.exe is in status 0xc000000f and  Windows failed to load because the kernel is missing, or corrupt..
User by the name of oldfred is good with Windows problems. Look for him if he hits your
thread and learn. sda1 is boot partition for windows should be the one you use I do believe to boot windows.
Do another boot script and post here and highlight whole thing and hit the # sign in upper right of message box
and will put in nice box to read it from.

---

### Post by garvinrick4 on 2011-10-29
Might have to install Windows boot loader and boot windows:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

Now put in Ubuntu live cd and use the code I gave you again to put grub2 in post 2:
Make sure to boot into ubuntu and do the sudo update-grub, that puts windows
in menu entrys and config file.

---

