---
title: "Cannot customize login image"
date: 2011-09-25
forum: General Help
---

### Post by Corey Goettsch on 2011-09-25
Hello all,

I recently had to reinstall Ubuntu 11.04.  Before, I was able to use the Ubuntu Tweak tool to customize my login picture.  When I reinstalled 11.04, I reinstalled the Ubuntu Tweak tool and attempted to reuse the custom login screen.  When I logged out, the picture was purple.  I then used the terminal to let me change login image with the appearance tool at the login screen.  I attempted to use the new login image, but it was still just a solid picture.  When I placed the cursor over the custom image, it simply said "image not found."  I even tried copying the image from my Pictures folder to /usr/share/backgrounds/, and it still would not work.  I am able to use the background images that come with 11.04.  I can customize the desktop background and the GRUB splash screen but not the login screen.  Would someone please let me know how to fix this?

---

### Post by Krytarik on 2011-09-25
Make sure the permissions of the concerning image file are set correctly, readable for all.

Greetings.

---

### Post by Corey Goettsch on 2011-09-25
Thanks so much, Krytarik!  That did the trick.

---

