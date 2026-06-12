---
title: "segmentation fualts on multiple programs"
date: 2010-05-25
forum: General Help
---

### Post by notesetter on 2010-05-25
I'm getting a lot of problems with segmentation faults when opening or using various programs in 10.04 (new install)

I've experienced problems with:
Firefox (from repositories)
Thunderbird (from repositories)
OpenOffice (from official OOo debs)
Transcribe! (manual install of executable binary)
Synaptic

I'm running a fresh install of Ubuntu 10.04 on a Compaq us2170 laptop. I'm running desktop effects/compiz.

Typically, a program will crash or fail to start when launched from the Applications menu or AWN. When I try starting from the command line, I get the "segmentation fault" notification.

Also, OpenOffice gave me a message about not being able to determine the language of the interface.

Restarting the computer or reinstalling packages temporarily fixes the problem. I've never encountered this much instability in a Ubuntu release before.

Anyone else encountering these problems?

Thanks,

David

---

### Post by notesetter on 2010-05-27
Update:

I've uninstalled OpenOffice and installed the official version from the repositories. I'm still getting crashes with that program.

I've uninstalled the official repository version of Thunderbird and manually installed Mozilla's binary. So far, no problems.

Last night, trying to start synaptic from a terminal, I got the message "segmentation faulty tree." (I was trying to uninstall Thunderbird.) I did ```
sudo apt-get install --reinstall synaptic
``` After that, Synaptic started fine from the terminal and I was able to uninstall Thunderbird.

This morning, after ```
sudo atp-get update && sudo apt-get upgrade
``` I did ```
sudo apt-get clean
``` I got a strange warning about a locked ~/tmp file. Incidentally, I couldn't save work in Scribus or OOo. I had to discard my work and reboot. Scribus is working fine now, but OOo crashes while trying to recover documents and consequently won't open.

I don't want to abandon this installation, but I need to be able to work without rebooting several times a day.:confused:

---

### Post by notesetter on 2010-05-27
I just received this wonderful message from a terminal while trying to start openoffice ```
david@lucid-laptop:~$ openoffice.org 
Inconsistency detected by ld.so: ../sysdeps/i386/dl-machine.h: 640: elf_machine_rel_relative: Assertion `((reloc->r_info) & 0xff) == 8' failed!
david@lucid-laptop:~$ 

```

---

### Post by wavded on 2010-05-29
I can totally relate, I'm having similar issues but with Banshee on Lucid 10.04.

```
Inconsistency detected by ld.so: ../sysdeps/i386/dl-machine.h: 640: elf_machine_rel_relative: Assertion `((reloc->r_info) & 0xff) == 8' failed!
```

---

