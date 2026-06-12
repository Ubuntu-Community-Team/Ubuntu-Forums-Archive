---
title: "Is Nautilus broken?"
date: 2006-06-23
forum: General Help
---

### Post by imaca on 2006-06-23
Haven encountered a problem copying large numbers of files (1500+) from a DVD as follows.
If I try and copy all the files at once, the progress goes to about 1000 then disappears.
If I copy files in 2 smaller lots it works fine.
???????:confused: ???????
This is a major problem for me if I can't trust the file system.

Also a similar problem - after about 3 weeks of using 6.06, when I copy files onto a memory card the file appears there after copying but when I take the card out and plug in again it isn't there.
The exact same thing happened for me on breezy, worked perfectly for a few weeks then suddenly copying to memory cards is dead.
As I have said in other post, my confidence in Ubuntu is being eroded.
This is a shame because I really really like it.

---

### Post by Ramses de Norre on 2006-06-23
Did you eject the memory cards correctly before you pulled them out? And I mean checking with mount to be sure they're gone? Otherwise it isn't surprising that the data isn't there..

And did you already try to copy those files from terminal? Maybe it's a bug in cp..

---

### Post by imaca on 2006-06-23
The files were being copied over existing files.
The existing files and folders were an incomplete backup of files from another PC.
The DVD I was copying from was ALL the data - ie it had folders with files in them which would have been there but empty in the existing data.

"eject the memory cards" ??? Hmmmmm. I think you are on to something....
I didn't know you had to do that, doh!
 How do I do that?

PS what's "cp"

---

### Post by Ramses de Norre on 2006-06-23
Ejecting is the same as 'safely removing" in windows, memory cards and in fact all kinds of removable drives are mounted async which means that when you write data to them the data is stored in RAM and written to the drives when your system has I/O available. It is done like this to limit read/write cycles on the flash drives and because writing on them is fairly slow.

When you eject the cards all data from the RAM is written to them and you can pull them out, but if you don't a lot of data will be in your RAM waiting to be written to the disc. To eject them just right click and select "eject".

cp is the command for copying files, and I think nautilus uses this internally to copy over files.

---

