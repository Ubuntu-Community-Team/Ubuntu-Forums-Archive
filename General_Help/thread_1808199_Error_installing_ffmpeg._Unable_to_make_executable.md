---
title: "Error installing ffmpeg. Unable to make executable file."
date: 2011-07-20
forum: General Help
---

### Post by abuammaar on 2011-07-20
Hi experts,

I tried to install ffmpeg on 7.04(Fiesty Fawn). when i ran  ./configure from terminal window, i got error regarding c compiler that unable to make executable file. Any help is appreciated.

---

### Post by Niocora on 2011-07-20
Right click the file and under permissions, check the "Allow executing file as a program" button. You may need to copy the files to somewhere like your desktop to do this though.

---

### Post by raja.genupula on 2011-07-20
i never have problem like this .
can you give me output of that command exactly .

---

### Post by abuammaar on 2011-07-20
> **Niocora said:**
> Right click the file and under permissions, check the "Allow executing file as a program" button. You may need to copy the files to somewhere like your desktop to do this though.

which file? configure or ffmpeg folder.

---

### Post by raja.genupula on 2011-07-20
output of ./configure

---

### Post by oldos2er on 2011-07-20
> **abuammaar said:**
> I tried to install ffmpeg on 7.04(Fiesty Fawn). when i ran  ./configure from terminal window, i got error regarding c compiler that unable to make executable file. Any help is appreciated.

Feisty is seriously out-of-date, you should upgrade to at least 10.04 or newer.

Your error is caused by not having build-essential installed. You can try the old releases repositories, [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

