---
title: "Make an external drive bootable"
date: 2012-08-23
forum: General Help
---

### Post by Cotopaxi on 2012-08-23
**[COLOR="Navy"]WARNING: For safety reasons plase DO NOT follow this "tutorial" yet! Please read the post #4 from YannBuntu, who is the creator of "Boot-Repair"![/COLOR]**

The reason for writing this thread is that I have been tweaking around for a fortnight trying to make an external drive bootable and finally made it work, so here I go.

1) Change the boot order of your computer's BIOS:
The boot order of the BIOS of the computer must be set to boot FIRST from USB devices, CD ROM, whatever. When the external drive is not connected to the computer the BIOS does not find any external drive and boots the computer from the main hard disk (the normal way).

2) Check that Boot Repair is installed:
In Ubuntu 12.04 it is already installed, for older versions it should be in the repos. The name of the file is &#8220;boot-repair&#8221;

3) Boot the computer with the external drive CONNECTED to it.
You are still booting the operative system of your computer's hard drive.

4) Open Boot Repair
Boot Repair will ask you if you want to update the software. You choose. Now, in the main window:

5) Select &#8220;Advanced Options&#8221;
this is in the lower left corner of the window.

6) Click the check-box &#8220;Reinstall GRUB&#8221;
Now the two tabs &#8220;GRUB location&#8221; & &#8220;GRUB options&#8221; become selectable.

7) Select the tab &#8220;GRUB location&#8221;
You now see a menu &#8220;OS to boot by default:&#8221; this menu displays the Operative System installed in the main hard drive of your computer. DO NOT change anything here!

Now click on the check-box &#8220;Separate /boot partition&#8221;. The pulldown menu should present you the partition with the operative system of your external drive. In my case it displays &#8220;sdb5 Ubuntu 12.04.1&#8221;. Select this option.


8.) Return to the tab &#8220;Main options&#8221;
Click on the check-box &#8220;Unhide boot menu&#8221;. Feel free to vary the number of seconds you want the boot menu to be displayed.

9) Click on the button &#8220;Apply&#8221;
And you are done!

10) Click on the button &#8220;Quit&#8221;
to abandon Boot Repair.

11) Reboot your system keeping the external drive CONNECTED.
The top option is highlighted and this is the OS of your main hard drive.
As soon as you press the down key, the counter stops counting.
Your external drive should now be presented under &#8220;Previous Linux versions&#8221;, in my case it presents:
&#8220;Ubuntu, with Linux 3.2.0-23-generic (on /dev/sdb5)."

Hopefully I am helping anyone! ):P

---

### Post by Cotopaxi on 2012-08-24
Sorry, Boot repair is in a specific repository, to install it see this post:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Sorry about this one!

---

### Post by Atitudes on 2012-08-24
Nice, thank you :D Just one noobish question, can we perform the same using the recovery mode? I encountered some troubles a month ago and it could have been solved easily...

---

### Post by YannBuntu on 2012-08-24
Hello Cotopaxi,
First of all, thanks for sharing your experience and knowledge, this is the soul of FOSS ;)
However, I am the developer of Boot-Repair, and I fear that your tutorial may not be suitable for other people. (or worse: it could damage their boot)
To be sure I understand what you have done, please could you indicate your [Boot-Info URL]("https://help.ubuntu.com/community/Boot-Info") ?

---

### Post by Cotopaxi on 2012-08-24
Hi YannBuntu

I hope I am doing it right:

[http://paste.ubuntu.com/1165258/]("http://paste.ubuntu.com/1165258/")

---

### Post by Cotopaxi on 2012-08-24
YannBuntu,

This is again the Boot-Info URL generated with the external Harddrive CONNECTED to the Laptop.

I hope it helps.

[http://paste.ubuntu.com/1165269/]("http://paste.ubuntu.com/1165269/")

---

### Post by Cotopaxi on 2012-08-25
Atitudes,

Sorry for my late reply, the post of YannBuntu kept me quite busy.

Atitudes, please DO NOT try anything at the moment, my "tutorial" might not be a help, but could be the killer of your system!

Let's just wait until YannBuntu gives us his feedback.

;)

---

### Post by Cotopaxi on 2012-08-27
Yann,

Do you need any more information from me?

Feel free to ask!

And a security question: Should I delete the whole post, for safety reasons?

Thanks!

---

### Post by YannBuntu on 2012-08-27
Hello Cotopaxi,


**- I confirm the procedure you used is not a procedure to make an external drive bootable.** It is indeed a procedure to move the /boot partition of the HDD system onto the external drive, which should normally lead to a situation where the PC can't boot if the external drive is disconnected.

**- the current situation of your PC is different from the situation that should have resulted after following the procedure** in post#1, because your HDD system doesn't use any separate /boot. So either this is a mistake in the procedure, or a bug of B-R, or something was changed after you followed the procedure. To be sure, please run Boot-Repair, click "Advanced options", click the "Backup" button, save the ZIP file somewhere, then attach it to your reply, or send it to me by email (yannubuntu ATT gmail DOTT com).

**- AFAIK, the standard procedure for making an external drive bootable** is:
1) install Ubuntu on the external drive
2) place its GRUB on the external drive:
  - into its MBR in case of standard non-EFI BIOS
  - into an EFI partition if EFI BIOS
3) make the BIOS boot on it.

**- My guess of what happened:** Your computer is EFI-type, and you first installed an Ubuntu n°1 in your HDD (which created an EFI partition on your HDD: on sda1). When you installed Ubuntu n°2 in your external drive, it replaced the GRUB n°1 by the GRUB of Ubuntu n°2. At this moment, I guess your problem was that you couldn't boot Ubuntu n°1 when the external drive was disconnected, wasn't it? So you used Boot-Repair to reinstall the GRUB of Ubuntu n°1, and now you can access Ubuntu n°1 even when the external drive is disconnected, can't you?


I'll ask a moderator to change the title to: "[EFI] Installing Ubuntu1 on HDD + Ubuntu2 on external drive"

---

### Post by Elfy on 2012-08-27
This is not the place for tutorials. 

Closed

---

