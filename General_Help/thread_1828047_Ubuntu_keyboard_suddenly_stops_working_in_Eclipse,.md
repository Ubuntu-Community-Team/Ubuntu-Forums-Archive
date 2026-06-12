---
title: "Ubuntu keyboard suddenly stops working in Eclipse, Chrome, Firefox, etc"
date: 2011-08-18
forum: General Help
---

### Post by ryandao on 2011-08-18
I have this annoying problem with my Ubuntu 11.04. My keyboard just randomly stops to respond when I'm using some certain programs. So far that problem happens to programs that have tabs like Eclipse, Chrome, Firefox. I've been searching for a long time for solutions but no luck. Any help is much appreciated.

---

### Post by An Sanct on 2011-08-18
Welcome to the forums!

What kind of a keyboard are you using? (USB/PS2)

I have a similar problem. The keyboard seem so "stick" with a key down programmatically. I have found out, that in my case it is a know issue somewhere in kernel :(

I also found out, that this does not happen with USB keyboards, but only with PS2 (which I use...)

PS. running Maverick 64b

---

### Post by ryandao on 2011-08-18
I'm using my laptop keyboard. My keyboard just randomly freezes. The only solution I can do now is to switch to another window and switch back~the keyboard is back. It's exactly like the problem this user has with opera [http://ubuntuforums.org/showthread.php?t=979481](http://ubuntuforums.org/showthread.php?t=979481), only with many other programs.

---

### Post by phuongdt3 on 2011-08-18
im having semilar problem,Thank you for the response.

---

### Post by ryandao on 2011-08-21
Anyone knows how to fix this?

---

### Post by asomad on 2011-08-21
I bet if you have a touchpad in the mix, it's even more fun...... typing is hell if I even brush the touchpad all sorts of crap happens...

---

### Post by ryandao on 2011-08-21
I disabled the touchpad but still got the problem...

---

### Post by ryandao on 2011-08-30
I finally found the solution! It's SCIM that makes keyboard lose focus. Simply run this command im-switch -s scim-bridge, it works like a charm!

---

### Post by vectorio on 2012-08-05
Many thanks for this useful post! Is there an updated SCIM in Ubuntu 12.04 (or elsewhere available) that resolves this issue?

---

