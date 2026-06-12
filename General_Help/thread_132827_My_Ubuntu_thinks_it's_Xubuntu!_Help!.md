---
title: "My Ubuntu thinks it's Xubuntu! Help!"
date: 2006-02-19
forum: General Help
---

### Post by Leiki on 2006-02-19
No, I didn't just install the xfce environment...

This is wierd! I had a lot of updates to do so I decided to update all of the things. After doing so I saw a light bulb at the top right so I clicked it and said a new linux kernel had been installed so I should restart...

I restarted, and right away I could tell something went wrong. My Windows partiton wasn't listed in my GRUB loader and I had 2 kernels listed (the new one and old one). I went to the new one, and the boot up screen had the Xubuntu splash image! And the text was blue! I was freaking out, but it went to the login screen and everything from there was Ubuntu.

Well, I fixed the GRUB loader by adding my Windows partiton in it, but what about this wierd kernel? Can I delete the new one and keep my old one, or delete my old one and fix my new one? Thank you!

---

### Post by alamba on 2006-02-19
Here's your answer buddy. Don't worry its a trivial matter of boot up graphics.

[http://ubuntuforums.org/showthread.php?p=741873#post741873](http://ubuntuforums.org/showthread.php?p=741873#post741873)

Good luck.

A

---

### Post by Leiki on 2006-02-19
Wow, thanks for the fast and helpful response! Now, should I delete my old kernel or just take it off my GRUB?

---

### Post by alamba on 2006-02-19
Either just let it be (i do) or just hash it out in /boot/grub/menu.lst

A

---

### Post by Lord Illidan on 2006-02-19
[quote=alamba]Either just let it be (i do) or just hash it out in /boot/grub/menu.lst

A[/quote]

I agree with the post above. If you get problems with your kernel, you may need an old kernel to go back to.

---

