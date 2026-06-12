---
title: "GRUB rescue"
date: 2010-11-18
forum: General Help
---

### Post by kadak.chocho on 2010-11-18
My machine starts and the grub rescue> flashes ....
 i tried to manually load into my ubunutu 10.4 kernel-2.6.32-24

my commands were
grub rescue>
  set prefix=(hdx,y)/boot/grub
  insmod linux
  insmod ext2
  set root=(hdx,y)
  linux (hdx,y)/boot/vmlinuz-2.6.32-24-generic
  initrd (hdx,y)/boot/initrd.img-2.6.32-24-generic
  boot

following this .... booting start ... untill i get a message .. waiting for root ...
and then 

Gave up waiting for root device. Common problems:
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missingm odules (cat /proc/modules; ls /dev)
ALERT! does not exit. Dropping to a shell!

BusyBox v........built-in shell (ash)
(initramfs)

here i can use a few shell commands ... i first need to mount my (dev/sdaY)in /tmp/ and then access the file ... no GUI



Please help me ... i have to start my computer in a hurry .... and have no access to a cd rom ... the internet connect here is sad .... so downloading a live CD and booting it from USB is also not an option.

ps - i am relatively a noob, only just started using ubuntu. Will be glad to learn along the way.

Thank you

---

### Post by oldfred on 2010-11-18
You did not actually use hdx,y did you? It should be the x= drive 0,1,2 etc and y = the partition where you have installed Ubuntu 1, 2, 3 or whatever. or (hd0,5) if on first drive, and partition 5 or sda5.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by kadak.chocho on 2010-11-18
11 ...... 
ofcourse not ..... otherwise i would not have been able to boot ... would have got a message saying ..  invalid filesystem .. or .... drive does not exist ....
i used .. (hd0,5) .... i have a total of 9 drives in hd0 .....
but now that you have asked .... i used (hd05) .. and /dev/sda5 to mount (in Busybox) ... when i needed to ... but it is not ncessary that they be the same ..... i however new them both to be (coincidently) same ... :)

---

### Post by oldfred on 2010-11-18
Did you try all the checks the grub rescue mega thread suggests to make sure you have correct partitions?

Without some linux based repair CD it is extremely difficult to review what you problems are and do repairs.

these are smaller downloads:
    * SystemRescueCd
    * PartedMagic 

Then I would run this (not 100% sure if all the linux commands are in above).

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by kadak.chocho on 2010-11-18
well i would have solved it .... had i access to a faster internet   ..... i am stuck in a remote area.... with a mobile broadband which keep  on disconnecting and reconnecting ...,
give me a bootable cd ... and Internet ... i can google and solve it......
but .... i really dont have access to any ......

i did check ... but as you can understand ... only to the best of my knowledge ......... find faults .... and possible faults in my theory/approach ..... syntax ... wise ... i guess it is right ...

thank you for your help ..... with time running out .... it actually quite invaluable

---

