---
title: "Error mounting partition when booting"
date: 2010-06-30
forum: General Help
---

### Post by Selleen rane on 2010-06-30
Changed sda6 to mount when loading, but the drive is ntfs and so when i changed the name in Windows it now gives the error "Can not mount /media/Documents" when i boot into Ubuntu. How do I remove that entry so I don't get that error anymore.

---

### Post by dino99 on 2010-06-30
use mountmanager to set your prefs (search into synaptic)

---

### Post by Selleen rane on 2010-06-30
Already tried that to fix the loading of the drive as with changing the name the system would not recognize it. So got that corrected now the drives mounts properly but it still gives me that error on boot, i need to know how to remove that line from the startup file

---

### Post by Morbius1 on 2010-06-30
Why not post your fstab?

```
cat /etc/fstab
```

---

### Post by Selleen rane on 2010-06-30
UUID=A6C8B400C8B3CD35 /media/Windows 7 ntfs-3g defaults 0 0
UUID=660CBEF40CBEBE7D /media/sda1 ntfs-3g defaults 0 0
UUID=A6C8B400C8B3CD35 /media/sda2 ntfs-3g defaults 0 0
UUID=612f9254-8674-410b-aea7-90d10e2f7101 / ext2 defaults 0 1
UUID=4922f7a4-9244-475e-a8ae-c7fc9cfd0501 swap swap sw 0 0
UUID=83D0D2A9BBD75640 /media/Documents ntfs-3g defaults 0 0

I assume it is the last entry but i am not seeing the new name or entry but the system still auto mounts the drives

---

### Post by dabl on 2010-06-30
> **Selleen rane said:**
> 

when i changed the name in Windows 



What does this mean?  Changed what name?

Did you do anything that would have changed the UUID of the partition?  You can check that in Ubuntu with ```
sudo blkid
```

The UUID needs to match the one shown in the /etc/fstab line for that partition.

---

### Post by Morbius1 on 2010-06-30
Didn't understand your last comment. Which is sda6?

You could also post the output of this command:
```
sudo blkid -c /dev/null
```

---

### Post by Selleen rane on 2010-06-30
Sorry with changed it in windows i am meaning that i changed the name of the drive because i can not do that to an NTFS drive in ubuntu 

here is the report
/dev/sda1: LABEL="System Reserved" UUID="660CBEF40CBEBE7D" TYPE="ntfs" 
/dev/sda2: LABEL="Windows 7" UUID="A6C8B400C8B3CD35" TYPE="ntfs" 
/dev/sda3: UUID="612f9254-8674-410b-aea7-90d10e2f7101" TYPE="ext2" 
/dev/sda5: UUID="4922f7a4-9244-475e-a8ae-c7fc9cfd0501" TYPE="swap" 
/dev/sda6: LABEL="Games" UUID="83D0D2A9BBD75640" TYPE="ntfs" 
/dev/sdb1: LABEL="1.5 Tb Backup Drive" UUID="384CEA464CE9FE8E" TYPE="ntfs"

---

### Post by Morbius1 on 2010-06-30
(1) Did you by any chance delete /media/Documents ? 
I don't see anything wrong with this:
>  UUID=83D0D2A9BBD75640 /media/Documents ntfs-3g defaults 0 0Bit if /media/Documents is now gone it will not mount - just a guess.

(2) You have the same partition mounted twice:
        > [COLOR=Blue]UUID=A6C8B400C8B3CD35[/COLOR] /media/Windows 7 ntfs-3g defaults 0 0
[COLOR=Blue]UUID=A6C8B400C8B3CD35[/COLOR] /media/sda2 ntfs-3g defaults 0 0You might want to put a # in front of the one you don't want. For Example:
```
#UUID=A6C8B400C8B3CD35 /media/Windows 7 ntfs-3g  defaults 0 0
```

---

### Post by Selleen rane on 2010-06-30
Nope did not delete /media/documents, documents used to be the name of the drive and it has been changed to games thats what made the problem worse, i used mount manager to reset the info about the drive and then it could be mounted normally inside Ubuntu but kept getting that boot error. 
I will try and ignore those 2 lines and see what happens be right back and thank you very much

---

### Post by Morbius1 on 2010-06-30
(1) Did you by any chance delete /media/Documents ? 
I don't see anything wrong with this:
>  UUID=83D0D2A9BBD75640 /media/Documents ntfs-3g defaults 0 0Bit if /media/Documents is now gone it will not mount - just a guess.

(2) You have the same partition mounted twice:
        > [COLOR=Blue]UUID=A6C8B400C8B3CD35[/COLOR] /media/Windows 7 ntfs-3g defaults 0 0
[COLOR=Blue]UUID=A6C8B400C8B3CD35[/COLOR] /media/sda2 ntfs-3g defaults 0 0You might want to put a # in front of the one you don't want. For Example:
```
#UUID=A6C8B400C8B3CD35 /media/Windows 7 ntfs-3g  defaults 0 0
```

[COLOR=Blue]EDIT: Actually you have to put a # in front of that line. You can't have a space between "windows" and "7" - at least not the way you did it.[/COLOR]

---

### Post by Selleen rane on 2010-06-30
Ok I feel like such a noob when I am really am not, but how to I get access to the edit fstab file?

Sorry been about 10 years since I have used Linux so I know I am very very Rusty here, thanks for your patience.

---

### Post by Selleen rane on 2010-06-30
Actually i did not add the space mount manager would have as i have never manually edited the file hence why i am asking how to :S

---

### Post by dabl on 2010-06-30
> **Selleen rane said:**
> 

 how to I get access to the edit fstab file?

Alt-F2 "gksudo gedit /etc/fstab"

will open it for editing.



But I think Morbius1 is right about the space in "Windows 7" -- that's a no-no.  You have to change that.  In a terminal window

```
sudo mkdir -p /media/windows_7
```

Then when you are editing /etc/fstab, change that mount point to match the new one, and it should work after you reboot the PC.

---

### Post by Selleen rane on 2010-06-30
Ok I can not use an 'su' command in terminal to gain administrative privileges and yet it will not let me giving me the error 'su: Authentication failure' i know i am root so either i am really outdated or doing something wrong, as even in the shell when i edit fstab with gedit it is read only

---

### Post by Morbius1 on 2010-06-30
There is no root in Ubuntu only sudo ( or in this case gksu or gksudo ).

What is the exact error when you issue the following command in the Terminal:

```
gksu gedit /etc/fstab
```

---

### Post by Selleen rane on 2010-06-30
Thank you [dabl]("http://ubuntuforums.org/member.php?u=217451") what you told me to do worked perfectly to give me access to edit fstab I nulled out the Windows 7 line and the /media/Document line and rebooted no more error but it will not auto load the drive so thats my next step to find out how to.

THANK YOU ALL :) 

so any suggestions on how to make it properly auto load, i am going to go verify the /media directory is correct

---

### Post by Selleen rane on 2010-06-30
Ok this is how my fstab looks now i am a little confused any suggestions on why the nulled lines where removed?

UID=612f9254-8674-410b-aea7-90d10e2f7101    /    ext2    defaults    0    1
UUID=4922f7a4-9244-475e-a8ae-c7fc9cfd0501    swap    swap    sw    0    0
UUID=83D0D2A9BBD75640    /media/Games_    ntfs-3g    defaults    0    0
UUID=660CBEF40CBEBE7D    /media/sda1    ntfs-3g    defaults    0    0

UUID=A6C8B400C8B3CD35    /media/sda2    ntfs-3g    defaults    0    0

---

### Post by Morbius1 on 2010-06-30
>                               [COLOR=Black]UUID=A6C8B400C8B3CD35[/COLOR] /media/Windows 7  ntfs-3g defaults 0 0The syntax of the fstab line is very strict. Each position has a purpose:

This is the way the system will interpret the line above:

device: [COLOR=Black]UUID=A6C8B400C8B3CD35
mount point: [/COLOR]/media/Windows
[COLOR=Blue]File type: 7[/COLOR]
options: ntfs-3g

Because of the space it sees "7" as a file type instead of ntfs-3g and there is no "7" file type. Then it sees ntfs-3g as an option and there is no such option

The way you handle spaces in this type of case is to use "\040" . For example:
```
[COLOR=Black]UUID=A6C8B400C8B3CD35[/COLOR] /media/Windows\0407  ntfs-3g defaults 0 0
```[COLOR=Blue]NOTE: That's a zero-4-zero[/COLOR]

Linux just like UNIX hates spaces :wink:

[COLOR=Blue]EDIT: If you try something like this, after making you changes to fstab , go into a terminal and type:[/COLOR]
```
 sudo mount -a
```
It will execute fstab for all new entries plus report errors if there are any. This way you can find out if there are any mistakes and saves you  a reboot.

---

### Post by Selleen rane on 2010-06-30
Well cleaned it up now it looks like this

UUID=612f9254-8674-410b-aea7-90d10e2f7101    /    ext2    defaults    0    1
UUID=4922f7a4-9244-475e-a8ae-c7fc9cfd0501    swap    swap    sw    0    0
UUID=83D0D2A9BBD75640    /media/Games    ntfs-3g    defaults    0    0
UUID=660CBEF40CBEBE7D    /media/sda1    ntfs-3g    defaults    0    0
UUID=A6C8B400C8B3CD35    /media/sda2    ntfs-3g    defaults    0    0

Rebooted and all the drives auto load correctly with no errors.

Now if i could just say the same for X server with its "error resolution change not allowed" or something like that LOL

Thank you all for all your great help :)

---

