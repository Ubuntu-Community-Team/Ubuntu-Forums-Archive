---
title: "Video related issue"
date: 2006-03-23
forum: General Help
---

### Post by Selbstmord on 2006-03-23
When I play any video, I get a blue stripe on the left side, and the overlay isn't working as it should, as shadows from cursors/windows etc also go blue when hovering over video output, what is wrong and how do I fix it?

Thanks in advance

/F

---

### Post by Ramses de Norre on 2006-03-23
What video card are you using, which driver?
Can you post the contents of your /etc/X11/xorg.conf ?

---

### Post by Selbstmord on 2006-03-23
I should have posted this in my first post, but here goes;

I'm running a fairly old laptop, a Toshiba Satellite Pro 4600, sporting a Trident-something video adapter, and the drivers are the default ones (Mesa GLX  Indirect), and I know that direct rendering doesn't have anything to do with the displacement of the video output, as I had the same blue thing going on on a Toshiba Tecra 8100 with an S3 Savage/MX, moreover, I get the same "error" in any possible video output (VLC, Xine, Totem, MPlayer etc.)

---

### Post by taurus on 2006-03-23
What happens if you change the Driver for your video card to "vesa" in /etc/X11/xorg.conf?  Do you still get the same blue stripe?
```

sudo gedit /etc/X11/xorg.conf

```

---

### Post by Selbstmord on 2006-03-23
No, same thing...
And the blue stripe is not affected by size, it's maybe 5mm wide and stays that size at all times.

Also, the .conf file tells me my graphics card is a "Trident Microsystems CyberBlade/XP"

---

### Post by Selbstmord on 2006-03-24
Nobody gets the same/similar issue?

---

### Post by coront on 2007-05-19
I have this very same problem. I'm currently using a Toshiba satellite 1405 s151 laptop with the same graphic card. Does anyone know how to fix it?

---

