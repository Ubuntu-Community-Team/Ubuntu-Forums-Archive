---
title: "Wii Backups?"
date: 2009-12-11
forum: General Help
---

### Post by PerfectReign on 2009-12-11
I just bought a Wii for my two rugrats yesterday. They'll open it later this month.

In anticipcation, I wanted to see what I could use to backup the games, since they're on CD or DVD (something like that anyway).

I found several links, but they all point to Windows-based solutions.

The only link I found for a real OS was here: [http://ubuntuforums.org/showthread.php?t=495884](http://ubuntuforums.org/showthread.php?t=495884) 

That thread is somewhat old, however.  Anyone recently used Ubuntu to backup and/or use homebrew software on a Wii?

---

### Post by Scarfnoogan on 2010-02-17
Bump
 
I'm also looking for a way to backup the games, I found a program called friidump but my idiocy seems to have overtaken me and I can't get it to compile/run, I've also tried rawdump(windows prog) in wine and virtualbox,
 
Wine: wont even open
VB: doesn't recognize the drive, says could be faulty(I've used it for this before)
 
 
has anyone dumped a wii disc successfully?
 
Adam

---

### Post by flippo on 2010-02-17
Can't you dd them?
In a terminal:
```
dd if=<device mount, usually /dev/cdrom> of=<where you want the file>.iso
```

---

### Post by pirateghost on 2010-02-17
you do realize that in order to play backed up copies you need a modchip or similar mod functionality on the wii, right?

you cant just make a dvd of the game and have it work without some type of modding done to the wii.

personally if you arent scared to open up the wii, i recommend a device called wiidrivekey.  i have a 6 yr old and that little drivekey mod was the best money i spent on that entire gamesystem.

---

### Post by flippo on 2010-02-17
There are actually ways to make the wii play backed up games with a softmod (ex the homebrew channel) but it does void the wii warranty.

---

### Post by pirateghost on 2010-02-17
> **flippo said:**
> There are actually ways to make the wii play backed up games with a softmod (ex the homebrew channel) but it does void the wii warranty.
like i said "or similar mod functionality".  that encompasses the softmods.  however a lot of games do not work with the softmods, so test thoroughly.

---

### Post by Scarfnoogan on 2010-02-17
> **flippo said:**
> There are actually ways to make the wii play backed up games with a softmod (ex the homebrew channel) but it does void the wii warranty.
 
 
My wii's softmodded with usbloader(external hard drive), it doesn't void the warrenty as you can erase the software added for the mod, unlike mod chips which are a permanent solution(and yes, a better quality mod)
 
 
I will try DD tonight when I get home, fingers crossed

---

### Post by Jackzor on 2010-02-17
I do believe that playing back ups is illegal. I may be wrong though.

---

### Post by Scarfnoogan on 2010-02-17
> **pirateghost said:**
> however a lot of games do not work with the softmods, so test thoroughly.
 
I've only tried about 15-20 games, but so far, most games that don't work can work by changing a setting on the wii, or in the case of Super mario brothers patching the iso file before burning(copying to HD)

---

### Post by Scarfnoogan on 2010-02-17
> **Jackzor said:**
> I do believe that playing back ups is illegal. I may be wrong though.
 
 
yes, if you're downloading them, or whatnot, but my kids are 5 and 9 so it gives me the warm fuzzies to not have them playing with the original discs

---

### Post by SyntheticXTC on 2010-02-17
> **Scarfnoogan said:**
> yes, if you're downloading them, or whatnot, but my kids are 5 and 9 so it gives me the warm fuzzies to not have them playing with the original discs

Technically K3B should be able to perform this function too...but with the copy protection on the wii discs it is probably not going to work.  And just because you get a copy of the disc, it is still not going to work as the wii has blocks in place to stop the use of dvdrs working on the wii.

Ofcourse if you softmod your wii it should work but it will void any warranty you may have for the wii.

Good Luck

---

### Post by Scarfnoogan on 2010-02-17
> **SyntheticXTC said:**
> Technically K3B should be able to perform this function too...but with the copy protection on the wii discs it is probably not going to work. And just because you get a copy of the disc, it is still not going to work as the wii has blocks in place to stop the use of dvdrs working on the wii.

 
That's why I was looking for rawdump(or a reasonable hand drawn facsimile) standard ripping/copying wont do the job

---

### Post by Jackzor on 2010-02-17
> **SyntheticXTC said:**
> Technically K3B should be able to perform this function too...but with the copy protection on the wii discs it is probably not going to work.  And just because you get a copy of the disc, it is still not going to work as the wii has blocks in place to stop the use of dvdrs working on the wii.

Ofcourse if you softmod your wii it should work but it will void any warranty you may have for the wii.

Good Luck

With the soft mod you will also lose the option to upgrade the firmware that Nintendo puts out.

---

### Post by Scarfnoogan on 2010-02-17
> **Jackzor said:**
> With the soft mod you will also lose the option to upgrade the firmware that Nintendo puts out.
 
 
you can do what people do with jailbroken iphones....restore, update, re-mod

---

### Post by Scarfnoogan on 2010-02-20
Update, ok, I found a way to do it, it seems to be slower than raw dump, but raw dump takes long enough that it's smart to set it before bed, or work, or school or whatever

so you get a program called Friidump.  0.4.0 is the latest version

I had a hard time getting it installed, but it's probably because I'm a gigantic NOOB!

so you go to terminal and cd to the directory you extracted it to

as super user run the following

mkdir BUILD

cd BUILD

cmake ..

make

make install
then to backup a disc run 
 friidump -d /dev/cddrive -a(replace cddrive with what's appropriate)

wait for 3-5 hours and enjoy your new wii back up iso


Adam

---

### Post by Siph0n on 2010-05-02
1st) I am 99% sure you can not remove all traces of a softmod. I read somewhere that everything you do is saved somewhere. Someone tried removing all their softmod stuff before sending it off to Nintendo to fix a problem. Nintendo still found traces of the softmod.

2nd) I use a program called WiiFlow on my Wii. I put a wii disc I own into the wii, and use WiiFlow to copy it to a usb drive. The usb drive has to be formatted as wbfs I think.

3rd) Only certain dvd drives can read wii games. I don't have the list, but definitely not all dvd drives can read wii discs.

---

### Post by Elfy on 2010-05-02
closed - staff review

---

