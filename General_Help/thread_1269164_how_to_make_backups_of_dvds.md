---
title: "how to make backups of dvds"
date: 2009-09-17
forum: General Help
---

### Post by tsueseres on 2009-09-17
hello how do i make backups of my dvs, i read that i can do that with k9copy but i have ubuntu hardy with gnome and i cant installit

---

### Post by scragar on 2009-09-17
There are lot's of programs that rip DVDs or similar disks, personally I prefer to do it from the command line:
```
dd if=/dev/dvd of=/home/**scragar**/Desktop/**myDVD**.iso  bs=1024k
```
I'm sure someone elses suggestion will be more user friendly though.

---

### Post by tsueseres on 2009-09-17
> **scragar said:**
> There are lot's of programs that rip DVDs or similar disks, personally I prefer to do it from the command line:
```
dd if=/dev/dvd of=/home/**scragar**/Desktop/**myDVD**.iso  bs=1024k
```
I'm sure someone elses suggestion will be more user friendly though.

i need to takeout the protection thats a problem

---

### Post by ramjet_1953 on 2009-09-18
Why can't you install K9Copy?

I know it is a KDE application, but it will install successfully into GNOME without issue.

It will install a few extra KDE files, to make it work, but GNOME is unaffected.

I have been using K9 Copy for years with GNOME.

Regards,
Roger :)

---

### Post by egalvan on 2009-09-18
> **ramjet_1953 said:**
> 
I have been using K9 Copy for years with GNOME.


Same here...

almost all KDE apps will run under Gnome,
and Gnome stuff runs under KDE.

They will even run under XFCE, they will just pull in many more dependancies.

---

### Post by tsueseres on 2009-09-18
ok the version im tring to install is 2.3.0.deb then it tell me 
dependenci not sat.. :kdebase-runtime
i make a sudo apt-get install kdebase-runtime and it installs me a lot of things (i think cause it took to much to end) 
i open again the deb files and it tellsme the same 
dependenci not sat.. :kdebase-runtime

i use hardy hope is not a problem

---

### Post by jocheem67 on 2009-09-18
DvdFabDecrypter under wine
Avidemux to create a nice x264/aac/mp4
Subrip under wine.

Foolproof, no CLI, and fun to do actually.

---

### Post by niteshifter on 2009-09-18
Use dvdbackup.

You'll need the Medibuntu repositories so you can install libdvdcss2.


```
sudo apt-get install libdvdcss2
sudo apt-get install dvdbackup
```

Using it:
```
dvdbackup -v -M -i /dev/dvd -o /media/disk/
```
-v tells the program to be verbose, print out while running.
-M mirror, copy the entire dvd.
-i input device.
-o output setting. You pick the path.

Read
```
man dvdbackup
```
for more ways to use it. Pretty painless to use actually. What's given above will create a directory in /media/disk whose name is usually the dvd's label. This folder is suitable for making an archive dvd by burning it's content to dvd or viewing with VLC's open directory function.

---

### Post by StuartN on 2009-09-18
How do you get a nice, plain, untranscoded directory of .VOB files off a DVD? I tried a few apps, but none was a simple as old DVD Decrypter under Windows.

---

### Post by 3rdalbum on 2009-09-18
> **tsueseres said:**
> ok the version im tring to install is 2.3.0.deb then it tell me 
dependenci not sat.. :kdebase-runtime
i make a sudo apt-get install kdebase-runtime and it installs me a lot of things (i think cause it took to much to end) 
i open again the deb files and it tellsme the same 
dependenci not sat.. :kdebase-runtime

i use hardy hope is not a problem

Use the version of K9copy that's available in the 8.04LTS repositories, or upgrade your system to 9.04.

It looks like you're trying to install the latest K9copy, which depends on the latest kdebase-runtime, which you only have if you are running Ubuntu 9.04.

---

### Post by 3rdalbum on 2009-09-18
> **StuartN said:**
> How do you get a nice, plain, untranscoded directory of .VOB files off a DVD? I tried a few apps, but none was a simple as old DVD Decrypter under Windows.

Acidrip will first rip plain DVD files, and then attempt to use Mencoder to transcode them. Although the ripping part always works, the transcoding process will fail if there are spaces in the filename (it's a bug).

You can use this bug to your advantage, to just get the plain unencrypted DVD ripped files off the disc. They will end up in Acidrip's temporary folder, which I believe is /tmp by default.

---

### Post by stinger30au on 2009-09-18
forget about wasting your time with the install of wine and using dvdfab and what ever else

very simple

first off, make sure your pc will play a standard dvd movie with the standard dvd movie player

if it wont play, you probably need to to install the software 

hit applications, add remove and search on "restricted"

install the restricted extras and restart pc and try again
this time it should play

now install k9copy
sudo apt-get install k9copy

this will rip any dvd you throw at it and compress it to fit on a 4.7 gig dvd and remove all copy protection

im yet to find any dvd it will not handle

---

### Post by jocheem67 on 2009-09-19
The advantage of dvdfab/wine is that it's capable of beating all the protections that are floating around.
K9copy isn't, though it is a good program. It's also a bit too KDE for my taste..
Thankfully there's choice, huh?:lolflag:

For a single vob out of a dvd, there's vobcopy

```
sudo apt-get install vobcopy
```

```
vobcopy -l
```

will automagically create one big vob out of the main movie on a dvd:P

And it's not about the restricted-extras that will make dvd's play on an ubuntubox, it's libdvdread/libdvdcss2...

---

### Post by stinger30au on 2009-09-19
> **jocheem67 said:**
> The advantage of dvdfab/wine is that it's capable of beating all the protections that are floating around.
K9copy isn't, though it is a good program.


as i said

im yet to find a movie that k9copy will not copy, it does the lot

---

### Post by StuartN on 2009-09-19
> **jocheem67 said:**
> ```
vobcopy -l
```

Now that sounds absolutely perfect!

It would be nice if there were an ignore-read-error option, as DVD Decrypter has, for dealing with scratched disks. For minor damage you just get a little video dropout in a perfectly watchable stream.

---

### Post by andrew.46 on 2009-09-19
Hi Stuart,

> **StuartN said:**
> Now that sounds absolutely perfect!

You can also *mirror* the directory structure of your DVD with:

```
vobcopy -m
```

From the man pages:

```

   -m, --mirror
        mirrors  the  whole  dvd to harddisk. It will create a directory
        named after the dvd and copy the ifo, bup and vob  files  there.
        The title-vobs are decrypted during this.


```

Lots of options to play with....

Andrew

---

### Post by stinger30au on 2009-09-19
> **StuartN said:**
> Now that sounds absolutely perfect!

It would be nice if there were an ignore-read-error option, as DVD Decrypter has, for dealing with scratched disks. For minor damage you just get a little video dropout in a perfectly watchable stream.


to reapir the scratched disc, polish the disc with brasso

never had one fail yet

forget the ones who tell you to use toothpaste, cos its useless, so to is dishwashing liquid

---

### Post by StuartN on 2009-09-19
> **stinger30au said:**
> to reapir the scratched disc, polish the disc with brasso

I have a really corrupt DVD to try that with - the surface looks reasonable, but it did work fine when new and is now not possible to copy. I have tried loads of methods and gave up on everything except cleaning with isopropyl alcohol.

---

### Post by StuartN on 2009-09-19
> **jocheem67 said:**
> For a single vob out of a dvd, there's vobcopy
```
vobcopy -l
```

Thankyou so much for this. I have now had a chance to try it, and that simple "vobcopy -l" is the simplest, most convenient method I have ever seen to rip a DVD.

It bombs out on very dirty / scratched disks and it doesn't like -l large files onto NTFS, but for a clean DVD to home directory EXT3 it is absolutely wonderful.

---

### Post by jocheem67 on 2009-09-20
Sometimes I rent a music-dvd from the local library...
With vobcopy I create the vob, with avidemux I extract the audio, with audacity I then make nice .ogg's out of the extracted wav.
Good method I think..

This is in Holland a legal thing by the way..might not be so in other Countries.

---

### Post by stinger30au on 2009-09-20
> **StuartN said:**
> I have a really corrupt DVD to try that with - the surface looks reasonable, but it did work fine when new and is now not possible to copy. I have tried loads of methods and gave up on everything except cleaning with isopropyl alcohol.


alcohol is a cleaner, not a polisher

the plastic that is scratched is the bit to be polished so the laser can punch thru it and read the very thin film of die on the top side where the data is stored

i have even used a slow speed bench polisher to repair scratched dvds

secret to success is to keep the disc moving and dont stop or you will damage the surface even more

---

### Post by StuartN on 2009-09-20
> **stinger30au said:**
> to reapir the scratched disc, polish the disc with brasso

never had one fail yet

I struggled with apt-get install brasso, even sudo apt-get brasso (and you would think an su could do anything). Eventually had to walk (!) to a local repository and use the -$ option. So having used my $, I find I am actually just moving the errors around - I still get errors, but in different sectors. The disk does not look too bad, and I have certainly read much worse looking scratches many times.

---

