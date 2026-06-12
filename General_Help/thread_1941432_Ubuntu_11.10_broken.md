---
title: "Ubuntu 11.10 broken"
date: 2012-03-15
forum: General Help
---

### Post by Spikeuh on 2012-03-15
Hello

I am an happy new user of ubuntu. But I should say "I was"...
Last time I have seen my gnome 3 desktop it crashes to a black screen. After that I was not able to log into the graphical interface anymore.

Every time I try to boot to Ubuntu (not in recovery mode) the login screen is black with randomly dispatched pixels which look a bit like the color of the ubuntu login screen background.
I can see the cursor of the mouse and I it is possible to move it. Some fields are almost displayed but I cannot do much more.

So now, I cannot use Ubuntu anymore (I can use the command line, but it kind of frustrating).

I am running Ubuntu 11.10 64bit on an Intel I5 with Nvidia Gforce. Ubuntu was up to date. The crash happens while surfing. I remember have click on video or link to video and then everything became black... The rest is above.

Someone can help me?
Thanks for advance.

---

### Post by Spikeuh on 2012-03-16
Nobody has an idea?
Maybe it is something really stupid like a file to restore or a configuration file to modify...
I don't know why that happens. It seems that my linux is real slow in graphical interface and totally buggy. Especially
Is there a way to check the integrity of the X and the desktops manager in command line?
It has been 4 days know, I really need a fix ;)
I just need a direction, because I do not understand yet de philosophy of the linux system.
Thanks for advance for any answer!
(kind of "up")

---

### Post by raja.genupula on 2012-03-16
Boot to Grub Recovery Mode -> FailsafeX mode and then reinstall your graphics drivers .

---

### Post by MARP1961 on 2012-03-16
A completely fresh install and configuration of Ubuntu should take well under an hour. If you have a separate /Home partition then you can keep all your old files and settings too.

---

### Post by YannBuntu on 2012-03-16
> **MARP1961 said:**
> A completely fresh install and configuration of Ubuntu should take well under an hour. If you have a separate /Home partition then you can keep all your old files and settings too.

For information: since Hardy, you can reinstall Ubuntu keeping /home even if it is not separated. Until Natty you had to do it via the manual partitioning menu, but since Oneiric you just need to select the "Upgrade 11.10 to 11.10" option of Ubuntu installer.

[[img]http://pix.toile-libre.org/upload/img/1331904390.png[/img]](http://pix.toile-libre.org/?img=1331904390.png)

---

### Post by muteXe on 2012-03-16
The amount of people on here who suggest a fresh install for any problem is annoying.

---

### Post by MARP1961 on 2012-03-16
OK, so people with more advanced knowledge of Ubuntu/Linux can fix many problems and probably enjoy the challenge. I understand them thinking that a fresh install is the last refuge of a coward; but if** beginners** ask for help, they might be wanting an easy and quick fix.

Complicated instructions and the frustration that results could drive them away from Linux. In time they will learn more and more. They will be more adventurous. I just remind people that fresh installs are an option, that's all. If someone can help more competently than me then that's great and everyone's happy. Let's all have our say, contribute what we can and let those asking for help decide what advice to follow. 

I want more people to benefit from Linux. This will only come by demystifying it. Let's not blind beginners with 'Bash Overdose' before they are ready.

Many thanks to YannBuntu for reminding us (me) about the 'Upgrade Ubuntu to Ubuntu' option. I must give this a try one day!

---

### Post by Spikeuh on 2012-03-16
First thanks for all your answers!

I am kind of a newbie in linux (even if it is not my first distro) but I am not only looking for simple method. I hope to learn a bit more about the system while solving this problem.

I am interested by the fix proposed by raja. (I am working in IT and interested in understanding how things works. But linux is still a new challenge to take)

Thanks for the tip about reinstalling the system without losing the home even if not separeted (which is my case). I already reinstall all the system due to bugs linked to the configuration of the Gnome 3 desktop. I wish I have knew that before.

I am also thinking it can only be a matter of graphical problem. So I will try reinstalling the drivers (If I can find how to to it).

But anyway all propositions are interesting!
So now I have to reboot to check if I can do it... Hope it will works!

---

### Post by Spikeuh on 2012-06-24
Hello,

One more time thank you for all the answers.

I finally discover that my graphical card was broken: no more 3D acceleration, it switch to a basic vga card. And this was the real problem. As I still get an image I was was not thinking about that.

So, problem solved!

---

