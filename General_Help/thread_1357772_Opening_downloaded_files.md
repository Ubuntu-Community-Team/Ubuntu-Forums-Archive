---
title: "Opening downloaded files"
date: 2009-12-17
forum: General Help
---

### Post by kat9505 on 2009-12-17
I downloaded WINE so that I can have iTunes on Ubuntu (you can do this). I downloaded iTunes but the file for the setup in "Downloads" won't open. It says "An error  occurred while loading the archive". I can't open any downloads. Please help! It is probably something simple, but I'm new to Ubuntu. :confused:

---

### Post by synapsys on 2009-12-17
Right click on the file.

Select "open with wine windows program loader"

---

### Post by kat9505 on 2009-12-17
> **synapsys said:**
> Right click on the file.

Select "open with wine windows program loader"


This isnt working for me. i dont see what you are talking about. it doesnt say that.

---

### Post by ubudog on 2009-12-17
Go to the downloads folder, highlight the file (most likely .exe), right click on it and select open with wine windows program loader.
That's the easiest I can put it.

---

### Post by synapsys on 2009-12-17
> **kat9505 said:**
> I downloaded WINE 

Did you download and install wine or just download it?

---

### Post by Julita on 2009-12-17
Why do you need iTunes? If for Apple ipods and etc, then there are Linux programs.

---

### Post by Marlonsm on 2009-12-17
Go to the software centre and get "PlayOnLinux", its said to install iTunes with no hassle.
(It's basically Wine configured for certain applications)

---

### Post by ubudog on 2009-12-17
> **Julita said:**
> Why do you need iTunes? If for Apple ipods and etc, then there are Linux programs.

Yes, Rythmbox is a very nice app and comes with Ubuntu. It can detect ipods and you just drag and drop your music onto the ipod. You can also view podcasts.

---

### Post by Julita on 2009-12-17
> **ubudog said:**
> Yes, Rythmbox is a very nice app and comes with Ubuntu. It can detect ipods and you just drag and drop your music onto the ipod. You can also view podcasts.
I was actually thinking about gtkpod ;) I knew nothing about Rhythmbox, though. I don't use it.

---

### Post by kat9505 on 2009-12-17
ok thanks everyone... im trying everything and ill let you know what:) works.

---

### Post by kat9505 on 2009-12-17
> **Marlonsm said:**
> Go to the software centre and get "PlayOnLinux", its said to install iTunes with no hassle.
(It's basically Wine configured for certain applications)

Thank you so much! This worked for me. I like these forums- I get so many responses in so little time.

---

### Post by kat9505 on 2009-12-17
now i have a new problem... i have downloaded itunes using playonlinux  but i cant start itunes.

---

### Post by ubudog on 2009-12-18
Maybe you need to open it as root.  Open a terminal from Applications>Accessories>Terminal and type ```
sudo playonlinux
```, type your password (you won't see it for security reasons) and press enter.  Then you should be able to start it.

---

