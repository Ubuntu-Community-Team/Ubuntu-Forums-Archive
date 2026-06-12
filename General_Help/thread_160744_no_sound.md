---
title: "no sound"
date: 2006-04-15
forum: General Help
---

### Post by IsKall on 2006-04-15
Hi guys! 
I recently installed Ubuntu on my laptop Acer 1642, and everything works fine except my soundcard, it is an Realtek, ALC260 (somthing like that)
Yes, I have checked the sound options and volume etc.

Anyone have any idea how I can make the sound work?

---

### Post by xXx 0wn3d xXx on 2006-04-15
in terminal type:
> 
sudo alsamixer

Make sure that nothing is muted.

---

### Post by IsKall on 2006-04-15
MasterChief1234, thats what I have been trying but still no sound comes. Everything is unmuted.

Does it have anything with the sounddriver?

---

### Post by xXx 0wn3d xXx on 2006-04-15
[QUOTE=IsKall]MasterChief1234, thats what I have been trying but still no sound comes. Everything is unmuted.

Does it have anything with the sounddriver?[/QUOTE]
I had no sound when I first installed breezy and nothing was muted. I now have sound because I compilied the newest kernel from kernel.org and wrote a tutorial on it. If you are new to ubuntu I don't recommend it and the new kernel might now have the drivers for your sound card. I think you could compile the kernel if you know the following commands: sudo, cd, cp and a few others. The link to my tutorial is in my signature. Only attempt it if you feel that you are expericenced enough. I am avaible for support if you require it or you can post in the 2.6.16 kernel thread.

---

### Post by IsKall on 2006-04-15
MasterChief1234, is it possible to get Ubuntu on ISO file with the latest kernel?

---

### Post by xXx 0wn3d xXx on 2006-04-15
[QUOTE=IsKall]MasterChief1234, is it possible to get Ubuntu on ISO file with the latest kernel?[/QUOTE]
You could do a clean install for dapper. It contains a newer kernel + when you update it is almost the newest one. Note what I said above, the new kernel might not even support your sound card. But I have a feeling that it will.

---

### Post by IsKall on 2006-04-15
will try it then :D thank you

---

### Post by Sef on 2006-04-15
You could do the following and post your results:

sudo gedit /etc/modprobe.d/alsa-base

if it uses alsa....if not, then substitute what you have.

I did that and made a couple of small changes and got sound.

---

### Post by IsKall on 2006-04-16
Thank you all! Espacially MasterChief1234!

I recently installed Dapper 6.06 on my Acer 1642 and now my souncard works!!!!! Everything works perfectly :D :D :D

Thank you guys!

---

### Post by xXx 0wn3d xXx on 2006-04-16
[QUOTE=IsKall]Thank you all! Espacially MasterChief1234!

I recently installed Dapper 6.06 on my Acer 1642 and now my souncard works!!!!! Everything works perfectly :D :D :D

Thank you guys![/QUOTE]
Awesome ! I'm glad it works. :)

---

### Post by IsKall on 2006-04-16
Yeah me too! :D 
Really want to learn linux :)

---

