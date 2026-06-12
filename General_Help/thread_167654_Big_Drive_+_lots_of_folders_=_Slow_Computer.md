---
title: "Big Drive + lots of folders = Slow Computer?"
date: 2006-04-28
forum: General Help
---

### Post by Konradman on 2006-04-28
Hi all, 

I have a problem for which I can't seem to find an answer anywhere.

I have an external USB2 drive on which I store stuff (filled with stuff, like 200GB worth and lots of folders)... it's mounted correctly and I can access it, but when I do...

Here is my problem:

Everytime I open this drive in my filebrowser (Nautilus I guess) My whole system gets choppy. For example, my mouse pointer freezes in place every couple of seconds for about a second each time. It's painfully annoying to browse through the drive... I could access everything fine, it's simply the performance that is sucking.

Any suggestions on how to fix this problem? :confused: :-k 

I am fairly new to Linux, so if you need more information in order to help me, let me know how to find and give you that info. If you can simply point me in the right direction or speculate about the problem, that would be great too.

Thanks!

---

### Post by marks_linux on 2006-04-29
you could try turning off some of the goodies like files preview, etc in the preferences. Makes a biggish difference to me.

---

### Post by GeneralZod on 2006-04-29
Have you enabled DMA on your harddrive? If not, search the forums for "DMA" - there's quite a few guides on how to do it :)

---

### Post by Paulo Wageck on 2006-04-29
i have had simililar problems with corrupted filesystem or bad blocks....

turn off preview in some cases might help

backup all to a brand new drive... manually check all your important files.

make a low level format using boot cdrom for this purpose from the harddrive manufacturer.

create a reiserFS partition using your current install or ubuntu install cd...


hope it helps....

---

### Post by Paulo Wageck on 2006-04-29
instead of copying using nautilus you can try shell access (recovery mode) and a norton commander like program callled mc
<(midnight commander)

sudo apt-get install mc

---

### Post by Slim Odds on 2006-04-29
[quote=GeneralZod]Have you enabled DMA on your harddrive? If not, search the forums for "DMA" - there's quite a few guides on how to do it :)[/quote] 
Is DMA relavent for USB?

How would you "enable" it?

---

### Post by GeneralZod on 2006-04-29
[QUOTE=Slim Odds]Is DMA relavent for USB?

How would you "enable" it?[/QUOTE]

Whoops - I totally missed that this was a USB drive :???: Ignore my earlier post ;)

---

### Post by Konradman on 2006-04-30
Well I was hoping that I would be able to get by without buying a new drive... It works fine in windowsXP anyway, so I doubt it's the hardware. I tried playing with the folder options.. still no good. I noticed that the performance lag drops when i go deep inside a directory, into a directory that has only files (no other folders) in it.

/music(choppy when browsing)/bands(still choppy)/a band(still)/(only files in here and this is where the choppiness stops)

Any other suggestions?

---

