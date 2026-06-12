---
title: "FireFox Is Acting Crazy"
date: 2009-09-15
forum: General Help
---

### Post by WalkerInTheWoods on 2009-09-15
Help! FireFox has gone crazy on me. When I open it up it doesn't go to my home page, it doesn't do anything. If I click on the home button it takes me to the Mozilla homepage. No addresses are showing up in the address bar or at the bottom. All my bookmarks are gone!

---

### Post by uylug on 2009-09-15
Quick question: Have you just upgraded to Firefox 3.5?

---

### Post by WalkerInTheWoods on 2009-09-15
I updated whatever FireFox update was in the Ubuntu repository.

---

### Post by Yannick Le Saint kyncani on 2009-09-15
You could delete your ~/.mozilla/firefox and start anew

---

### Post by WalkerInTheWoods on 2009-09-15
It looks like I may have to do so unless someone has a better idea.

> **Yannick Le Saint kyncani said:**
> You could delete your ~/.mozilla/firefox and start anew

---

### Post by lovinglinux on 2009-09-15
> **WalkerInTheWoods said:**
> It looks like I may have to do so unless someone has a better idea.

See **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

---

### Post by WalkerInTheWoods on 2009-09-16
> **lovinglinux said:**
> See **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

I fixed it by renaming the firefox folder and starting from scratch. I then restored my bookmarks from the back up file in the renamed folder.

If this happens again I will try this. Thank you.

---

### Post by lovinglinux on 2009-09-16
> **WalkerInTheWoods said:**
> I fixed it by renaming the firefox folder and starting from scratch. I then restored my bookmarks from the back up file in the renamed folder.

If this happens again I will try this. Thank you.

That works too. The solution provided in my tutorial just allows you to fix the problem without messing with other FF profile files, thus preserving settings, cookies, passwords, extensions and so on.

---

### Post by uylug on 2009-09-16
Yes. I had the same problem after the upgrade and I solved it the same way as you did.

---

