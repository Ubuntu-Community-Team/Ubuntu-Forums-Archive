---
title: "Unity Desktop Shows Blank/Empty Screen"
date: 2011-10-30
forum: General Help
---

### Post by sxeABz on 2011-10-30
Hi, Ubuntu GURUS!


[Image 1]("http://i42.tinypic.com/352njo4.jpg")
[Image 2]("http://i44.tinypic.com/2l5hu.jpg")
[Image 3]("http://i43.tinypic.com/34xnnk0.jpg")

This is how i welcomed by Ubuntu 11.10 Unity Desktop, Nothing changes whether i "TRY UBUNTU" from LiveCD or install fresh copy of it. i can't see any dialog boxes of any app though i can tell they are open and running, and here are my necessary Sys info:

System Model:
IBM eServer xSeries 205 8480
CPU:
2.4 GHz
Memory:
1GB (Just in case you wanna know)
VGA:
nVidia Quadro FX 1100 (128MB)
3D Drivers version:
173.14.28

Just let me know if you want any further info, i desperatly need help, Any help would be very much appreciated, Thanks in advance.

P.S: Now you might ask what was i doing before posting this thread, well, the answer is; i was searching the whole Ubuntu forum and other related blogs. Thanks again.

---

### Post by collisionystm on 2011-10-30
Have you installed the official Nvidia drivers? It sounds to me that the driver is broken.

---

### Post by sxeABz on 2011-10-30
Well, how can i if i can't get to any option. i'm afraid i don't

---

### Post by sxeABz on 2011-10-31
Anyone, Where can i post this thread to get to know the answer?

---

### Post by effenberg0x0 on 2011-10-31
1) Getting to a terminal

a) At this screen, try to press Ctrl+Alt+T to open a terminal. If you can open a usable Terminal Window, jump to 2, otherwise go to b.

b) If you can't get a usable Terminal Window, try to Ctrl+Alt+F6, which should take you to a VT (Virtual Terminal). If you can see the VT, login with your user and password and go to 2. If you can't switch to the VT and login, go to c.

c) Restart the PC holding the shift key, to see the Grub boot menu, and, at the menu, select the recovery option. Let it boot until you are at a prompt. Go to 2.

2) Run this:
```

cd /tmp
wget www.itdata.com.br/tmp/oneiric.sh .
sudo chmod +x oneiric.sh
sudo ./oneiric.sh

```

---

### Post by sxeABz on 2011-11-01
Still no progress...

[IMG]http://i40.tinypic.com/ea4oc6.jpg[/IMG]

[IMG]http://i40.tinypic.com/r2q9fs.jpg[/IMG]

These are the messages i got right before nVidia drivers file execution. but the download go very smooth, Hope these error messages help you to know the basic problem :)

---

### Post by effenberg0x0 on 2011-11-01
When you press OK in this screen you probably get to a console prompt. At this prompt, run the following commands:

```
sudo service lightdm stop
sudo kill -s $(pidof lightdm)
sudo service gdm stop
sudo kill -s $(pidof gdm)
sudo killall -s KILL /usr/bin/X
```

*Notice the X in /usr/bin/X is uppercase ok?

Then run... 
```

sudo ./NVIDIA*
```... again and see if the installation proceeds beyond this screen.

** Press OK for all the questions of the NVIDIA install. Let me know when the install finishes. We need to do a few more couple things.

---

### Post by Mark Phelps on 2011-11-01
My desktop looked like your first two pictures after I made the mistake of trying to tweak a Compiz option using CCSM.  I had to jump to the CLI and enter lots of commands to uninstall compiz and unity, clean up the remainder, and reinstall compiz and unity.

If you think that will help your situation, see the details in the link below:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by sxeABz on 2011-11-02
Thank You Effen and Mark my problem is very much solved through booting Ubuntu with Windows 7 though i don't like doing it, Anyway, i let Ubuntu download and install all the packages during installation setup and i'm now able to work with Ubnity 2D version but login with Classic still shows same result but Effen if you want then i can dig deeper for this problem with your help, Mark, i'll keep this link for future ref, who knows if i got myself situation like this and again Thank you both :)

---

