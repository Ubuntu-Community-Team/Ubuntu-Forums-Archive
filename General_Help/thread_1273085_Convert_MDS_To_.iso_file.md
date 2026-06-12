---
title: "Convert MDS To .iso file"
date: 2009-09-23
forum: General Help
---

### Post by forgetclosure on 2009-09-23
Hello, i recently downloaded a backup of a ps2 game because my little brother scratched it all up. I am simply looking to convert a .mds file, an .I00 file, and an I01 file (which i'm assuming is similar to .bin/.cue but with multiple parts)

WHY it comes in many pieces completely confuses me, but i just would like to convert those three files to a single .iso if possible.

Thank You,

-Brad

---

### Post by tgeer43 on 2009-09-23
Don't know if this will accomplish what you're after but the only Linux app that I know of that can handle MDS files is CDemu which you can read about/download here:

[COLOR=Blue]_[http://cdemu.sourceforge.net/index.php#about](http://cdemu.sourceforge.net/index.php#about)_[/COLOR]

tgeer

---

### Post by forgetclosure on 2009-09-23
> **tgeer43 said:**
> Don't know if this will accomplish what you're after but the only Linux app that I know of that can handle MDS files is CDemu which you can read about/download here:

[COLOR=Blue]_[http://cdemu.sourceforge.net/index.php#about](http://cdemu.sourceforge.net/index.php#about)_[/COLOR]

tgeer

Yeah, that pretty much works :)
i can mount it using that program and make an .iso out of the files - thanks a lot for your help!

---

### Post by tgeer43 on 2009-09-23
You are quite welcome.

tgeer

---

### Post by forgetclosure on 2009-09-25
> **tgeer43 said:**
> You are quite welcome.

tgeer

darn, it turns out it doesn't support .mds/i00/i01 files.. i read in a few places that i00 and i01 files are actually iso files just with an mds that points to them much like a bin/cue, but i don't know of any programs that understand it.. oh well, i guess i'll have to use alcohol 120% to convert them.. boo windows :(

---

### Post by StuartN on 2009-09-25
> **forgetclosure said:**
> but i don't know of any programs that understand it..

Still boo Windows, but DVD Decrypter names an ISO file exactly like that. When you select the MDS file to burn onto a blank, it will pick up the matching ISO components I00, I01, etc.

Edit: Just a thought, but cat file.I01 file.I02 > file.iso might actually work, all in Linux.

---

### Post by babygenius55 on 2010-04-01
Just for the record, I believe the broken up files are due to file size limitations. I was doing a session just today, and decrypter made iso's fine on my NTFS drive, but had to switch to a fat32 drive to finish...It started breaking them up...I couldn't figure out why until I ran the 'cat file.I01 file.I02 > file.iso' command: It told me the file was too large...DOH! I totally forgot about that. I have since copied all relevant files to one of my ext4 partitions. Let's see what happens.

---

