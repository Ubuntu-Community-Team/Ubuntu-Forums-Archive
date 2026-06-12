---
title: "Is the nVidia GeForce 7900GT supported?"
date: 2006-04-18
forum: General Help
---

### Post by th3t1nm4n on 2006-04-18
I just built a new box and decided to get an ATI X1900XTXT and learned the hard way that it wasn't going to work in Ubuntu like my laptop's ATI card does. I am returning it and am going to purchase an nVidia since on my old box my nVidia worked fine with the nvidia legacy drivers from the repositories.

I would like to buy one of [these nVidia GeForce 7900GT's]("http://tinyurl.com/zze6a"), so I searched the forums and didn't find much confirmation on whether or whether not it was supported, so I would like to know if it is or isn't.

I'd be needing it to be supported well as I play a lot of games from Q4 to Battle for Westnoth.

Thanx for any info on the 7900GT's compatability in advance!

---

### Post by Elvish Legion on 2006-04-18
Is there a linux driver for it?

Why not buy a 7800 or something thats a bit cheaper and well supported?

---

### Post by th3t1nm4n on 2006-04-18
Mainly I want this card because of it being an improvement from the 7800, as for the driver: that's what I'm asking for confirmation on, does the nvidia-xgl driver support this chipset?

---

### Post by jlundell on 2006-04-19
According to nVidia's website ([http://www.nvidia.com/object/linux_display_ia32_1.0-8756.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8756.html)), the newest version of their linux driver does support the 7900 chipset.

---

### Post by Jason_25 on 2006-04-19
I hope your not planning on still using ubuntu 4.10.  

Anyway, like someone before said, the nvidia driver will work and the vesa driver will work too.

---

### Post by th3t1nm4n on 2006-04-19
Alright, thanks for the link.

I'll be running DrapperFlight6 x64, what is the difference [here]("http://www.nvidia.com/object/unix.html") between Linux IA64 and Linux AMD64/EM64T?

Thanks for all the help by the way! :D

---

### Post by Jason_25 on 2006-04-19
IA64 are pure 64 bit cpus like Itanium.  You want AMD64 if your using AMD64 ubuntu.

---

### Post by th3t1nm4n on 2006-05-28
I ended up getting an eVga nVidia 7900GT, it worked out of the box, and for 3D support all I had to do was ```
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
```
and then press Ctrl+Alt+Backspace, runs Quake4 like a dream.

---

