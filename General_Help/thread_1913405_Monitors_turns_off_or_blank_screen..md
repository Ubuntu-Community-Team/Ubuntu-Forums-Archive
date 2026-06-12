---
title: "Monitors turns off or blank screen."
date: 2012-01-22
forum: General Help
---

### Post by ExoriaX on 2012-01-22
Installing Ubuntu 11.10 using wubi.
[http://www.youtube.com/watch?v=-xiHHkOHb8A](http://www.youtube.com/watch?v=-xiHHkOHb8A)

Computer Spec:
AMD Phenom II X4 955
ATI Radeon HD 5770
G.Skill 8GB DDR3
Samsung Spinpoint F3 1TB
2 monitors (Acer 23" 1920x1080 Primary and Dell 20" 1680x1050 Secondary)

First attempt: Ubuntu installed successfully. It pops up restricted drivers available. I activate it then monitors just go off but computer is still running with no hd activity. I forced my computer to shut down and then turn on. I chose Ubuntu in boot option. The monitor just went blank but monitors are still on though with no hd activity.

Second attempt: After reinstalling, during the installing in Ubuntu set up, the monitors turned off again.

Third attempt: The video I linked above is the third attempt. It ended up same as second attempt.

I am pretty much gave up and don't know what's going on. So I decided to post here and see if anyone know how to fix it.

Thanks,
Exor

---

### Post by ExoriaX on 2012-01-22
Nobody has an idea to fix this?

---

### Post by CC Inc on 2012-01-22
Well, I had a problem where in GRUB after I selected ubuntu, the screen turned off, and after waiting awhile it turned back on and Ubuntu started.

---

### Post by ExoriaX on 2012-01-22
> **CC Inc said:**
> Well, I had a problem where in GRUB after I selected ubuntu, the screen turned off, and after waiting awhile it turned back on and Ubuntu started.
When I install it in wubi then it asked me to restart. After restart there will be "error: prefix is not set" something like that. It takes a while then it will start Ubuntu installation. I don't think that's the problem though.

---

### Post by CC Inc on 2012-01-22
So there is nothing flashing in the corners of your screen?

---

### Post by ExoriaX on 2012-01-22
> **CC Inc said:**
> So there is nothing flashing in the corners of your screen?
The first time I install it from wubi and then restart it will take a while and yes it's flashing and said "error: prefix is not set" something like that. After installed then it will be quick.

---

### Post by ExoriaX on 2012-01-22
I am currently uploading a video that I recorded while the problem. I will post here when it's completed.

So you can see it better.

---

### Post by ExoriaX on 2012-01-22
[http://www.youtube.com/watch?v=-xiHHkOHb8A](http://www.youtube.com/watch?v=-xiHHkOHb8A)

Ignore the audio. It was my lil brothers yelling while playing games.

---

### Post by CC Inc on 2012-01-22
Ok, so they turned off during language packs, do just the monitors turn off or the whole computer?

Im no expert by the way.

Edit: so the whole computer is still on, just the monitors turn off. hmm. What happens when you restart the computer? Does the windows boot loader load, and if so, is ubuntu one of the choices?

---

### Post by ExoriaX on 2012-01-22
> **CC Inc said:**
> Ok, so they turned off during language packs, do just the monitors turn off or the whole computer?

Im no expert by the way.
I added some annotations there but seem like you missed them but that's ok. As you can see after monitors turned off, keyboard and mouse and pc still have power so the computer is still on.

---

### Post by CC Inc on 2012-01-22
What happens when you restart the computer? Does the windows boot loader  load, and if so, is ubuntu one of the choices?

---

### Post by ExoriaX on 2012-01-22
> **CC Inc said:**
> What happens when you restart the computer? Does the windows boot loader  load, and if so, is ubuntu one of the choices?
I recently restarted and yes there is "Ubuntu" in boot option. I selected Ubuntu and press enter then it starts the installation all over again not picking up the left over. I decided to let it run and see what happen.

At "installing language packs" it still turned off monitors.

---

### Post by CC Inc on 2012-01-22
Have you tried letting it sit for awhile? Also, what is your graphics card?

---

### Post by ExoriaX on 2012-01-22
> **CC Inc said:**
> Have you tried letting it sit for awhile? Also, what is your graphics card?
Yes I left it run for about 5 minutes. Still nothing, monitors are completely off whole of time as well as no hard drive activity at all.

I have computer spec in my first post. It's ATI Radeon HD 5770.

---

### Post by CC Inc on 2012-01-22
That may be your problem, because I believe Radeon HD 5770 isnt compatible with linux. Try removing the card and installing again, and then if that works you can get drivers [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English").

---

### Post by ExoriaX on 2012-01-23
> **CC Inc said:**
> That may be your problem, because I believe Radeon HD 5770 isnt compatible with linux. Try removing the card and installing again, and then if that works you can get drivers [here]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.43&lang=English").
I don't think the video card was the problem. I was able to have Ubuntu  10.x installed on my computer before. It worked just fine. I had it formatted long time ago so I stopped using Ubuntu because I use computer primarily for gaming. Then after I found out that I could install and uninstall Ubuntu just like an application using Wubi. Sadly, 11.10 didn't go well on my computer.

I mean come on, how is 5770 is the problem? It's only 2-3 years old?

---

### Post by ExoriaX on 2012-01-23
Fourth attempt: I decided to restart and let it run again and it works fine after installation and restricted driver installed.

I don't know why it works now, because I have not done anything. I just simply restart and let it run exactly like last attempts. Right now, OS is being updated.

In fact, I am posting this post while on Ubuntu.

I will not tag this as "SOLVED" because the problem will continue to appear if I try to reinstall again.

---

