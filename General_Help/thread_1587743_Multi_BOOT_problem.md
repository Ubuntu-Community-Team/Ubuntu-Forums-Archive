---
title: "Multi BOOT problem"
date: 2010-10-04
forum: General Help
---

### Post by ehsanulamin on 2010-10-04
Hello Everyone.
I was trying to use UBUNTU in my Toshiba Laptop L510.
But after it Installed in my hard disk it did't start the operating system.
I tryed lot of time. But when UBUNTU boot showing it Starting UBUNTU ICON the Screen goes BLACK.


Anyways... I want solution with [GNU *GRUB boot loader.*]("http://www.gnu.org/software/grub/manual/grub.html")

I want to make my Microsoft Windows 7 Default as a operating system.
How can I do that without Entering into UBUNTU's Main System... by using command.
Please someone give me a step by step help. i really appreciate your help.. thx


NOTE: I have the UBUNTU 9.10 CD.  
[ ]("http://www.gnu.org/software/grub/manual/grub.html")

---

### Post by ehsanulamin on 2010-10-04
[B]Multi BOOT problem

[/B]
 
                                                                Hello Everyone.
I was trying to use UBUNTU in my Toshiba Laptop L510.
But after it was Installed in my hard disk it did't start the operating system.
I tryed lot of time. But when UBUNTU boots... it showing The UBUNTU ICON then Screen goes BLACK.


Anyways... I want solution with [GNU *GRUB boot loader.*]("http://www.gnu.org/software/grub/manual/grub.html")

I want to make my Microsoft Windows 7 Default as a operating system.
How can I do that without Entering into UBUNTU's Main System... by using command.
Please someone give me a step by step help. i really appreciate your help.. thx



NOTE: I have the UBUNTU 9.10 CD.

---

### Post by sikander3786 on 2010-10-04
For changing the default Operating System, you'll need to edit Grub.cfg, donot directly edit it but edit /etc/default/grub and then run update-grub from a terminal and update your Grub.cfg file and that could be done either by booting the installed Ubuntu or via a Live CD (this will be a little more time consuming/difficult). I don't think there is a way of changing it without booting the system.

You've got an Intel Graphics Chipset? For the screen going black, you need to edit the Grub Menu entry a bit. When the computer starts, press 'e' on the first entry in Grub Menu. Using arrow keys, navigate to "quiet and splash" delete them and type the term "nomodeset" in their place. Press Ctrl + X to boot.

If that was unsuccessful, type "i915.modeset=0 xforcevesa" in place of "quiet and splash" and continue with the boot.

And if successful, you can install startupmanager and choose your default OS, the easy way. Type in a terminal, Application > Accessories > Terminal

```
sudo apt-get install startupmanager
```

You can also install it via the Software Center under Applications menu.

Start it from System > Administration > StartUp-Manger.

---

### Post by dcstar on 2010-10-04
> **ehsanulamin said:**
> [B]Multi BOOT problem

[/B]
 
                                                                Hello Everyone.
I was trying to use UBUNTU in my Toshiba Laptop L510.
But after it was Installed in my hard disk it did't start the operating system.
I tryed lot of time. But when UBUNTU boots... it showing The UBUNTU ICON then Screen goes BLACK.


Anyways... I want solution with [GNU *GRUB boot loader.*]("http://www.gnu.org/software/grub/manual/grub.html")

I want to make my Microsoft Windows 7 Default as a operating system.
How can I do that without Entering into UBUNTU's Main System... by using command.
Please someone give me a step by step help. i really appreciate your help.. thx



NOTE: I have the UBUNTU 9.10 CD.

You need to hold the SHIFT key down as it boots to bring up the Grub menu, then you can select a Recovery boot to get into the Ubuntu system in basic graphics mode.

Once there you can then try and track down why you don't see your system boot up correctly - it may be a simple graphics problem.

---

### Post by ehsanulamin on 2010-10-04
> **dcstar said:**
> You need to hold the SHIFT key down as it boots to bring up the Grub menu, then you can select a Recovery boot to get into the Ubuntu system in basic graphics mode.

Once there you can then try and track down why you don't see your system boot up correctly - it may be a simple graphics problem.
I have solve the Default Operating System selection and it's Time by Command Promt without loading main UBUNTU system. Because my UBUNTU system is not still running.. So I have to go all the way through command promt. :)

Anyway i'm happy that i have solved it by my self.

I'll  let you know the step in my next post.


Thanks DCstar... at least you respond to my asking. Thx :)

---

### Post by ehsanulamin on 2010-10-04
I have solve the Default Operating System selection and it's Time by  Command Promt without loading main UBUNTU system. Because my UBUNTU  system is not still running.. So I have to go all the way through  command promt. :smile:

Anyway i'm happy that i have solved it by my self.

I'll  let you know the step in my next post.


Thanks Sikander... at least you respond to my asking. Thx :smile:

---

### Post by ehsanulamin on 2010-10-04
Select UBUNTU recovery mode from the boot menu. Now after it load you will get the option to select “Normal”.  Open as Normal. After it load as normal… it will ask ur user ID and Password.
  Enter the appropriate password. Then you will get the command Prompt. In command prompt type 
  “df –h” to see the drives of your system. Unless just skip the step. Type “cd /dev”  to go to your Hard Disk’s root drive. [Now if you want to see the directories and files you can type “dir”.] type “cd boot” to go to boot folder. There you have to go to grub folder. Type “cd grub” to go to grub folder. In this folder there is a CFG file named “grub.cfg”. Now what you have to do is…. You have to edit the “grub.cfg”. But Remember Changing the Vales there without understanding can let your system not to boot.
   
  Ok… Now you can edit this files with a little editor in UBUNTU command prompt. It’s call Nano.
  Now Type “sudo nano grub.cfg”. it will show you the contain of the file. Now here you will find a line at the Beginning 4 or 5 line later…. Set default = “0”. Here you have to change the 0 value to other value that is what your desire operating systems number in the boot menu. 
  For Example if your Operating system is Windows 7 and it is the 5 numbers in the boot menu then you have to change value to 4. Cause it start with 0.
  Now if you all so want to change time before boot default operating system… then search some next line downward. You will see “timeout = 10”. Change it to your desire second you want.
  Now time to save the “grub.cfg”. press CTRL+X and you will be asking to save the file. Type Y to save and N  to Not save. After entering Y for saving press Enter once more to save it as before as “grub.cfg”.
  Just Restart the Computer to see the Change.
  Thank you everyone.:guitar::)

---

### Post by ehsanulamin on 2010-10-04
Select UBUNTU recovery mode from the boot menu. Now after it load you will get the option to select “Normal”.  Open as Normal. After it load as normal… it will ask ur user ID and Password.
  Enter the appropriate password. Then you will get the command Prompt. In command prompt type 
  “df –h” to see the drives of your system. Unless just skip the step. Type “cd /dev”  to go to your Hard Disk’s root drive. [Now if you want to see the directories and files you can type “dir”.] type “cd boot” to go to boot folder. There you have to go to grub folder. Type “cd grub” to go to grub folder. In this folder there is a CFG file named “grub.cfg”. Now what you have to do is…. You have to edit the “grub.cfg”. But Remember Changing the Vales there without understanding can let your system not to boot.
   
  Ok… Now you can edit this files with a little editor in UBUNTU command prompt. It’s call Nano.
  Now Type “sudo nano grub.cfg”. it will show you the contain of the file. Now here you will find a line at the Beginning 4 or 5 line later…. Set default = “0”. Here you have to change the 0 value to other value that is what your desire operating systems number in the boot menu. 
  For Example if your Operating system is Windows 7 and it is the 5 numbers in the boot menu then you have to change value to 4. Cause it start with 0.
  Now if you all so want to change time before boot default operating system… then search some next line downward. You will see “timeout = 10”. Change it to your desire second you want.
  Now time to save the “grub.cfg”. press CTRL+X and you will be asking to save the file. Type Y to save and N  to Not save. After entering Y for saving press Enter once more to save it as before as “grub.cfg”.
  Just Restart the Computer to see the Change.
  Thank you everyone.:guitar:

---

### Post by Mark Phelps on 2010-10-04
Your solution is temporary at best.

I'm shocked that ANYONE would suggest editing the grub.cfg file.  You'd think the text there telling folks NOT to edit it would make sense at least to some folks!

The next time you do a routine kernel update, that file gets rewritten -- you have no control over that -- and your hand-edited changes are GONE.

To change the startup order, the easiest way is to install startup-manager, start it, and use the pull-down to select the GRUB entry to be the default.

---

### Post by Mark Phelps on 2010-10-04
Unless there's some glitch in the forum software, this is the THIRD post you've made on the same topic.

Multi-posting is against forum rules.  Please do no multi-post anymore.

Thanks

---

### Post by CharlesA on 2010-10-04
Threads merged.

@OP: Please don't cross post (post more then one in different forums.)

Thanks.

---

