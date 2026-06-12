---
title: "Dual Booting Windows 7 and Ubuntu"
date: 2011-08-23
forum: General Help
---

### Post by worlddlck on 2011-08-23
Hello, i've just trying to install ubuntu

I am using windows 7 , and i am trying to dual boot windows 7 and ubuntu

After the installation done in windows 7 , i followed the instructions that restart my computer, but still after restart , there is only JoliOS and Windows 7 but Ubuntu...

What can i do?

*i cant uninstall ubuntu on my windows 7 
Here is the error message:
Error executing command
>>command=C:\windows\system32\bcedit.exe /delete
{54af256d-1855-11e0-bcb8-c4669a0cdfea} /f
>>retval=1
>>stderr=An error occured while attempting to delete the specified entry.
The system cannot find the file specified

>stdout=

For More information, please see the log file:
C>\users\dickso~1\appdata\local\temp\wubi-11.04-rev211.log

Please help me =(
Thanks~

---

### Post by bcbc on 2011-08-23
Looks like wubi failed to get the boot entry in bcdedit and that's what's preventing the uninstall.

Either add boot entry using this: [http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/) if you want to get it booting,

or use the manual uninstall instructions here: [https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F]("https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F")

---

### Post by Mark Phelps on 2011-08-24
We've seen this problem with Wubi before when the Win7 BCD is not on the partition that Wubi presumes.  This is OK for Windows because it's MBR will point to the proper partition, but it appears to give Wubi a real problem.

I've gone through the Wubi documentation and there does not appear to be a parameter to tell Wubi which partition contains the BCD.

If you fix this, please post the solution back here so we can share that with others.  THANKS

---

