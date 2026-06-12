---
title: "How to make floppy work?"
date: 2009-10-29
forum: General Help
---

### Post by jlh68 on 2009-10-29
I have been trying to get my floppy drive (on my desktop) to work since Ubuntu 8.04 without any success.  I have a floppy drive that the light stays on all the time (yes I have reversed the cable four different ways).  The floppy module is loaned into the kernel.  It does not show in the Places > Computer list.  I even thought the floppy drive was defective and had it exchanged  by the vendor.  I have another desktop with the same problem, so I believe it is a software/operating system problem and not a hardware problem.

I have tried several solutions and none have worked.

I have a bunch of old floppies that I would like to get the data off and burned to a CD-R. 

Does anyone know what I can do to get the floppy drive to work?

---

### Post by P4man on 2009-10-29
Does the light stay on while you are in grub menu ? If it does, then it is a hardware / cable / bios problem. If not, then I got no clue Im afraid.

---

### Post by alphaniner on 2009-10-29
Have you done anything outside of Ubuntu to verify the drive is working?  For example setting your BIOS to boot from the floppy drive?  Even if you don't have a bootable floppy, the drive should be scanned and you should get a 'non-system disk' error if it is working properly.

---

### Post by gdonwallace on 2009-10-29
You might try to unmount the floppy from terminal.  If it will unmount then there may be something else wrong.  If it gives you an error message, then I would suspect that something else is wrong.  I would start with the bios and make sure that it shows the floppy.  Also, have you tried using a different floppy cable?  The actual cable could be the problem.

To unmount the floppy **sudo umount /dev/fd0**  Check the /etc/fstab (you can page this file to find the floppy entry **pg fstab** most distros will label the floppy as /fd0)

---

### Post by jlh68 on 2009-10-29
**gdonwallace** Yes I have tried another cable.  I also have the same problem on a second desktop.  One where the floppy drive worksed with WinXP, until the M/B went south.  I replaced it, installed Ubuntu.

**alphaniner** I will try booting from floppy and see what happens. 

BTW the below is from bg 255651 and I tied it and could only get ot step 4, wher I got an error "Cannot Initialize Device" + "Unable to open any device formatting cannot continue"

> Floppy Activation for Ubuntu 8.10 – 22 Feb 2009 - [email]miketan63@gmail.com[/email] (Windows,Macintosh,Linux)
Run Update Manage - Check – Reboot.
Backup OS.
1. Run (Alt + F2) : gksu gedit /etc/modules
1A. For msdos usage - Add the line :
      floppy
      to the end of the list. Save the file & Close document.
OR
1B. For Linux Native (ext2) usage - Add two lines :
      #To load floppy module
      floppy
      to the end of the list. Save the file & Close document.
1C. Reboot.
2. Run : sudo mkdir floppy0
                 sudo chmod g+rwx floppy0
                 sudo chmod o-rx floppy0
                 sudo modprobe floppy
                 sudo mount /dev/fd0 floppy0
2A. Reboot.
3. Go to Main Menu : System/Administration/Synaptic Package Manger -
     Quick search - type floppy - Check - fdflush / fdutils -
     Mark for Installation - Apply.
3A. Reboot.
4. To launch Floppy Formatter :
     In a Root Terminal , type : sudo gfloppy (enter)
     (To display Root Terminal, Go to Main Menu :
     System/Preferences/Main Menu/System Tools -
     Check – Root Terminal – Close)
5. To mount floppy : Right Click on Floppy Drive - Mount Volume -
     in Nautilus (File Browser).
     Do not use Double Click.
     To open floppy : Double Click or Right Click - Open.
5A. Unmount floppy after use.
6. Formatting works perfectly on good quality floppy but not
     for Standard & Thorough on degraded floppy from the above command
     executed from a Clean Registry. Previous handled command from user
     may corrupt registry.
7. Reboot if floppy unable to mount or fail.
8. Floppy activated successfully with full read & write access plus
     formatting. 

---

### Post by jlh68 on 2009-11-06
I tried Puppy Linux on my very old Toshiba laptop that has a floppy drive.  Puppy recognized the floppy and accessed files.  (Win98, 96MB Ram P-III)

I then tried Puppy on my desktop and it could not access the floppy.  It did know a floppy was present.

I have checked the BIOS as to floppy operation. 

That leads me to believe that maybe there is a conflict with the motherboard and the floppy drive, or that the two Linux distros both have a problem with the floppy access.

---

