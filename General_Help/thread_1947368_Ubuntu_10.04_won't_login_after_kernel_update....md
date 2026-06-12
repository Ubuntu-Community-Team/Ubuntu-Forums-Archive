---
title: "Ubuntu 10.04 won't login after kernel update..."
date: 2012-03-26
forum: General Help
---

### Post by stargatefan on 2012-03-26
Hello,

I own a Dell studio 1535.

I recently ran my update manager, and it installed the 2.6.32-40 kernel (previously 2.6.32-39). After the update I restarted my computer like normal, but it wouldn't pull up the session login page.

It played the "bongo" sound, but it was just the purple screen. No panel at the bottom, and I was unable to use my mouse (my touchpad worked though if that helps).

I am currently using my windows partitioned because the same thing happened when I selected earlier kernels at the boot menu. 

Thank You for your assistance.

---

### Post by imachavel on 2012-03-26
one of two ways to try and solve this, put in the live cd, boot to it and look for a kernel repair option, if it doesn't exist, can you get to grub or will the hdd not boot at all? If you can get to grub, and get into a terminal session, try this command:

sudo apt-get update && sudo apt-get dist-upgrade

or could you boot the live cd, google how to run boot repair, should be in software center. Then create a grub script, but how will this help with a failed kernel? I doubt you can even get into the command line recovery mode. What a doozy, I'm going to wrack my brain but this is kind of a hands on thing to try and approach.

What purpose do you use the computer for, is it an emergency? Is it for your own office or for a client, if it's for a client I'd guess you have the option to take out the drive, back up all the files, then completely reformat and reinstall the OS, if you understand the procedure.

OR PERHAPS, I didn't think of this, sometimes grub will give you an older kernel version to boot to, but it's not guaranteed to work

---

### Post by stargatefan on 2012-03-26
Thanks for the response.

I'm not sure why, but it works fine when I disconnect all USB devices(phone, mouse, external HD) prior to booting up.

---

### Post by Johnny M! on 2012-03-26
Very Similar Problem with the System Update that grabbed the new Kernel 2.6.32-40.

Please see:

[http://ubuntuforums.org/showthread.php?p=11795469#post11795469](http://ubuntuforums.org/showthread.php?p=11795469#post11795469)


BVR
Johnny M!
:guitar:

---

