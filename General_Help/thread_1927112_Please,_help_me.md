---
title: "Please, help me"
date: 2012-02-17
forum: General Help
---

### Post by samyso on 2012-02-17
Please, I want to decompress a file _*[I]firmware*[/I]_
for a 2000 SAT HD Please note that I use Version ubuntu 10.04 lts
file name :
..................
NxpRom.bin 
..................
Thank you all

---

### Post by cryptotheslow on 2012-02-17
I wouldn't have thought a .bin file can be decompressed as it is typically a binary file.

Check the drive manufacturer's site for instructions on how to flash the firmware to the drive if that is what you are trying to do.

---

### Post by Khayyam on 2012-02-17
> **samyso said:**
> Please, I want to decompress a file _*[I]firmware*[/I]_
for a 2000 SAT HD Please note that I use Version ubuntu 10.04 lts
file name :
..................
NxpRom.bin 
..................

Sometimes bin files are just zip archives, if this is the case then you can run 'unzip' on it and uncompress. If its a windows installer then you probably won't be able to do anything with it under linux.

You can check the and see what the file is with the following:

```
file NxpRom.bin
```

HTH ...

---

### Post by Leppie on 2012-02-17
If this is a linux driver, you should be able to run it:
```
sudo bash ./NxpRom.bin
```

---

### Post by samyso on 2012-02-17
I thank you all for your responses
 But
 How do I use and is cramfs [COLOR=#000000][COLOR=#0000BB]and [/COLOR][/COLOR]Mkcramfs unzip and re-compress a file bin
Or
How to apply JavaScript Firmware Modification Kit to dismantle the bin file?

---

