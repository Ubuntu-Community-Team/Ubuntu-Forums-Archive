---
title: "Red dash"
date: 2012-06-25
forum: General Help
---

### Post by masterrogue on 2012-06-25
I have had this red circle with a white dash in it ever since I upgraded  to Precise Pangolin, can anybody tell me what to do about this? I have  searched, and found nothing that has any missing dependencies. I've  reinstalled most files, nothing. When I try to work in terminal, it  basically flashes the same message at me.
[IMG]http://img.photobucket.com/albums/v157/MichiganRocks/Home%20Site/Screenshotfrom2012-06-25084440.jpg[/IMG]

---

### Post by rubylaser on 2012-06-25
Have you tried opening the terminal and running apt-get?  It should tell you what the problem is.

```
sudo -i 
apt-get update && apt-get upgrade
```

---

### Post by masterrogue on 2012-06-25
I've tried it, and I get a similar message. I'll try again...

---

### Post by masterrogue on 2012-06-25
Indicates that everything is fine, but I still have error indicator.:mad:

---

### Post by rubylaser on 2012-06-25
What is the output when you try this?

```
apt-get -f install
```

---

### Post by masterrogue on 2012-06-25
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Then it's done, and my problem still exists....

---

### Post by masterrogue on 2012-06-25
Looking at what I just posted, I see that it doesn't actually say that "building my dependency tree" is done. Is there something that I could do there?

---

### Post by GreatDanton on 2012-06-25
The best solution for all upgrading problems is to start from scratch. Download Precise pangolin, make live cd/sub, grab external Hard disk and backup all important data. After that just reinstall the system and your problem will disappear.

---

### Post by masterrogue on 2012-06-26
Decided you were right. Backed up my files, formatted my hard drive, and loaded a brand new Precise Pangolin. All the issues seem to have disappeared.

---

### Post by rubylaser on 2012-06-26
Glad to hear it.  If you have a chance, please mark the thread as solved under the Thread Tools at the top.

---

