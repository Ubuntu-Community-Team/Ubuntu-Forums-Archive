---
title: "Lag issue?"
date: 2009-06-27
forum: General Help
---

### Post by wobbmike on 2009-06-27
ive recently switch from windows vista to ubuntu. and im really happy with the results except for one little problem. i cannot figure out why in firefox web pages lag and are scratchy? dont really know how to explane it but just scrolling the page it lags. my specs are

Intel Pentim dual core 2.2 GHz
7600 GS 512 MB Nvidia PCI-e x16
1.5 GB of ddr 667 ram

in windows or any other operating system ive ran on this machine this has never been an issue? it's probably something little im just missing. haha but anyways if you can shed some light it'd be much appriciated, thanks.

- Mike

---

### Post by TeoBigusGeekus on 2009-06-27
Why don't you try some other browsers? Opera or Epiphany for example.
If you search these forums a lot of people are complaining about latest Firefox's performance (personally I don't know - Opera user).

---

### Post by wobbmike on 2009-06-27
ive tryed opera & it wont load. it installs but when i go to applications > internet > Opera i click it and it does nothing

---

### Post by TeoBigusGeekus on 2009-06-27
Why is that?
Open a terminal, type
```
opera
```
and post us any error messages.

---

### Post by wobbmike on 2009-06-27
alright tryed it & this is what i got

michael@michael-desktop:~$ opera
The Opera binary is not located at "/home/michael/lib/opera/9.64/opera".
Please modify the wrapper script at "/home/michael/bin/opera".
michael@michael-desktop:~$ 

btw thanks for the help. :)

---

### Post by TeoBigusGeekus on 2009-06-27
We will then uninstall it and install again.
```
sudo apt-get purge opera
```
and then 
```
sudo apt-get install opera
```

---

### Post by wobbmike on 2009-06-27
alright it uninstalled correctly but i got the exact same message after i reinstalled it & tryed to start it up threw terminal.

---

### Post by Arup on 2009-06-27
Have you installed nvidia drivers, FF will crawl unless drivers are installed. Have you installed correct version of Opera?

---

### Post by wobbmike on 2009-06-27
yeah i have. i had a hell of a time installing them to :( & as for opera still no luck. & yeah i got the right version. thanks :)

dono if this pic will help but??

[http://img208.imageshack.us/img208/5318/driversz.png](http://img208.imageshack.us/img208/5318/driversz.png)

---

