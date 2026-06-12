---
title: "Nautilus shows files with bigger size !!!"
date: 2011-10-15
forum: General Help
---

### Post by bigthugs0 on 2011-10-15
i just noticed that nautilus on ubuntu 11.10 shows all files with  bigger size !!! but when u copy the file to another operating system , u can see the real size of the file

for example when i download the Ubuntu Server amd64 

it was about 682MB and after downloading it became 715MB

so when u see the size in properties in bytes its 715,436,032 bytes , divide it on 1024 twice to get it in MB u get the result 682MB , so nautilus doesn't calculate this !!!!!!!

i guess this is bug :S

its annoying


im running on Ubuntu 11.10 64 Bit

---

### Post by mcduck on 2011-10-15
Nautilus uses 1000 as multiplier, as its supposed to do since it uses MB as unit instead of MiB.

edit: Perhaps you should instead report a bug to the developers of your other OS/file manager for not using correct prefix for the units they are using. :D

---

### Post by An Sanct on 2011-10-15
That would be the difference between 1024 and 1000 (MB and MiB)

---

### Post by bigthugs0 on 2011-10-15
looool so other OSs are all wrong :D , how cooool hahahahaha

---

### Post by An Sanct on 2011-10-15
> **bigthugs0 said:**
> looool so other OSs are all wrong :D , how cooool hahahahaha

Actually no :), but they are fooling you - with the help of hardware suppliers.

Take a look at this [wiki]("http://en.wikipedia.org/wiki/Mebibyte"), note the table on the left

See, actually, when you buy a 1Tb disk, you _do not_ get a 1024Gb disk, you get a 1000Gb disk.

---

### Post by OzzyFrank on 2011-10-16
Yeah, this somewhere between annoying and really bad. Basically everything I've gotten used when it comes to filesizes has been turned on its head, with "95.8Mb" now being displayed as "100.4Mb", which seems rather dramatic to me. I've looked for a way to change it back, but can't seem to find any option to do so. I remember way back when I used Windows, you could actually change that, though it was probably a hack, so I am guessing somewhere there is the option to return the mode of display back to what it was. Any ideas how to go about this?

PS: I'm also running 64-bit 11.10, in case that makes a difference (which it shouldn't, but you never know)

---

### Post by thepisu on 2012-02-16
What about submitting an feature request for Nautilus, an options to select between MB and MiB in filesize view? Like the one in Filezilla...

I'm astonished that no one else asked this.

---

### Post by bugritall on 2012-09-22
I have switched from Ubuntu 10.04 straight to 12.04 and now none of my files is the same size as before. A video that Lucid reported as 800.0 MB is now 838.8 MB and the free space on one of my drives has gone from 218.8 GB to 234.9 GB. Neither system mentions MiBs or GiBs so, since Precise is reporting file sizes correctly, it must mean that Lucid and earlier releases were getting it wrong for all those years.

When someone finally noticed that Nautilus was reporting file sizes in MiBs and GiBs and calling them MBs and GBs, something definitely needed to be done. Personally, I would have preferred to see file sizes reported correctly in MiBs (eg 800.0 MiB) so that the at-a-glance numbers remained consistent with the old, incorrect ones.

Finally, it's all very well being purist about things but look again at the first sentence of my post. Does that "none of my files _is_ the same size" offend your sensibilities? It's grammatically correct but because it "sounds just wrong" I would normally have written the sentence differently. Purity in all things isn't always the best approach, not when idiom and common usage dictate otherwise. Mind you, I draw the line at "different than".  :)

---

