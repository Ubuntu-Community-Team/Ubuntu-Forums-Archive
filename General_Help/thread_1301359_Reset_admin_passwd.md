---
title: "Reset admin passwd?"
date: 2009-10-26
forum: General Help
---

### Post by gregapan on 2009-10-26
**[B]I need to reset my admin password since I've forgotten it, but Le Catch 22 seems to be that one needs to know **it to reset it. I know my regular password. 

Here's the catch: is there any way to do this without resorting to the pre-boot reset? My laptop monitor is mostly kaput, and my main monitor does not receive feed until bootup, making it extremely difficult to do it that way.



[/B]

---

### Post by aysiu on 2009-10-26
This is how you do it:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by gregapan on 2009-10-26
Um, NO, it's not!

If you had read my post, you would know that I do not have access to my screen in the preboot environment.

Therefore, I was asking if there are alternative methods.

---

### Post by aysiu on 2009-10-26
> **gregapan said:**
> Um, NO, it's not!

If you had read my post, you would know that I do not have access to my screen in the preboot environment.

Therefore, I was asking if there are alternative methods.
The alternative method is in the YouTube video at the bottom of the page.

If you can't boot a live CD, you may have to remove the drive and put it in another computer or an external enclosure.

---

### Post by gregapan on 2009-10-26
Interesting.

However, it still requires my admin password after Step 3. (I get a blacked out screen and a request for passwd window)

I tried to skip that step, but naturally the system would not let me copy that "shadow" file.

---

### Post by nothingspecial on 2009-10-26
Can you access your laptop remotely using ssh - ie do you have another computer on your network?

---

### Post by P4man on 2009-10-26
If by admin password you mean root password, then you probably havent forgotten it, you have never known it:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you manually unlocked root account and changed its password then that might not have been the smartest thing to do.

---

### Post by aysiu on 2009-10-26
> **gregapan said:**
> Interesting.

However, it still requires my admin password after Step 3. (I get a blacked out screen and a request for passwd window)

I tried to skip that step, but naturally the system would not let me copy that "shadow" file.
If the live CD requires a password, then it's somehow corrupted, and you should re-download (preferably using BitTorrent) the .iso.

---

