---
title: "64 bit installation inside 32bit Xp"
date: 2009-10-15
forum: General Help
---

### Post by Adi100 on 2009-10-15
Greetings to all.

I am absolute beginner to Ubuntu, i have used UNIX to some extent in my college days.Basically I like Windows( I  still remember creepy vi editor), But now wanted to try Linux.

MY System configuration is Core2Duo Intel 946GZ MB 1 GB RAM Which is capabel of running 64 bit OS.

I have downloaded 64 bit version(Ubuntu 8.04), I have certain doubts which can only be answered by a users who have used linux for some time.

They are:

- I do not want to damage my windows installation It take lot of time reinstall all updates and patches.

-Does running Ubuntu from Live CD and saving to hard disk will result in corrupt NTFS?
  ( NTFS is a secret maintained by MS)?

-can I use Wubi to install 64 bit Ubuntu on a 32 bit Xp plateform.?

- Does Ubuntu runs in Aa virtual machine( Internet search didnot helped much).?

- my system can boot from CD/DVD do I need to use the option  provided on installer 
CD ( to boot from CD).?

- does it modifies my bootloader (Ntldr) or simply modifies boot.ini
or it writes a new MBR if Wubi is used.?

-Can i still use my windows backup programs to backup the folder in wchich linux was installed as usual or it is locked by some process while windows is running.?

- Presumably it is installed( copied over NTFS) program installed when running UBUNTU will use underlying NTFS, Can my underlying File system be corrupted ?


- does Files created in windows copied over flashDrive or Cd/DVD( example doc (using openoffice)file and Pdf files ) be opened on Linux, or file interchange is not possible.

I request the experienced community here to help me clearing my doubts.


Regards

Adi

---

### Post by kanikilu on 2009-10-15
> **Adi100 said:**
> - I do not want to damage my windows installation It take lot of time reinstall all updates and patches. This isn't really a question, so there's not much to answer with, but anyting can happen. I would recommend doing a backup before doing anything more than trying the Live CD.

> -Does running Ubuntu from Live CD and saving to hard disk will result in corrupt NTFS?
  ( NTFS is a secret maintained by MS)? Writing to NTFS is pretty stable, but there is always a risk...

> -can I use Wubi to install 64 bit Ubuntu on a 32 bit Xp plateform.? The Wubi FAQ covers that: [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

> - Does Ubuntu runs in Aa virtual machine( Internet search didnot helped much).? Yes. I personally use VirtualBox: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox) I'm not positive, but you may have to use the 32 bit version if you're using it as a guest OS in VBox or VMWare (someone correct me if I'm wrong).

> - my system can boot from CD/DVD do I need to use the option  provided on installer 
CD ( to boot from CD).? I'm not sure what you mean by this :confused: Just let your system boot from the optical drive...

> - does it modifies my bootloader (Ntldr) or simply modifies boot.ini
or it writes a new MBR if Wubi is used.? Depends on the installation method. I believe Wubi modifies the boot.ini, a dualboot setup will change the MBR.


> -Can i still use my windows backup programs to backup the folder in wchich linux was installed as usual or it is locked by some process while windows is running.? I'm assuming you are referring to Wubi again? If so, I'm not sure, you might check their site. If virtualized, then yes, you can backup the virtual hard drive file.

> - Presumably it is installed( copied over NTFS) program installed when running UBUNTU will use underlying NTFS, Can my underlying File system be corrupted ? Sorry, you lost me there. Can you clarify or rephrase the question? Can something happen to your Windows installation in a dual-boot or Wubi setup? Sure, anything can happen. Is it likely? Not really, as long as you're careful.

> - does Files created in windows copied over flashDrive or Cd/DVD( example doc (using openoffice)file and Pdf files ) be opened on Linux, or file interchange is not possible. It depends on the file. A TXT file in Notepad will work find. A document created in Word should work as well. A DRM'ed TV show from iTunes? Not so much...

I think you need to do a little more research and figure out which method of trying Ubuntu is best for you:

- Live CD: Easiest method. Very unlikely anything will happen to your Windows installation, unless you mount that partition and start trying to write to it...

- Wubi: Easy to setup and remove, but requires a reboot to get from Windows to Ubuntu.

- Dual-boot: Makes changes to your MBR, so is not as easy to remove, and if you don't know what you are doing and select some options in the installer, can overwrite Windows.

- Virtualization: Not necessarily as easy to setup as Wubi, but is just as easy, if not easier to remove. It's also very unlikely anything will happen to Windows. It's the only method that will let you run Ubuntu "inside" Windows, not requiring a reboot to use each OS.

---

### Post by Adi100 on 2009-10-16
Thank you Kanikuli for your help and time.

I would go for LiveCD and virtualization for getting comfortable on Linux.

I think i have to download 32 bit version and I am reading ubuntu pdf guide how to go for virtualization.

Thank you once again.

Regards

Adi

---

