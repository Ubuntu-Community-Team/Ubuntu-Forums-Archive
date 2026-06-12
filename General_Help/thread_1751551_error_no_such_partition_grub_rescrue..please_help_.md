---
title: "error: no such partition grub rescrue..please help me!!!! lol"
date: 2011-05-06
forum: General Help
---

### Post by Czvp on 2011-05-06
Can anyone please tell me in the basic noob way of how to remove ubuntu from the dual boot??? and i need every little step because i repeat, i am a noob!! lol i want to wipe it out completely and just use it through the virtual machine.
 
 
 
Welp as you can probably can tell from the title i deleted the ubuntu partition from my pc that came with windows 7 and now when i start i get that error message. i kind of have an idea from reading other post about what is happening. i believe its looking for the ubuntu bootloader and its not finding it, correct me if im wrong. im not panicing because last night i did it once and read up on reinstalling it from my live cd will fix the boot problem and my pc will start like normal. ok well my question is...how do i get rid of ubuntu from a dual boot. dont get me wrong i love ubuntu but i love VM more and want to run it through there instead. today someone told me to delete all the partitions that does not have anything to do with windows and i did but it still didnt work so now im asking for help. 
 
 
How to competely Remove Ubuntu From Partitions after having a dual boot???

---

### Post by drs305 on 2011-05-06
I will give you the first step - restoring the Windows bootloader. Assuming the Windows boot files haven't been corrupted and that your Windows is on **sda**:

Boot the Ubuntu LiveCD and select "Try It". Open a terminal and install an app called 'lilo'. Run the two commands; don't bother with messages saying to configure lilo, and then reboot into your Windows bootloader:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Reboot.

If Windows boots, you can use Windows partitioning software to remove the Ubuntu partitions (you probably have two - the Ubuntu partition and a small swap partition).

---

### Post by Czvp on 2011-05-06
whoaaaa that was fast big guy!!! ill try that now! thanks!

---

### Post by varunendra on 2011-05-07
Or (with due respect to drs305), you may try just restoring Windows 7 MBR which was replaced by GRUB.

If you have Win 7 Installation DVD: [http://windows7themes.net/how-to-fix-mbr-in-windows-7.html](http://windows7themes.net/how-to-fix-mbr-in-windows-7.html)

If you don't have Win 7 installation DVD, you can download and use Windows 7 System Recovery Discs : [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Whatever suits you best!

A piece of unsolicited advice from a noob (don't get fooled by my beans, they mean nothing;))to a noob (you said it, not me;)): If you really love Ubuntu, why use it in a restricted, crippled environment (VM??). VMs are very good for testing and simulating multi OS environment (that often CS students need), but can't provide full featured OS experience. Also, for the latter case, you may try Win 7 in VirtualBox instead. So I think dual boot was the best option for you and you should rather keep it that way.

But that was just an opinion, you may have your own reasons and priorities. :)
Good luck!

---

### Post by Czvp on 2011-05-07
Hey thanks a lot varunendra but i used drs305's method to the madness and it worked flawlessly! 
The only step i had to add was updating my grub before the lilo command he gave me would actually work.
But speaking of ur method, i kind of tried something like that by pressing f10 at the start up and running the system recovery utility but it just reformated my Windows 7 back to factory and never got rid of the dual boot. 
i even selected use entire partition when i seen the option.
Drs305's method got rid of the linux bootloader then i just deleted the partitions but u know what, for some odd reason i believe its still there....do u?!?!
and another thing..... the only reason i wanted use it in the VM is because i like to reformat my PC every 3 - 6 months to keep it running fast
since i just found out on accident that u can reformat the windows partition even if it has a dual boot im going to put linux back on it, i dont know why but i felt like it wasnt possible.
but yeah thanks for all the help and i marked it as solved!
ttyl!

---

### Post by varunendra on 2011-05-08
> **Czvp said:**
> .... as you can probably can tell from the title i  deleted the ubuntu partition from my pc ...... i believe its looking for  the ubuntu bootloader and its not finding it....
> **Czvp said:**
> Hey thanks a lot varunendra but i used drs305's method to the madness and it worked flawlessly! 
The only step i had to add was updating my grub before the lilo command he gave me would actually work.
ummmm.... I'm a bit lost here..
If you had already deleted the linux partitions, how did you manage to successfully update grub?

> **Czvp said:**
> But speaking of ur method, i kind of tried something like that by pressing f10 at the start up and running the system recovery utility but it just reformated my Windows 7 back to factory and never got rid of the dual boot. ..then I doubt if it even touched the MBR. I guess it would have just restored a backup partition image and may be even the partition boot record (PBR) at most. The methods I suggested were meant to restore the MBR.

> **Czvp said:**
> Drs305's method got rid of the linux bootloader then i just deleted the partitions but u know what, for some odd reason i believe its still there....do u?!?!
yeah, you still have it, but lilo this time, not grub! From man page of the lilo command:-
> **-M** master-device [mbr|ext]
[INDENT]Install  a Master Boot Record on the device specified as master- device, selecting the Standard or Extended  Master  Boot  Loader per the option.  ........... If mbr is specified, the Standard Master Boot Loader will **search partitions  1-4  for an active flag, and boot the flagged partition**.......
[/INDENT]
which means it is lilo MBR there that just hands over the boot process to the Windows 'Partition Boot Record' (PBR) in the windows partition. But what's the difference if it is doing the job the way you wanted :). (For more info on lilo command visit: [http://swoolley.org/man.cgi/lilo](http://swoolley.org/man.cgi/lilo))

 > **Czvp said:**
> and another thing..... the only reason i wanted use it in the VM is because i like to reformat my PC every 3 - 6 months to keep it running fast..ah, the everlasting windows issue from ancient days.... :lolflag:

And if you are planning to put linux (ubuntu, right?) back on it, no need to bother with MBR, Grub will take good care of everything.

---

### Post by ubume2 on 2011-05-11
I think there is a rescue tool that will restore your mbr, if you don't have the Windows install disk.

Super Grub Disk

---

