---
title: "Trying to get linux headers.. need some help (I'm a noob)"
date: 2006-06-01
forum: General Help
---

### Post by jkbowle on 2006-06-01
I'm trying to apt-get the linux-headers for my kernel version using the following line:
sudo apt-get install linux-headers`uname -r`

but I keep getting the following error:
E: Couldn't find package linux-headers2.6.15-23-386


I know it's probably a repository thing.. but I'm not sure what repository to add.. anyone know?  Should I just download the .deb package?

Thanks

---

### Post by joshrobinson on 2006-06-01
use synaptic and search for headers.. its easier :-D i think theres another - after headers

---

### Post by rcarring on 2006-06-01
If you run synaptic, then add every repo listed in the repos dialog, reload, you can then search the All list and look for the linux-headers you need.

That's how I got mine installed.

Edit -- beaten to it =D

---

### Post by jkbowle on 2006-06-01
Cool thanks, just realized that I left out a "-" before `uname -r`.

BTW.. all that stuff dealing with synaptic.. went way over my head

---

### Post by joshrobinson on 2006-06-01
[QUOTE=rcarring]If you run synaptic, then add every repo listed in the repos dialog, reload, you can then search the All list and look for the linux-headers you need.

That's how I got mine installed.

Edit -- beaten to it =D[/QUOTE]

:eek:

---

### Post by joshrobinson on 2006-06-01
[QUOTE=jkbowle]Cool thanks, just realized that I left out a "-" before `uname -r`.

BTW.. all that stuff dealing with synaptic.. went way over my head[/QUOTE]

at least you got it working.. i was pretty sure there was a - in there.. you need them to compile a program im guessing?

---

### Post by jkbowle on 2006-06-01
[QUOTE=joshrobinson]at least you got it working.. i was pretty sure there was a - in there.. you need them to compile a program im guessing?[/QUOTE]
Yeah.. will be installing Cisco VPN eventually.. but right now.. I'm trying to install the latest NVIDIA drivers.. and that thread is just too long to read in one sitting.. I"m too impatient for that.

---

### Post by jkbowle on 2006-06-01
Just found the repositories section in synaptic.. SWEET..

Now I understand.  Thanks everyone for helping me out.

---

### Post by RAOF on 2006-06-01
[QUOTE=jkbowle]I'm trying to apt-get the linux-headers for my kernel version using the following line:
sudo apt-get install linux-headers`uname -r`
[/QUOTE]
A better version is **sudo aptitude install linux-headers** (or possibly -headers-386, I'm not sure).  That way, if you ever get a kernel update, your headers will match the new kernel.  Less important now Dapper's gone stable, but still.  Better safe than sorry.

---

