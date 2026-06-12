---
title: "Garbled Splash Screen"
date: 2012-06-20
forum: General Help
---

### Post by Tuba Respect on 2012-06-20
Hi, this is my first post.
When Ubuntu boots up, the splash screen is garbled.
I am running Ubuntu 12.04 32 bit. Also, I have an eVGA Nvidia GeForce 9800 GT but I am using the generic video driver.
Any help or suggestions would be greatly appreciated.
Thanks

---

### Post by HarryTorry on 2012-06-20
I believe that the splash uses a different drawing method (or vram) to every day use. Your card could possibly be damaged.

When I boot my desktop, there are LOTS of artifacts. The card was severely damaged, I baked it in the oven and it was fine for a few months. Then I got the artifacts again, but I only have them on boot (before an OS loads). I believe this could potentially be the same with you. Are you experiencing the 'garbled-ness' anywhere else?

---

### Post by Tuba Respect on 2012-06-21
No, its just the splash screen. Windows boots fine though.

---

### Post by mike555 on 2012-06-21
Try a different graphics driver.I had that until I used the "addition drivers" and installed the graphics driver .

---

### Post by Redblade20XX on 2012-06-21
Try the "nomodeset" kernel parameter.

-Red

---

### Post by Tuba Respect on 2012-06-21
@mike555 
I switched to the recommended Nvidia driver by using "Additional Drivers" and it worked.
Thanks :-)

---

