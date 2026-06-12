---
title: "what to do with a .sh file?"
date: 2010-01-21
forum: General Help
---

### Post by phillychease on 2010-01-21
i found this program
[http://www.collanos.com/en/downloads](http://www.collanos.com/en/downloads)
and i want to download it, but the file is a .sh file. 
what do i do with it?

---

### Post by sisco311 on 2010-01-21
Open a terminal (Applications -> Accessories -> Terminal)
type
```
sudo sh
```
type a space, drag the file in the terminal window, then press Enter.

---

### Post by howefield on 2010-01-21
> **phillychease said:**
> i found this program
[http://www.collanos.com/en/downloads](http://www.collanos.com/en/downloads)
and i want to download it, but the file is a .sh file. 
what do i do with it?

Normally, all you need to do is open a terminal (Applications -> Accessories -> Terminal) and navigate to the folder that your file (best to have it in the folder that you want to install it to) is in and type.

```
chmod +x yourfile.sh
```

Followed by..

```
sudo ./yourfile.sh
```

Replace your file with the name of the downloaded file.

---

### Post by jamesisin on 2010-01-21
I recently wrote a script for converting Ape files to FLAC files:

[http://www.soundunreason.com/InkWell/?p=1335](http://www.soundunreason.com/InkWell/?p=1335)

You might enjoy the discussion about how to use the script and where to store it as this will enrich your understanding of scripts and the shell.  (Your terminal runs BASH which is a shell.)

---

### Post by phillychease on 2010-01-21
thanks people!

---

