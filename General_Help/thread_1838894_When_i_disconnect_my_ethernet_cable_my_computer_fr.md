---
title: "When i disconnect my ethernet cable my computer freezes up"
date: 2011-09-04
forum: General Help
---

### Post by ffmurray on 2011-09-04
so i just did a clean install of ubuntu 11.04 on my ace 5250 laptop.  i had problems with it freezing up at the password screen at login after my first restart.  i connected my ethernet (connecting to my other laptop runnin U10.10 and sending its internet through ethernet) and and ran repair packages from recovery mode.  this seemed to work and i was able to start using the laptop again.  i disconnected the ethernet network because i was tethering from my phone and the computer was fine, but about an hour later i removed the cable and the computer froze completely and i restarted it and i again couldnt get past the password screen without a complete freeze requiring a restart.  it happened four or five times, in classic and safe mode too.  i finally connected my ethernet cable and it was able to login right away with no problem.  i can disconnect from the network but if i remove the cable then it freezes up within 10 seconds.

i am completely stumped.

---

### Post by LMP900 on 2011-09-04
A person is having a similar issue, although the problem occurs when the ethernet cable is *connected*. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/742376](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/742376) I was also able to dig this up in the forums: [http://ubuntuforums.org/showpost.php?p=10863837&postcount=9](http://ubuntuforums.org/showpost.php?p=10863837&postcount=9)

Perhaps that can get you started while someone with more expertise than myself sees this thread.

---

### Post by ffmurray on 2011-09-05
thanks, i looked through it but i could not figure out whats causing this. i cant see how having the cable connected is holding my system together even when its not connected to a network or anything.

---

### Post by ffmurray on 2011-09-05
so the same thing is happening with a couple of acer laptps and ubuntu 11.04 and fedora 15

---

### Post by saintjedisaiyan on 2011-10-13
I already have the same problem with my lenovo G475 with ubuntu 10.04LTS. I'm really trying to fix this problem is so annoying.

---

### Post by dcstar on 2011-10-15
> **saintjedisaiyan said:**
> I already have the same problem with my lenovo G475 with ubuntu 10.04LTS. I'm really trying to fix this problem is so annoying.

Try setting a Static IP address in the Network Manager and then see if it "freezes".

---

### Post by Dogmeat on 2012-03-25
I had the same problem in my 5250. Setting the network card with a static IP caused it to stop freezing, thank you.

---

