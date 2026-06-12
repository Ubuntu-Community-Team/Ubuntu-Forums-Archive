---
title: "md5 verify problems"
date: 2011-02-15
forum: General Help
---

### Post by epz on 2011-02-15
Hello everyone,

I'm having problems verifying a cd's checksum. 
I actually have both the cd's iso and the cd itself, to verify that a copy (from iso) would be burnt fine I extracted iso's files into a folder and then made another iso from them, the result was that iso 1 and iso 2 had different md5  checksums. 
  
    
  Here what I did (more details) 
1) Extracted files from iso with archive manager (extract here from nautilus) 
2) Used  mkisofs -o to create a new iso (with even same name as original) 
3) Checked archives dimension with archive manager (just open from nautilus) 
   
  What's odd (to me) is that the 2 iso have different dimension (and then checksums) but if i open them with file manager i can't seem to find any difference 
To be sure that this was not an April fool (its a lil early for those) I downloaded an Ubuntu iso verified it's checksum, extracted its files and made another one (from the files I extracted as explained above), both with brasero and with mkisofs, only difference was 1mb dimension (which baffled me abit). 

   Yet I haven't tried to verify the checksum copying files from CD (as you have seen I used the iso) so before I go insane and start questioning why I even bother doing it could someone tell me what would be the problem? Why are those checksums different? 
   
     Thanks in advance   

PS: forgive any grammar Horror or lack of informations, it's a lil late here

---

### Post by asmoore82 on 2011-02-15
Was this a bootable CD?

If so, if you didn't take care to carry over the boot data, you won't get the same ISO.

ISO's are tagged with the name of the software that made them.
And I think they are also tagged with a creation date.

And finally, md5's are extremely sensitive to differences, which is what
makes them excellent for verification in the first place. Different
iso/burning tools seem to use different zero paddings at the end of the
image. This doesn't effect data integrity, but it is more than enough to
drastically change the md5. You can use `isoinfo` to get the exact right
size of the ISO...

```
**isoinfo -d -i ubuntu-10.10-netbook-i386.iso**
CD-ROM is in ISO 9660 format
System id: LINUX
Volume id: Ubuntu-Netbook 10.10 i386
Volume set id: 
Publisher id: 
Data preparer id: 
Application id: GENISOIMAGE ISO 9660/HFS FILESYSTEM CREATOR (C) 1993 E.YOUNGDALE (C) 1997-2006 J.PEARSON/J.SCHILLING (C) 2006-2007 CDRKIT TEAM
Copyright File id: 
Abstract File id: 
Bibliographic File id: 
Volume set size is: 1
Volume set sequence number is: 1
[COLOR="Purple"]Logical block size is: 2048
Volume size is: 356297[/COLOR]
El Torito VD version 1 found, boot catalog is in sector 182
Joliet with UCS level 3 found
Rock Ridge signatures version 1 found
Eltorito validation header:
    Hid 1
    Arch 0 (x86)
    ID ''
    Key 55 AA
    Eltorito defaultboot header:
        Bootid 88 (bootable)
        Boot media 0 (No Emulation Boot)
        Load segment 0
        Sys type 0
        Nsect 4
        Bootoff AA 170
```
^The exact size in bytes must be [COLOR="Purple"]these numbers[/COLOR] multiplied together...
```
**echo $(( 2048 * 356297 ))**
[COLOR="Purple"]729696256[/COLOR]
**du -b ubuntu-10.10-netbook-i386.iso**
[COLOR="Purple"]729696256[/COLOR]	ubuntu-10.10-netbook-i386.iso
```

Not all ISO's will be perfect:
```
**isoinfo -d -i thinkpadT61-BIOS.iso | grep size**
Volume set size is: 1
Logical block size is: [COLOR="Purple"]2048[/COLOR]
Volume size is: [COLOR="Purple"]2835[/COLOR]
**echo $(( 2048 * 2835 ))**
[COLOR="Red"]5806080[/COLOR]
**du -b thinkpadT61-BIOS.iso **
[COLOR="Red"]6113280[/COLOR]	thinkpadT61-BIOS.iso
```

We can confirm that the extra data is all zero padding:
```
**dd [COLOR="Purple"]bs=2048 skip=2835[/COLOR] if=thinkpadT61-BIOS.iso 2>/dev/null | hd**
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
0004b000
```

And we can trim the ISO to make it perfect:
```
**dd [COLOR="Purple"]bs=2048 count=2835[/COLOR] if=thinkpadT61-BIOS.iso of=new-thinkpadT61-BIOS.iso**
2835+0 records in
2835+0 records out
5806080 bytes (5.8 MB) copied, 0.017118 s, 339 MB/s
**isoinfo -d -i new-thinkpadT61-BIOS.iso | grep size**
Volume set size is: 1
Logical block size is: [COLOR="Purple"]2048[/COLOR]
Volume size is: [COLOR="Purple"]2835[/COLOR]
**echo $(( 2048 * 2835 ))**
[COLOR="Purple"]5806080[/COLOR]
**du -b new-thinkpadT61-BIOS.iso**
[COLOR="Purple"]5806080[/COLOR]	new-thinkpadT61-BIOS.iso
```

---

### Post by Habitual on 2011-02-15
asmoore82:

Mad props on this write-up. You rock!

---

### Post by epz on 2011-02-16
> **asmoore82 said:**
> Was this a bootable CD?

If so, if you didn't take care to carry over the boot data, you won't get the same ISO.

ISO's are tagged with the name of the software that made them.
And I think they are also tagged with a creation date.

And finally, md5's are extremely sensitive to differences, which is what
makes them excellent for verification in the first place. Different
iso/burning tools seem to use different zero paddings at the end of the
image. This doesn't effect data integrity, but it is more than enough to
drastically change the md5. You can use `isoinfo` to get the exact right
size of the ISO...

```
**isoinfo -d -i ubuntu-10.10-netbook-i386.iso**
CD-ROM is in ISO 9660 format
System id: LINUX
Volume id: Ubuntu-Netbook 10.10 i386
Volume set id: 
Publisher id: 
Data preparer id: 
Application id: GENISOIMAGE ISO 9660/HFS FILESYSTEM CREATOR (C) 1993 E.YOUNGDALE (C) 1997-2006 J.PEARSON/J.SCHILLING (C) 2006-2007 CDRKIT TEAM
Copyright File id: 
Abstract File id: 
Bibliographic File id: 
Volume set size is: 1
Volume set sequence number is: 1
[COLOR=Purple]Logical block size is: 2048
Volume size is: 356297[/COLOR]
El Torito VD version 1 found, boot catalog is in sector 182
Joliet with UCS level 3 found
Rock Ridge signatures version 1 found
Eltorito validation header:
    Hid 1
    Arch 0 (x86)
    ID ''
    Key 55 AA
    Eltorito defaultboot header:
        Bootid 88 (bootable)
        Boot media 0 (No Emulation Boot)
        Load segment 0
        Sys type 0
        Nsect 4
        Bootoff AA 170
```^The exact size in bytes must be [COLOR=Purple]these numbers[/COLOR] multiplied together...
```
**echo $(( 2048 * 356297 ))**
[COLOR=Purple]729696256[/COLOR]
**du -b ubuntu-10.10-netbook-i386.iso**
[COLOR=Purple]729696256[/COLOR]    ubuntu-10.10-netbook-i386.iso
```Not all ISO's will be perfect:
```
**isoinfo -d -i thinkpadT61-BIOS.iso | grep size**
Volume set size is: 1
Logical block size is: [COLOR=Purple]2048[/COLOR]
Volume size is: [COLOR=Purple]2835[/COLOR]
**echo $(( 2048 * 2835 ))**
[COLOR=Red]5806080[/COLOR]
**du -b thinkpadT61-BIOS.iso **
[COLOR=Red]6113280[/COLOR]    thinkpadT61-BIOS.iso
```We can confirm that the extra data is all zero padding:
```
**dd [COLOR=Purple]bs=2048 skip=2835[/COLOR] if=thinkpadT61-BIOS.iso 2>/dev/null | hd**
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
0004b000
```And we can trim the ISO to make it perfect:
```
**dd [COLOR=Purple]bs=2048 count=2835[/COLOR] if=thinkpadT61-BIOS.iso of=new-thinkpadT61-BIOS.iso**
2835+0 records in
2835+0 records out
5806080 bytes (5.8 MB) copied, 0.017118 s, 339 MB/s
**isoinfo -d -i new-thinkpadT61-BIOS.iso | grep size**
Volume set size is: 1
Logical block size is: [COLOR=Purple]2048[/COLOR]
Volume size is: [COLOR=Purple]2835[/COLOR]
**echo $(( 2048 * 2835 ))**
[COLOR=Purple]5806080[/COLOR]
**du -b new-thinkpadT61-BIOS.iso**
[COLOR=Purple]5806080[/COLOR]    new-thinkpadT61-BIOS.iso
```


  Wow, if this isn't a clear explanation I don't know what is, thank you very much for all the details, this answers alot of questions. 
  
  Sadly though won't solve my original problem since some of the cds I'm going to verify are Windows cds that I got years ago bundled with my computer (so I wanted to see if there was some nasty stuff in, I never used Windows since I formatted that pc lol but it appears that Microsoft lets you download isos so I could just grab their checksum and compare.). 
Anyways thank you again it was much appreciated.

---

