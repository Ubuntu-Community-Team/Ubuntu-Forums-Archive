---
title: "Computer Randomly Shuts down"
date: 2009-08-06
forum: General Help
---

### Post by Mike_IronFist on 2009-08-06
Okay, this is a pain.

I often leave my computer to do things, as we all do, and I press the key shortcut to "lock" it. The screensaver comes on (Plasma) and I leave to do whatever I do.

And Ubuntu just randomly turns off my computer. This has happened twice when I left the screensaver on. Ubuntu just shut my computer off at random.

Two times when the screensaver wasn't on, but I was just making some changes to configurations, my computer just shut off without warning. Mind you, the configurations I was changing were'nt earth-shattering system modifications, just graphical stuff. (Compiz settings, Cairo dock)

This only happens in Ubuntu, and I've yet to find a solution.

I've heard that it has to do with some setup or something similar called ACPI.

The shutoffs I thought were related to overheating (which, my computer was a little hot when I was configuring stuff) but this NEVER happens while running Windows and it also happened just minutes after I put the screensaver on.

---

### Post by Mike_IronFist on 2009-08-06
Bump. This is a serious problem.

---

### Post by P4man on 2009-08-06
still sounds like a hardware problem to me. You're running compiz and/or a screensaver which would put considerable load on your videocard which you may not do under windows (do you ever play any 3D games on windows?).

Also you say "shut down". Does it turn the computer off, or restart it ? If its turned off, can you turn it on instantly again?

---

### Post by gldearman on 2009-08-06
Yeah, that is a serious problem.

I wouldn't dismiss overheating yet.  It might be that the Ubuntu screensaver taxes your CPU or video card in a way that the Windows screensaver does not.

When I was having this problem, I installed the Computer Temperature Monitor applet onto my Gnome panel.  The package is computertemp.  With it, you can quickly check your temperature at any time (the applet's icon changes color, and you can mouse over it to get a temperature reading).  Of course, you can't see the icon when your screensaver is on, but it has a logging function, too.

My overheating problem also started with only one application, and I didn't make the connection with heat, since it seemed like such an innocuous application.

---

### Post by Mike_IronFist on 2009-08-06
> **P4man said:**
> still sounds like a hardware problem to me. You're running compiz and/or a screensaver which would put considerable load on your videocard which you may not do under windows (do you ever play any 3D games on windows?).

Also you say "shut down". Does it turn the computer off, or restart it ? If its turned off, can you turn it on instantly again?

I say shut down because I mean SHUT DOWN. It turns off. It doesn't go into suspend, it doesn't restart. It shuts down. Rebooting leads to the good ol' GRUB boot screen etc etc.

As for games, I play LOTS of 3D games on Windows. Half Life 2, Left4Dead, Portal, Spore, and heck, I even got Crysis to run on my computer, even though ti runs a little framey.

So telling me that my gpu and cpu can't handle a pretty Open GL screensaver when I can run games with far more demanding requirements is a little silly. I do keep Compiz and Cairo open as well, but all of it is hardly TAXING on my cpu and gpu, all though the glitchiness of Compiz when combined with the NVIDIA driver is painful.

Before anyone suggests it's the driver (173 from the Ubuntu Repos) know that I observed this exact problem in an ATI user when searching for a solution. Unfortunately, no one could solve their problem either.

My Cairo dock also has a temperature monitor on it that tells me how hot my GPU is getting. My GPU doesn't even start slowing itself down until it reaches 255 degrees celsius, according to NVIDIA settings.

And last but not least, I run Vista/Windows 7 when I am not running Ubuntu. Vista in particular can be greedy towards system resources, but I never once got a random shutdown from Vista no matter how hot my computer got.

I will however, try the temp monitor thing.

Thanks for your help.

---

### Post by P4man on 2009-08-06
> **Mike_IronFist said:**
>  My GPU doesn't even start slowing itself down until it reaches 255 degrees celsius, according to NVIDIA settings.

Euh.. I sure hope its not getting anywhere NEAR 255°C!

anything over ~100°C is reason for concern, if the nvidia applet tells you it doesn't throttle below 255 its probably because it cant throttle at all (255=2^8 if you start counting from 0).

Im not saying this is your problem, but we have no crystal ball and can't know what you don't write. Software problems with videocards usually result in reboots or kernel panics, I've never heard a PC shut down because of it.

Anyway, have a look at your CPU and GPU temperatures so we can exclude that possibility. The nvidia x-server application should give you the GPU temp. Also tell us what hardware you are using. And FWIW, I would also suggest upgrading your driver to 180, which I think is the recommended now.

---

### Post by sydbat on 2009-08-06
In your original post you mention [ACPI]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface"). This is something that should be enabled during installation (I believe) of the OS. It might not be enabled in your Ubuntu install, and I am not sure how to do so ([although this might help]("http://ubuntuforums.org/showpost.php?p=2500000&postcount=4")) or if it would rectify your problem.

---

### Post by connorh123 on 2009-08-06
I had this same problem.
What I did to fix it, was I noticed it was over-heating? Why? Because there was dust clogged in my laptop. I cleaned it out, and it never shutdown since.

---

### Post by Mike_IronFist on 2009-08-06
> **connorh123 said:**
> I had this same problem.
What I did to fix it, was I noticed it was over-heating? Why? Because there was dust clogged in my laptop. I cleaned it out, and it never shutdown since.
That sounds very accurate. I'm gonna clean it out. Thanks for your help!

---

