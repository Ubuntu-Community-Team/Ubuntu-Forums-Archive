---
title: "Watch it in OpenOffice!!"
date: 2010-10-17
forum: General Help
---

### Post by victorhugo289 on 2010-10-17
I was working in OpenOffice Word when I accidentally plugged the cable off.
In OpenOffice word there appeared a message saying ´Recovery of file'. I just clicked away, there was a weird pull-down menu that said "unicode" among other weird fonts and guess what?? BLANK PAGE.
My file was big and had a lot of writing in it, now it is 0 bytes long.

Some would say that this has something to do with the ex4 file system rather than with OpenOffice, but I just say: watch it. Lest you´re working on something important and lose everything.

I work in Ubuntu every day. And i love it. u.u

---

### Post by Vaphell on 2010-10-17
power failure is an undefined state and you can't be sure of anything. IIRC Ext4 is reportedly somewhat more prone to failure because devs finetuned it for performance so writes are less frequent but in greater chunks (hdds are good at continuous writes). Power failure can cause buffered write not being written at all before pc dies. Having backups in different places is a good idea because it's bad to put all eggs in one basket. Your hdd may die, filesystem may get corrupted, computer stolen/destroyed, you can wipe the data by mistake... Don't rely on automatic backups, always perform manual ones too. It also makes it's easier to roll back the doc if you change your mind and you got older copy closer to the new idea :)

you can minimize the risk of damage in OO by enabling the backup feature
it's under Tools-Options-Load/save (or whatever, not using EN version here)
if your main doc dies for whatever reason, you still have something to fall back on

---

### Post by hrickh on 2010-10-17
> **Vaphell said:**
> 
you can minimize the risk of damage in OO by enabling the backup feature
it's under Tools-Options-Load/save (or whatever, not using EN version here)
if your main doc dies for whatever reason, you still have something to fall back on
As someone who spends the majority of his working day in oo.org (and before that I used MSO extensively), this is a good idea in any case - doesn't matter what filesystem is used.

R.
==

---

### Post by victorhugo289 on 2010-10-24
It happened yet again. I saved and saved and now the file is 0 bytes long.
I should buy a no-break connector or whatever they call it.
Strange, sticky notes is not affected by power failure...I should probably use Sticky notes.

---

### Post by victorhugo289 on 2010-10-24
> **hrickh said:**
> As someone who spends the majority of his working day in oo.org (and before that I used MSO extensively), this is a good idea in any case - doesn't matter what filesystem is used.

R.
==

it's enabled, and I saved 5 seconds before the light went off,  I was writing the beginning of a new word when pluff!!

---

### Post by victorhugo289 on 2010-10-25
I found two options in Tools/Options/Loadsave
 
to save every: 1 minute 
to always make backup copy: YES!
 
I feel more confident now! 
 
I love Ubuntu, and I really like Open Office.

---

### Post by Hagar Delest on 2010-10-25
Is your file system EXT4? There are some discussions about it (here?) and it seems that the cache has been increased to improve performance. The downside is that the write operations on disk are heavily delayed. Hence such situations where OOo saves the file, the OS tells it it has been saved but the file hasn't yet been registered on the HD.

I keep using EXT3 and never faced that problem.

---

### Post by victorhugo289 on 2010-10-30
> **Hagar de l'Est said:**
> Is your file system EXT4? 

Yes, it is Ext4.

---

