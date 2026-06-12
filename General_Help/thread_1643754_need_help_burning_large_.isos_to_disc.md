---
title: "need help burning large .isos to disc"
date: 2010-12-12
forum: General Help
---

### Post by capitalfear on 2010-12-12
say i have a 5.9 gig iso. i need to burn it to two 4.7 DVD+Rs that are 4.7 gigs

i would like to be able to put 4.7 gigs on the first disc, then 1.2 gigs on the second. 
i don't know if its a program or what. also if you can do it in windows 7 thats fine i can do it there too

---

### Post by rickyrockrat on 2010-12-12
It depends on what you are going to do with those ISOs.  I don't know of any application that would actually run an ISO image split across 2 DVDs, so I presume you are just saving it for copying back.

One way is to dd the iso.

Just not sure what you are trying to do.

---

### Post by katykat on 2010-12-12
I *believe* the large ISOs are designed for dual sided 8+Gb DVD+R's .

With these beasts I would run directly from the hard drive with a utility that will read ISOs, or write the VOB files directly to disk. 

Then I normally compress them to fit on a regular DVD with RAR in multivolume mode. 

I usually write DVDs to the HD for viewing just in case there is a read error, and I dont want to be stuck with a half finished movie.

---

### Post by rickyrockrat on 2010-12-12
Sorry, it's still not clear what your usage is.

If you want to mount the ISOs, that's *really* easy:
```
mkdir m
sudo mount -o loop HonkinBig.iso m
```

---

### Post by rickyrockrat on 2010-12-12
if you want a program to do this for you, try one of these:
acetoneiso
furiusisomount
gisomount 
gmountiso

However I've never used them. I'm one of those hard-core command line guys.

---

### Post by capitalfear on 2010-12-12
no i dont need to mount it but thank you for that, and i love my command line as well. and i am cheap when it comes to those DL discs, they are awesome, but i dont want to pay what they are charging, i just need to "hold" the rest of the information whilest i stick in another dvd+r

---

### Post by rickyrockrat on 2010-12-12
Then there's two options. 1) Use dd to split the ISO into manageable chucks, then use k3b to write a data DVD.
2) Get an external HDD, or just buy a cheap USB-IDE adapter and use any old harddrive.

For the first option, you will want to use bs= with count= to get the first part of the file, then
use bs= count= and skip= to get the second half.

Dump each of those into a new k3b data DVD.

If you do this a lot, you can script it very easily and leave k3b out of it.

```
mkisofs -o $FN -J -R -no-emul-boot -boot-load-size 4 -boot-info-table /path/to/dir/with/files
```

---

### Post by capitalfear on 2010-12-12
i just always wanted to keep a hard copy of my isos

---

