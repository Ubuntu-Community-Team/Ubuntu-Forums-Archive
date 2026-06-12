---
title: "Is there a way to make hibernate NOT close my programs?"
date: 2012-04-16
forum: General Help
---

### Post by TheGuyWithTheFace on 2012-04-16
I recently switched from windows 7 to Ubuntu 11.10 Oneric Ocelot, and one of the only things I've missed so far is hibernating. I know, I know, Ubuntu supports hibernating, but for some reason it closes my programs when it does this. Doesn't that defeat the purpose??? Is there any way to fix this???

---

### Post by TheGuyWithTheFace on 2012-04-21
Ok, so I've found this article:

[http://manpages.ubuntu.com/manpages/oneiric/man5/hibernate.conf.5.html](http://manpages.ubuntu.com/manpages/oneiric/man5/hibernate.conf.5.html)

and It looks like if I changed a couple boolean values (GaimRestoreStatus, maybe?), I could make hibernate leave my programs alone. My question is, what the heck is Gaim?

More importantly, though, for some reason the file it's talking about, I can't find. Am I doing something wrong??? 

:confused:

---

### Post by brainwash on 2012-04-21
The instant messaging client Pidgin was called Gaim before it has been renamed.

Well, does your system really restore the hibernated session or is it just starting a fresh session? You could verify it by typing **uptime** in the terminal. Furthermore, did you encrypt your home directory on install? This would also encrypt the swap partition (random key) and therefore disable the ability to load the hibernated session.

The output of
```
cat /var/log/pm-suspend.log
```
might be helpful to find a solution for your problem.

---

### Post by TheGuyWithTheFace on 2012-04-21
> **brainwash said:**
> The instant messaging client Pidgin was called Gaim before it has been renamed.

Well, does your system really restore the hibernated session or is it just starting a fresh session? You could verify it by typing **uptime** in the terminal. Furthermore, did you encrypt your home directory on install? This would also encrypt the swap partition (random key) and therefore disable the ability to load the hibernated session.

The output of
```
cat /var/log/pm-suspend.log
```
might be helpful to find a solution for your problem.

Well, I ran that cat command, but what am I looking for? I got a long list of... something, but I don't know what it's supposed to be...

and yeah, I'm pretty sure I encrypted my home folder. Is there a way I can have my home folder encrypted and still use hibernate properly? If not, how could I disable the encryption on my home directory? And no, I don't think it restores my hibernated session, because after hibernating, everything I had running is gone. It's like I had just shut down instead of hibernating!

:(

---

### Post by brainwash on 2012-04-22
Alright, there is no need to remove the encryption of your home folder. You can simply revert the also encrypted swap partition back to normal state by following this guide:

[http://www.logilab.org/blogentry/29155](http://www.logilab.org/blogentry/29155)

Read the instructions carefully and make sure, you apply the changes to the correct device (/dev/sda**X**).

By doing so you will break the security concept of having an encrypted home folder, because sensitive data from that folder, which is somtimes loaded into RAM, will be saved on the now unencrypted swap partition during hibernation.

---

### Post by TheGuyWithTheFace on 2012-04-22
> **brainwash said:**
>  
By doing so you will break the security concept of having an encrypted home folder, because sensitive data from that folder, which is somtimes loaded into RAM, will be saved on the now unencrypted swap partition during hibernation.

I'll take that risk. Thanks!

---

### Post by TheGuyWithTheFace on 2012-04-22
Well, apparently my swap partition is messed up in some way, so once I'm done backing up my hard drive, I think I'll try deleting my current swap and just making a new one. Is that a good idea?

---

### Post by TheGuyWithTheFace on 2012-04-22
WAIT!!! What am I thinking??? Precise Pangolin stable comes out in 4 days, I'll just upgrade to it and hope for the best.

...now I feel dumb...

---

### Post by TheGuyWithTheFace on 2012-07-07
So, I installed precise, and love it! I managed to get hibernate working, and was satisfied. However, a month or so ago, I broke my system, and had to re-install. Unfortunately, now I can't get hibernate working right. I followed these instructions to enable it:

[http://www.howtogeek.com/113923/how-to-re-enable-hibernate-in-ubuntu-12.04/](http://www.howtogeek.com/113923/how-to-re-enable-hibernate-in-ubuntu-12.04/)

and these steps to make sure my swap partition wasn't encrypted:

[http://www.logilab.org/blogentry/29155](http://www.logilab.org/blogentry/29155)

and I can click hibernate and all, but it still closes my programs like it used to, as if I had merely clicked shut down.

any new suggestions?

---

### Post by TheGuyWithTheFace on 2012-07-12
... Bump?

---

