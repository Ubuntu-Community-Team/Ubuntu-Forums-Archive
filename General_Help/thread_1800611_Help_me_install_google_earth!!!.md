---
title: "Help me install google earth!!!"
date: 2011-07-09
forum: General Help
---

### Post by HennesseyRockZ on 2011-07-09
hey im having a bit of trouble installing google earth because i dont know how to install bin files

---

### Post by haqking on 2011-07-09
> **HennesseyRockZ said:**
> hey im having a bit of trouble installing google earth because i dont know how to install bin files


well bin files are source and need compiling.

however google earth is in the repos so you should find it in software centre or synaptic.

It is not the absolute latest version but works just great ;-)

what version of ubuntu you talking about ?

there is a TUT here at [http://tombuntu.com/index.php/2010/05/02/how-to-install-google-earth-in-ubuntu-10-04/](http://tombuntu.com/index.php/2010/05/02/how-to-install-google-earth-in-ubuntu-10-04/) for 10.04 you may need to modiy it slightly as it is from last year

---

### Post by HennesseyRockZ on 2011-07-09
Well sypnaptic package manager says its install but it isnt, i typed google earth in applications and it's nowhere to be found

---

### Post by haqking on 2011-07-09
> **HennesseyRockZ said:**
> Well sypnaptic package manager says its install but it isnt, i typed google earth in applications and it's nowhere to be found

so its not under under your internet menu ?

have you rebooted since install ?

or if it is installed then it should be found in /usr/bin and then add it to your launcher

---

### Post by waynefoutz on 2011-07-09
[http://www.google.com/earth/download/ge/agree.html]("http://www.google.com/earth/download/ge/agree.html")

The .deb download is right there in that link.

---

### Post by HennesseyRockZ on 2011-07-09
Still cant find it xD

---

### Post by pqwoerituytrueiwoq on 2011-07-09
> **waynefoutz said:**
> [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

The .deb download is right there in that link.
+1
if this command gives you *x86_64*
[FONT=Courier New]uname -m[/FONT]
select 64 bit ubuntu (option 2)

---

### Post by HennesseyRockZ on 2011-07-09
Still having problems, i think i need to know how to install a bin file

---

### Post by oldos2er on 2011-07-09
Once you've downloaded GooglEarthLinux.bin, open a terminal, "cd" to the folder where the *.bin is, run ```
chmod +x GoogleEarthLinux.bin

sudo ./GoogleEarthLinux.bin
```

---

