---
title: "i dont see anything"
date: 2011-02-09
forum: General Help
---

### Post by verder veremem on 2011-02-09
hi,
i cant talk english well but i will try to expalin my problem.
i set up ubuntu :( however i cant see my disks

i am a project manager and my all project is my harddrive(D). and i formated windows when i set up ubuntu(by mistake)

my drive d is still staying but i cant see :(
if i dont see my project i am sure that they send away to me :(
please help me.i took screenshot


[COLOR=Red]***i cant set up windows becasue it is not NTFS :(***[/COLOR]

[http://i53.tinypic.com/9k5eub.png](http://i53.tinypic.com/9k5eub.png)

[http://i52.tinypic.com/339kn6f.png](http://i52.tinypic.com/339kn6f.png)

---

### Post by verder veremem on 2011-02-09
please help me,please :/

---

### Post by verder veremem on 2011-02-09
hi,
i cant talk english well but i will try to expalin my problem.
i set up ubuntu :( however i cant see my disks
i have project in harddirve and i dont see. 

my drive d is still staying but i cant see :(
if i dont see my project i am sure that they send away to me :(
please help me.i took screenshot


[COLOR=Red]***i cant set up windows becasue it is not NTFS :(***[/COLOR]

[http://i53.tinypic.com/9k5eub.png](http://i53.tinypic.com/9k5eub.png)

[http://i52.tinypic.com/339kn6f.png](http://i52.tinypic.com/339kn6f.png)

---

### Post by verder veremem on 2011-02-09
anybody have an idea

---

### Post by sikander3786 on 2011-02-09
I am sorry to say but it looks like you chose "Use entire disk" during the Ubuntu installer and it deleted all the partitions and created new one's thus assigning all the space to Ubuntu.

If your project was that important and you need to recover it, IMMEDIATELY stop using your current system. Instead boot an Ubuntu Live CD/USB and try recovering your data.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by bapoumba on 2011-02-09
Threads merged.

I would be better not to start different threads on the same subject (and wait around 24h before bumping) thanks.

---

### Post by Mark Phelps on 2011-02-09
My own personal experience is that MS Windows OS utilities are better at recovering MS Windows partitions, and Linux utilities are better at recovering Linux partitions ...

That said, you should IMMEDIATELY stop using the PC with the overwritten partition.  Every time you write to that, you seriously compromise your ability to recover anything from that drive.

Instead, you need to do the following:
1) Remove the affected drive from the PC
2) Find an MS Windows-based PC
3) Using the above PC, go to the Runtime Software website and download their trial version of GetDataBack for NTFS.  Install that on the Windows PC
4) Connect your affected drive to the Windows PC
5) Run GetDataBack and see how well it detects your original data
6) If it does it well, you will have to purchase the actual product in order to recover the data.

And before anyone flames me for mentioning the dreaded "commercial software!", if this is your livelyhood, then how much is it worth to get your work back?

---

