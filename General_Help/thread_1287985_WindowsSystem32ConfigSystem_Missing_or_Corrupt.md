---
title: "Windows/System32/Config/System Missing or Corrupt"
date: 2009-10-10
forum: General Help
---

### Post by adai2020 on 2009-10-10
Hi,

Firstly, i have a Lenovo T60 Thinkpad laptop which came preinstalled with Windows XP. For one of my courseworks in university, i then dual installed Ubuntu 9.04 using the WUBI - Windows Installer. Note: WUBI Windows Installer together with the Ubuntu installed can be easily uninstalled if it is not required just like normal Windows applications. Thus i had a laptop which could dual boot into either Windows XP or Ubuntu 9.04. Everything was fine with Ubuntu and Windows XP and the dual boot option also worked fine.

Recently when i tried to start up my computer and chose the Windows XP option to boot, on the boot up screen it showed me the following message:

Windows/System32/Config/System Missing or Corrupt

I could not boot into my Windows XP anymore but i can successfully boot into my Ubuntu 9.04 by choosing the Ubuntu boot up option. I am currently using Ubuntu in my laptop to access internet and even to type out this message. 

From my Ubuntu operating system, i am actually able to access to my C drive where Windows XP is installed. I can access my C and D Drive and hence access all the files in C and D drive which is also where Windows XP is installed in my computer. I have already made a full backup of the entire C and D drive. Thus i am now prepared to try any new method to solve the problem as i have no fear of loss of data.

1) Is it somehow possible to repair the missing or corrupt file without having to reinstall and reformat the entire Windows XP installation again ? 

2) Is it possible to just repair the corrupt file without loosing all data stored in C drive by using the available access to C drive through Ubuntu 9.04?

3) What are the options that are currently available to me to rectify this problem ?

4) I dont mind loosing or erasing my Ubuntu 9.04 OS in the attempt to rectify my Windows boot up problem as i have nothing important stored in my Ubuntu as of now and all important data has already been backed up anyway. If Ubuntu will be affected during the repair procedure, it doesn't matter as i will just reinstall my Ubuntu when the computer or Windows is working. 

5) Is it possible to somehow repair the Windows boot up problem without loosing all my data stored in the C drive ?

The recovery CD that was supplied together with my laptop only allows me to erase everything in my hard drive, reformat and reinstall everything. No other option is given by the Recovery CD that came together with my Lenovo Thinkpad laptop. I want to try all possible methods to recover my Windows without deleting all the data and program files stored in my computer. I am intending to only opt for a full erase, reofrmat and reinstall as the last option available. Therefore i am seeking out other options available here to me.

Any help will be great.

Thanks,
Adai.

---

### Post by skatinjj on 2009-10-10
You should be able to copy a new version of that file over to your XP installation from ubuntu using your cd.

Search the cd for the file system and copy it over to the path shown in the error message.

---

### Post by adai2020 on 2009-10-10
I am unable to find the system/config file from the given Recovery CD from Lenovo. In fact the recovery CD comes in a set of 9 CD's which i am supposed to insert one after another to reinstall the entire system.

But even after going through the CD's i cannot seem to find any file named system/config.

Can you provide any alternatives for me to find the system/config file ?

---

### Post by skatinjj on 2009-10-10
> **adai2020 said:**
> I am unable to find the system/config file from the given Recovery CD from Lenovo. In fact the recovery CD comes in a set of 9 CD's which i am supposed to insert one after another to reinstall the entire system.

But even after going through the CD's i cannot seem to find any file named system/config.

Can you provide any alternatives for me to find the system/config file ?

Is there a way you can boot into the recovery console?

---

### Post by adai2020 on 2009-10-10
I first used the recovery CD that came together with my laptop. But the recovery CD only gave one option which is to reformat and reinstall the entire drive.Hence i did not use the cd which came together with my laptop.

Thus, i then just used a normal Windows XP CD meant for other computers from oher people. I used the Windows XP Setup CD, the first Windows Setup page appeared. I then pressed the key 'R' to choose the option that stated 'To repair Windows XP installation using Rceovery Console, press R'.

After that i received a blue screen with the following message on it:
[I]"Setup did not find any hard disk drives installed in your computer.

Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk related hardware configuration is correct. This may involve running a manufacturer supplied diagnostic or setup program

Setup cannot continue. To quit Setup, Press F3."

[/I]
The only option given to me was to quit setup as you can see from the above message. Hence i quit the setup program by pressing F3. Thus i am unable to boot into a recovery console.

---

