---
title: "Purple screen at startup. Win7 dual install."
date: 2012-02-22
forum: General Help
---

### Post by RingAnimated on 2012-02-22
I keep getting the same problem every time i boot it. it's the latest version. Dual installed with Windows 7. My video card is a NVIDIA Geforce GTX550ti. The only thing the keyboard can do is restart. I cannot do anything else. any help would be great, i'm getting sick of restarting my computer over and over again.

Would there be a way to restore my whole hard drive back a day in BIOS in case i don't like this. MOBO is MSI K9N6PGM2-V2.

---

### Post by RingAnimated on 2012-02-22
BTW: i'm running it on my VirtualBox right now and i like it.

---

### Post by Mark Phelps on 2012-02-23
> **RingAnimated said:**
> ... Would there be a way to restore my whole hard drive back a day in BIOS in case i don't like this. MOBO is MSI K9N6PGM2-V2.

Basically -- NO.  

The only way to restore an entire drive to a previous state would be to have created a backup at that time of the entire drive.

There are various tools that can be used in Linux to do this, the one I prefer is Clonezilla.  With that, you can back of individual partitions, or the entire drive -- and restore the same.

---

### Post by RingAnimated on 2012-02-23
> **Mark Phelps said:**
> Basically -- NO.  

The only way to restore an entire drive to a previous state would be to have created a backup at that time of the entire drive.

There are various tools that can be used in Linux to do this, the one I prefer is Clonezilla.  With that, you can back of individual partitions, or the entire drive -- and restore the same.
Do you know how to fix the PSOD, i think i need a linux GTX550ti driver

---

### Post by miasmablk on 2012-02-23
cd to the directory containing the tar.gz fille

example home/xxxx/downloads

then [COLOR=#6666CC][/COLOR]```
tar -zxvf [COLOR=#6666CC]ledzepplin.tar.gz[/COLOR]
```[COLOR=#6666CC][/COLOR]

you may need super user permissions for this

so ex:```
sudo tar -zxvf file.tar.gz
```

then cd to the directory the tar.gz outputs ```
cd led zepplin
```

then ```
./configure
```

then ```
make
```

then ```
sudo make install
```

---

### Post by miasmablk on 2012-02-23
woah.....wrong thread what the heck lol! ^^^^^

---

### Post by RingAnimated on 2012-02-23
> **miasmablk said:**
> woah.....wrong thread what the heck lol! ^^^^^

I was wondering, i can't even do anything once i get the PSOD.

---

### Post by RingAnimated on 2012-02-24
Bump.

---

### Post by LinuxFan999 on 2012-02-24
It looks like the only thing you can do is reinstall Ubuntu.

---

### Post by enjoijesus94 on 2012-02-24
Purple Screen Freezes?

Ok When Ubuntu Starts To Boot Hit Shift.

Now Go To The second to last line and remove 

"quiet splash"

and replace with
"nomodeset"

and tell me if it works

---

### Post by RingAnimated on 2012-02-25
> **enjoijesus94 said:**
> Purple Screen Freezes?

Ok When Ubuntu Starts To Boot Hit Shift.

Now Go To The second to last line and remove 

"quiet splash"

and replace with
"nomodeset"

and tell me if it works
I just end up at GNU GRUB.

---

### Post by enjoijesus94 on 2012-02-25
> **RingAnimated said:**
> I just end up at GNU GRUB.

So Your Dual Booting ?

With Your Ubuntu Install Highlighted Press Shift.


And Then Replace Quiet Splash With 'nomodeset'

then Crtl+x to boot):P

---

### Post by RingAnimated on 2012-02-25
> **enjoijesus94 said:**
> So Your Dual Booting ?

With Your Ubuntu Install Highlighted Press Shift.


And Then Replace Quiet Splash With 'nomodeset'

then Crtl+x to boot):P

Shift does nothing

---

### Post by enjoijesus94 on 2012-02-25
Sorry About That Hit 'e'
then it will take you to the boot up commands.

replace quiet splash with 'nomodeset'
without quotes.
should be on the second to third line on the bottom.
Ctrl+x to boot

see if that helps.

post back.

---

### Post by RingAnimated on 2012-02-26
> **enjoijesus94 said:**
> Sorry About That Hit 'e'
then it will take you to the boot up commands.

replace quiet splash with 'nomodeset'
without quotes.
should be on the second to third line on the bottom.
Ctrl+x to boot

see if that helps.

post back.

One time doing this I got to the loading screen, got stuck on 5

---

### Post by RingAnimated on 2012-02-27
Bump ive seen the loading screen twice now.

---

### Post by RingAnimated on 2012-03-02
Bump

---

### Post by RingAnimated on 2012-03-30
I just uninstalled it.

---

