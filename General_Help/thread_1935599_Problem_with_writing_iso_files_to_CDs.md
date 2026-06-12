---
title: "Problem with writing iso files to CDs"
date: 2012-03-04
forum: General Help
---

### Post by L R C on 2012-03-04
I've downloaded a Lubuntu iso file because I want to install it on another computer. I tried to writing the iso file to a Sony CD-R and it went well at first, then after it had written the file to the disk, when it said it was "finalising" it, several messages came up saying I had to eject the disk manually, and that I wasn't authorised to use the drive (or something).

I then ran the disk on the computer I wanted Lubuntu on, and it kind of worked, but when it got to the actual installation of the program it said there was an error. I wrote the iso file to another disk but gave up when I got the same messages as before (that I wasn't authorised to use the drive).

Anyone got any ideas?

---

### Post by drdos2006 on 2012-03-04
Make sure it is not a hardware problem first.
Can you remove the data cable and then re-insert the data cable at both ends of the data cable ? That is on the motherboard and the CD burner.
I have had a couple of occasions where this has been the fault with HDDs.

regards

---

### Post by BBQdave on 2012-03-04
> **L R C said:**
> Anyone got any ideas?

More information on the system you are using to burn ISO's would be helpful  :)

If you are using GNU/Linux, I would suggest Xfburn and select the lowest burning speed. You should end up with less coasters. In any operating system, sometimes it is helpful to select the lowest burn speed.

---

### Post by L R C on 2012-03-04
I don't think that's the problem, it can read disks and it kind of managed to write the file...

---

### Post by winh8r on 2012-03-04
First thing to do is check the MD5 checksum of the .iso before you try to burn it.

to do this , open a terminal and 
```

cd /path/to/directory/where/iso/is
```

then enter

```
md5sum lubuntu-11.10-whichever-version -you -have.iso
```

this will print out a string in the terminal, which hopefully should match one of the md5 hashes below depending on which one you have:

```

	

lubuntu-11.10-alternate-amd64.iso
a3d9689f0f63827d8f72a38b5a80767e

	

lubuntu-11.10-alternate-i386.iso
6b2ef531916da95982eb9b9de9dcb19e

	

lubuntu-11.10-desktop-amd64.iso
34adee80fd0e0f37a5b898706988fe49

	

lubuntu-11.10-desktop-i386.iso
a0307761af5a0e3374f65959366d1dcb
```


if these match up then the iso is OK.

burn at the lowest speed possible to prevent errors then when you put it in the target machine, run the integrity checker before the cd boots.

If there are still errors, then run the memtest option on the live cd as it may be possible that you have issues with RAM which are giving errors.

If this test completes without any problem then I would suspect the cd.dvd drive, (clean the lens with some isopropyl alcohol and a lint -free cloth)

then if it still wont work , suspect that the drive is failing.

---

