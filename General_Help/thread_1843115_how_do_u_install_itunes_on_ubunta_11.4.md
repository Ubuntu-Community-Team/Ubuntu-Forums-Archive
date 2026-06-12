---
title: "how do u install itunes on ubunta 11.4"
date: 2011-09-12
forum: General Help
---

### Post by mattpl1981 on 2011-09-12
im new here and trying to figure everything out here. how do you install itunes on ubuntu 11.4?

---

### Post by ubudog on 2011-09-12
iTunes cannot be natively installed in Ubuntu.

Have you tried Wine yet?  

Install Wine like so:
```
sudo apt-get install wine
```

Then, download the installer, and open it with Wine.

Regards,
ubudog

---

### Post by mattpl1981 on 2011-09-12
where am i supose to type that code in at?

---

### Post by pqwoerituytrueiwoq on 2011-09-12
i tunes if a bit buggy in wine
the default audio player should handle a ipod just fine
edit:
in the terminal

---

### Post by ubudog on 2011-09-12
> **mattpl1981 said:**
> where am i supose to type that code in at?

In a terminal.

On 11.04, search for "Terminal" using the Dash (little Ubuntu logo at the top of the screen)

On 10.10 and below (or 11.04 on Classic), it can be accessed by clicking Applications>Accessories>Terminal.

Note: After that command it will ask for your password.  Type it, but it will not show up (for security).  Enjoy.

---

### Post by mattpl1981 on 2011-09-12
so you can plug a ipod in and play?

 i want itunes so i can add new songs to my ipod

---

### Post by ubudog on 2011-09-12
> **mattpl1981 said:**
> so you can plug a ipod in and play?

 i want itunes so i can add new songs to my ipod

I believe so, yes.  It just can't run natively on Linux.  (that's why you have to use Wine)

---

### Post by mattpl1981 on 2011-09-12
i have wine installed but not sure how to use it. it shows as wine configure and havent got past that yet. im new to this and havent figured it out yet.

---

### Post by jandrusk on 2011-09-12
Always had problems with ITunes in Wine, so I dumped that big fat bloated big and just use Banshee.

---

### Post by pqwoerituytrueiwoq on 2011-09-12
open the itunes exe with wine to install it
the default is the file roller

just try banshee with your ipod it will most like work out of the box better than itunes will in wine odds are itunes will not see your ipod

---

### Post by ubudog on 2011-09-12
> **mattpl1981 said:**
> i have wine installed but not sure how to use it. it shows as wine configure and havent got past that yet. im new to this and havent figured it out yet.

Now, download the iTunes installer, save it to say your Desktop, go to your desktop, right click the .exe file, and select Open with Wine.

---

### Post by mattpl1981 on 2011-09-12
when i type in itunes nothing shows up

---

### Post by ubudog on 2011-09-13
> **mattpl1981 said:**
> when i type in itunes nothing shows up

What?  

Right click the .exe file.  Then, select Open with Wine Windows Program Loader.  The installer will open.

---

### Post by haqking on 2011-09-13
see here for more info on itunes in Linux

[http://www.psychocats.net/ubuntu/itunes](http://www.psychocats.net/ubuntu/itunes)

and for a simple run down of wine see here [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

