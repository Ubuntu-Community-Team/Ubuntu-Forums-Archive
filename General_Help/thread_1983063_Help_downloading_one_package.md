---
title: "Help downloading one package"
date: 2012-05-19
forum: General Help
---

### Post by dckirba on 2012-05-19
Hello all,

I'm trying to install ia32-libs which I need to install Adobe AIR which I need for another program. However, I've come up against a funny problem:

All required dependencies are installed but my package manager is unable to download libproxy1.

After I tried accessing it through packages.ubuntu.com, I finally realized it's because my ISP has put a blanket block on anything that has the word 'proxy' in it.

So I really need somebody's help. I would greatly appreciate it if someone would download this file from the Precise repository for me:

```
libproxy1_0.4.7-0ubuntu4_i386.deb

```
And kindly upload it somewhere I can access it after renaming it to remove the 'proxy' from the name.

Thank you in advance,

David K

---

### Post by diesch on 2012-05-19
[http://www.florian-diesch.de/tmp/dckirba.zip](http://www.florian-diesch.de/tmp/dckirba.zip) contains that file.

---

### Post by forrestcupp on 2012-05-19
If you're using 12.04, Ubuntu doesn't use IA32-libs anymore. They switched over to multiarch. So I'm not sure that it's going to work without messing something up.

---

### Post by dckirba on 2012-05-19
Thank you :)

---

### Post by dckirba on 2012-05-19
> **forrestcupp said:**
> If you're using 12.04, Ubuntu doesn't use IA32-libs anymore. They switched over to multiarch. So I'm not sure that it's going to work without messing something up.

It's needed for Adobe AIR, which I need for another program.

---

### Post by gordintoronto on 2012-05-19
> **forrestcupp said:**
> If you're using 12.04, Ubuntu doesn't use IA32-libs anymore. They switched over to multiarch. So I'm not sure that it's going to work without messing something up.

Interesting. I installed ia32 to get Skype working. It's a huge install, worked just fine. Skype videoconferencing is working, too.

---

### Post by forrestcupp on 2012-05-20
> **gordintoronto said:**
> Interesting. I installed ia32 to get Skype working. It's a huge install, worked just fine. Skype videoconferencing is working, too.

Did you notice if it happened to remove multiarch in the process? In this latest release, they stopped using ia32 in favor of multiarch, and they changed how everything is handled. Hopefully, it won't mess things up for you when you try doing more standard things later. I know that multiarch has a transitional package for ia32 compatibility. Maybe that's what you installed.

Sometimes, it's not a good idea to try to force installing things in a non-standard way if it isn't working out.

---

### Post by gordintoronto on 2012-05-20
If memory serves, ia32 installed around 170 packages and didn't remove anything. Could be wrong.

I've never heard of Multiarch. I just wanted to get Skype videoconferencing running, using this command line:
bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'

Took me a while to find that in Google, and I didn't find anything which looked simpler. (Skype is a 32-bit app running on 64-bit Ubuntu. It wants to talk to a 32-bit webcam driver.)

---

### Post by forrestcupp on 2012-05-20
I don't completely understand it. All I know is that starting with 12.04, they switched to Multiarch in place of ia32-libs as their means of handling 32-bit apps in a 64-bit OS. I don't know enough about how the two mesh, but I know that ia32-libs was meant to be replaced.

Hopefully, it just works out for you and doesn't cause you any future problems.

---

### Post by forrestcupp on 2012-05-21
I checked it out, and the ia32-libs package in the repos is just a transitional package that depends on ia32-libs-multiarch, which are all the i386 packages that have been transitioned from ia32-libs to work with multiarch.

So if you used the ia32-libs from the repos, you didn't do anything wrong, and you'll be ok.

---

### Post by cortman on 2012-05-21
You can probably also get around this using tor, available in the repositories.

---

