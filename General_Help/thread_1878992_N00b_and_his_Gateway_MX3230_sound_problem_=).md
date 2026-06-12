---
title: "N00b and his Gateway MX3230 sound problem =)"
date: 2011-11-10
forum: General Help
---

### Post by Finlay09 on 2011-11-10
Hey everyone, I've had Ubuntu install in a dual bot configuration on a couple of desktops with no issues, but this laptop is another story. it's a Gateway MX3230 and I'm using build 11.10 I haven't had any problems with the screen or the WiFi, but what settings I have do nothing to get sound working. I'm just hoping that there's a driver or a way to tweak a driver or something to get this working. would LOVE to use Ubuntu alone on this computer, especially seeing XP is nearing end of life. thanks for any and all help!



Cheers,JF

---

### Post by jonobr on 2011-11-10
1. Open Volume Control (double click speaker icon upper left in gnome)
2. go to Options (File > Options
3. Make sure "External Amplifer,0" is checked
4. close
5. Click the "Show Switches" arrow
6. and UNCHECK External Amplifier

---

### Post by Finlay09 on 2011-11-10
i don't think that's for the same version of ubuntu as mine, my speaker icon is in the upper right corner 11.10

---

### Post by jonobr on 2011-11-10
BTW


Totally taken from [this Thread]("http://ubuntuforums.org/showthread.php?t=1015207")

---

### Post by Rodney9 on 2011-11-10
I cannot claim to have come up with this myself, searched google MX3230 Gateway linux, anyuway found this -

Some 18yo on his blog discussed this regarding the MX3230 Gateway laptop. 

Seems like it's an issue with the Via sound chip (and yes, it runs a realtek chip for some reason). 

Anyways, you have to go into the terminal and type alsamixer  and disable the external amplifier option. 

don't just turn it down, make sure you switch it off (tab over the EXT amp and hit the <period> key. 

If that does not work have a look here - 
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)


Rodney

---

### Post by Finlay09 on 2011-11-10
yea, i saw it earlier when searching the interwebs. same laptop, but that person was running xubuntu?

---

### Post by Finlay09 on 2011-11-10
cool i'll try that out and i'm blown away by the quick responses guys, you set a standard for all forums to follow :)

---

### Post by Rodney9 on 2011-11-10
> **Finlay09 said:**
> yea, i saw it earlier when searching the interwebs. same laptop, but that person was running xubuntu?
 Doesn't matter, alsamixer should work , did it work ?

---

### Post by jonobr on 2011-11-10
Luck of the draw,

You will post another day and it will go unanswered for days:-)
 

When that happens BUMP is your friend!!:D

---

### Post by Finlay09 on 2011-11-10
can't seem to find an external amplifier option, still looking tho

---

### Post by Finlay09 on 2011-11-10
ok, i found a setting in there labeled external, disabled it with period, but still no sound

does it matter that i'm currently on live cd? and not a full install

---

### Post by jonobr on 2011-11-10
A good question, I dont know.

I assumed you had the full thing on there.

Reading the wiki page on the Live cd it doesnt mention audio specifically
it only says ir will.......

> give a 'demo' session on a machine before installing or upgrading

    checks hardware works as expected

    check the look & feel of the distro 

Now by hardware , I dont know if that covers audio......

I wish I could help you out on that one, but I dont know.... :(

---

### Post by Finlay09 on 2011-11-10
i would assume audio would be a big item to ensure compatibility

---

### Post by jonobr on 2011-11-10
We are agreed on that.... but "we" aint part of "they".
As said, I dont know.
Id be reluctant to get you to install the full thing only to have the same problem.

---

### Post by Finlay09 on 2011-11-10
yea, this thing was a handful to find drivers for XP.... anyone know someone who can write/tweak drivers

---

