---
title: "Woh is me!!!"
date: 2006-06-05
forum: General Help
---

### Post by LinuX Nova on 2006-06-05
Heya guys. Ubuntu messed up my laptop unfortunately (just not enough resources apparently) so i need to re install the laptops native Windows 98.

For this i need to reformat my hard drive to what Microsoft 98 accepts (fat13?) and i understand i can just use the boot disk and type

```
Format: [Drive Name]
```
at the dos prompt, but i'm not sure what the default name of the drive is when you install ubuntu.


I'm lost :'( Please help.

Thank you all,

Paul

---

### Post by cleentrax on 2006-06-05
Don't give up on Ubuntu yet. The alternate install disc lets you install on a PC with less than 256mb of RAM, and Xubuntu is also a lightweight option for older PCs.

What are your system specs?

---

### Post by LinuX Nova on 2006-06-05
I'm sorry, i should have said. My future college has also specified that I MUST have windows on the laptop, and there is no way enough space for a dual boot.

However I havent given up on the OS, as I use it on my desktop, and have done for almost a year now, I'll be upgrading to dapper soon.

---

### Post by johnc4510 on 2006-06-05
I agree with cleentrax, don't give up yet. Try one of his suggestions, there's a good chance you'll be glad you did.

---

### Post by sweeper on 2006-06-05
I think the server install needs even less ram under 192 I think.

---

### Post by sweeper on 2006-06-05
[QUOTE=LinuX Nova]Heya guys. Ubuntu messed up my laptop unfortunately (just not enough resources apparently) so i need to re install the laptops native Windows 98.

For this i need to reformat my hard drive to what Microsoft 98 accepts (fat13?) and i understand i can just use the boot disk and type

```
Format: [Drive Name]
```
at the dos prompt, but i'm not sure what the default name of the drive is when you install ubuntu.


I'm lost :'( Please help.

Thank you all,

Paul[/QUOTE]

You might need the windows 98 floppy discs, sorry I can't remember more :(

---

### Post by LinuX Nova on 2006-06-05
Thanks, I have those, i just need the name of the average ubuntu hard drive, whats yours?

---

### Post by cleentrax on 2006-06-05
This is not a Windows support forum. ;-)

Every Windows boot disc I have used comes with formatting capabilities. Boot from the disc, and follow the instructions. You should use FAT32.

---

### Post by LinuX Nova on 2006-06-05
All i need to know is the name of your Hard drive.

---

### Post by Jason_25 on 2006-06-05
The "name" of the hard drive is not required for reinstalling windows.  

For windows 9x systems to wipe the master boot record to use windows again, use the 
```

fdisk /mbr

```
command.  

And for NT systems use the recovery console.  Specifically, fixboot and fixmbr.  You can read more about them at the MS knowledge base.

---

### Post by sweeper on 2006-06-05
[QUOTE=LinuX Nova]Thanks, I have those, i just need the name of the average ubuntu hard drive, whats yours?[/QUOTE]

Not a clue, sorry. If you stick the floppies in they should 'just work' lol, tho I haven't used 98 for ages. ;)

---

### Post by kriding on 2006-06-05
or you could run the fdisk command and just delete the partitions, then set them up again, that way all names and labels are deleted. Once you have them setup,  enter "format c: /u" (w/out quotes) and this will format the drive to FAT32. ('u' stands for 'unconditional' meaning it will wipe absolutly everything

---

### Post by LinuX Nova on 2006-06-05
[QUOTE=kriding]or you could run the fdisk command and just delete the partitions, then set them up again, that way all names and labels are deleted. Once you have them setup,  enter "format c: /u" (w/out quotes) and this will format the drive to FAT32. ('u' stands for 'unconditional' meaning it will wipe absolutly everything[/QUOTE]

problem is, it says invalid drive specification.

I'm confused.

---

### Post by kriding on 2006-06-05
hmm..ok, I know there was a thread on here that provided a link to another disk utility. I used it when I tried to revert from ubuntu to XP. I'll try and find the thread for you, unless someone else beats me to it:D

---

### Post by LinuX Nova on 2006-06-05
Thanks, will i be able to use it without an OS, cos at the moment there isn't one.

---

### Post by kriding on 2006-06-05
define use it!

ultimatly no, as there will be nothing to run your hardware, or any kind of platform to support your software, however, you should be able to boot from floppy or CD ROM if your bios supports it

---

### Post by snellgrove on 2006-06-05
[QUOTE=LinuX Nova]My future college has also specified that I MUST have windows on the laptop[/QUOTE]

I feel real sorry for you :eek: 

I would scrounge enough cash for a 2nd box, to have Linux tbh..  cant stand using windows these days, it only frustrates me!

---

### Post by LinuX Nova on 2006-06-05
I think I'm buggered. Windows 98 Installation tells me there is insufficiant space, and fdisk freezes up when i ask it to delete all partitions.

---

### Post by kriding on 2006-06-05
I couldn't find the thread I was after, but here's a link to gparted. Download it and see what you can do (I've never used it but there's plenty of info on these forums about it

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by LinuX Nova on 2006-06-05
Looks promising, thanks. I may have a go at dual-booting with dapper if i can get windows installed.

---

### Post by kriding on 2006-06-05
I wouldn't dual boot on a 4 gig hard drive...it's a teeny bit too small:)

---

### Post by LinuX Nova on 2006-06-05
did i say 4? I meant 6.

---

### Post by Jason_25 on 2006-06-06
[QUOTE=LinuX Nova]I think I'm buggered. Windows 98 Installation tells me there is insufficiant space, and fdisk freezes up when i ask it to delete all partitions.[/QUOTE]

So what happens when you do fdisk /mbr ?  Also fdisk -i should work too if the first doesn't work.

---

