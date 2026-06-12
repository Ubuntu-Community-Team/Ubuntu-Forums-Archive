---
title: "Registry and INI files - Confused!"
date: 2010-10-24
forum: General Help
---

### Post by 0000_soldier on 2010-10-24
Hey Gents and Ladies,

I was just doing a little reading on win2k registry and it has been used to improve INI file concept, I was wondering, does linux have some kinda registry or is it just files, because poking around the structure is as follows:

 / root
home - 
          --users
/etc
/opt
/mnt
/dev
/cdrom
/root
/sys
  ... you get the idea, can anyone please give me a brief overview of styles of how linux manages settings compared to the windows version concept or are they the same?

Thanx sorry if this question is a bit dumb :confused: any information about Ini and registry will help

---

### Post by cpmman on 2010-10-24
The registry and INI files are a Windows concept which as far as I know are unique to Windows based on msdos.  Linux was developed as a secure system where only root has complete control.  Ubuntu was developed with root as a superuser.  The normal method of using superuser powers is to use the sudo command and supply your own password if you have administrative privileges.  Individual programmes use .config files in linux which serve a similar purpose to INI files.  There is no registry - the installation security does not need it.

---

### Post by matt_symes on 2010-10-24
Hi

Linux uses both. However all of your _local_ settings are stored  in your home directory ~/ (ls -al). _System_ settings (as a general rule) are stored in /etc (cat <filename>). A much better way of doing things.

Kind regards

---

### Post by 0000_soldier on 2010-10-25
So Linux does not have an equivilant of "regedit"?

---

### Post by matt_symes on 2010-10-25
Hi

Not really no (regedit). You can use vi, emacs, nano or gedit (or many others) to edit most config files.
Have a look at gconf-editor also.

Remember Linux is not windows.

Kind regards

---

### Post by 0000_soldier on 2010-10-25
Thank you i have a starting point

---

