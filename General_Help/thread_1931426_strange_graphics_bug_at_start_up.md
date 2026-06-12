---
title: "strange graphics bug at start up"
date: 2012-02-25
forum: General Help
---

### Post by xtremesupremacy3 on 2012-02-25
Hello.

Kinda two questions here, but I'm mostly concerned about the first one.

I installed Ubuntu Oneiric cleanly (no update) as I always do.
This gave me Unity which I enjoyed for a long time.
However, I seen KDE 4.8 in a review and having disliked KDE I was intrigued, so installed the kde-desktop on top and to be honest with you, I love it.
I kept lightdm because I think it's prettier.
The problem I now have though is that 4/5 times when starting my laptop, I get a really ugly graphic glitch. When I don't have it, then it just loads the splash but this requires a hard reset (see photo's).
Anyone know how to fix this?

Question 2 is easier.
I have 500Gig on my HDD, and only have 100 left.
I have downloaded many games, lots of photo's, music. You know the score.
However, I only want KDE now.
Is there a way I can get rid of everything (Unity, Unity2D etc) and just have KDE? I don't have a spare hard drive to use for backup so I prefer the removal of Ubuntu instead of a new install.

Thanks in advance

---

### Post by xtremesupremacy3 on 2012-02-25
nobody?

---

### Post by josephmills on 2012-02-25
there is this if you want just KDE 
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
as far as the plymouth boot splash have you tried to change it to a different one ? 
```
sudo update-alternatives --config text.plymouth  

```
then 
```
sudo update-alternatives --config default.plymouth 

```
then run 
```
 sudo update-initramfs -u 
```

hope that this helps

---

### Post by xtremesupremacy3 on 2012-02-25
from what I can see, the plymouth fix seems to have worked.
Probably too early to tell but having restarted it, it has not gone all ugly on me.
Thanks for that, I will look into link that you sent, thank you

---

### Post by josephmills on 2012-02-25
Great I am glad that things worked out for ya. you can also remove any unwanted plymouth boot splashs they are under /lib/plymouth/ 
but no need to if everything is fixed. Once again have a good one and I am glad to see that you are up and running again.

---

