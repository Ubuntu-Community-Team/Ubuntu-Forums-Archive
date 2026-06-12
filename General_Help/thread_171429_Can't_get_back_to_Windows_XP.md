---
title: "Can't get back to Windows XP"
date: 2006-05-06
forum: General Help
---

### Post by dawgs72 on 2006-05-06
Today I installed Ubuntu version 5.10 on a 30 GB partition of my hard drive and now I cannot get back into Windows XP.  When I select Windows it shows me a screen where it asks me how I want to start Windows (Safe Mode, Last Known Good Configuration, Normally, etc.) I have tried every option but after every time my computer reboots after I make my selection.

If anyone has any idea of what I have done or how I can fix it, would be greatly appreciated.

---

### Post by dawgs72 on 2006-05-06
I deleted the partition that contained Ubuntu to see if that would helpbut still I cannot boot into Windows when I try I get this message

```
GRUB Loading stage 1.5.
GRUB loading please wait...
Error22
```

---

### Post by Chillster on 2006-05-06
Try putting a windows bootdisk in or boot from windows xp cd and go into recovery console. When you got the prompt type fdisk /mbr and that should probably take care of it.

---

### Post by dawgs72 on 2006-05-06
I just tried the fdisk /mbr and windows said it did not recognize that command for a list of availiable commands type 'help'

Any other suggestions?

---

### Post by cyracks on 2006-05-06
I think there is a command like fixboot or fixmbr or something like that. The second option is to just reinstall windows.

---

### Post by Ramses de Norre on 2006-05-06
Do fixmbr, only if that doesn't solve it you could try fixboot. I've had bad experience with fixboot, though I don't really know the difference.

---

### Post by r53s on 2006-05-06
fdisk/mbr works...
But you should have a W98 boot floppy...

---

### Post by LORD_PoLvO on 2006-05-06
you could always just use ubuntu instead of windows?

---

### Post by dawgs72 on 2006-05-06
I tried fixmbr and fixboot now i get this
```
NTLDR is missing
```

---

### Post by LORD_PoLvO on 2006-05-06
you have to re-install the operating system if thats teh case.

---

### Post by dawgs72 on 2006-05-06
[QUOTE=LORD_PoLvO]you could always just use ubuntu instead of windows?[/QUOTE]

I would but other people use this computer who can barely use windows.

---

### Post by sinkxdie on 2006-05-06
I know it costs, but you can always try Crossover Office

---

### Post by LORD_PoLvO on 2006-05-06
[QUOTE=dawgs72]I would but other people use this computer who can barely use windows.[/QUOTE]


oh well if thats the case windows woiuld be better but, its really not that hard to use ubuntu once all the net and drivers etc are working they should have no trouble using it and they would probably find the simple meus esier.

---

### Post by r53s on 2006-05-06
Ok, if you can't repair master boot record on winblows, then the other solution is to reinstall linux, and install grub on mbr (Winblows partition)...
I think it's best to have each OS in it's own hard  disk...

---

### Post by LORD_PoLvO on 2006-05-06
[QUOTE=r53s]Ok, if you can't repair master boot record on winblows, then the other solution is to reinstall linux, and install grub on mbr (Winblows partition)...
I think it's best to have each OS in it's own hard  disk...[/QUOTE]


yup thats how i have mine set up though i have 2x 40 gig the slave 40 gig have 2 partions 20 each for linux and storage for windows coz i use windows for pron and giant downloads etc.

---

