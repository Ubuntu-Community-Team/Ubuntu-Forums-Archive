---
title: "Ipod Touch/Iphone cross compiler"
date: 2010-01-02
forum: General Help
---

### Post by Psycho.mario on 2010-01-02
Hi,
I am just learning to write programs in C++, and i got an iPod Touch for christmas. I have jailbroken my iPod so i can run my own programs on it. If i ever get them compiled. After a few hours of searching i have been unable to come up with a working toolchain for ubuntu which compiles for ipod/iphone. Does anyone know where i can get one/find a howto which will help me to get a toolchain working??

Thanks

---

### Post by Psycho.mario on 2010-01-03
I just found out that someone called 'Nightwatch' created an ARM/Mach-O Toolchain which is supposed to work; however, i cannot find it anywere on the internet. Does anyone know where i can find any toolchain for my ipod?

Thanks

---

### Post by Psycho.mario on 2010-01-03
Bump

---

### Post by manuelb on 2010-01-03
I have a working toolchain running on my laptop (jaunty/32): i don't know if the iPod Touch differs in some way since i setup the cross compiler for iPhone development, but you'll need to build your own toolchain ([http://code.google.com/p/iphone-dev/]("http://code.google.com/p/iphone-dev/")).
The thing is, you'll also need to copy the iPhone/iPodTouch root filesystem in order to have a working cross compiler.
You can follow the instructions [here]("http://code.google.com/p/iphone-dev/wiki/Building"), it worked nicely for me.

---

### Post by Psycho.mario on 2010-01-03
I tried that but it kept on failing, so i gave up. I have found a toolchain for mac, i dont own a mac, but my friend does. when he comes online later, ill use ssh and try that. if it works ill see if i can get some kind of mac virtual machine together.

Thanks

---

