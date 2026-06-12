---
title: "New to Linux -- A couple of Basic Problems"
date: 2010-07-16
forum: General Help
---

### Post by liakosR+ on 2010-07-16
Hello! I am pretty much new to Ubuntu but I'm willing to test it out because I think it's worth my effort. Still, I'm facing a couple of problems. I'm having trouble with three issues here:

1. I have downloaded Google Earth and I don't know what application to use to install it. When I was using Windows, when trying to install a program I was usually looking for the .exe file. is there a similar file here in Ubuntu to install and run applications?

2. Maybe it isn't a "Basic" problem but, still, it is a problem. I have searched the Ubuntu Software Center and found Skype but I could not install it because "This program is available from the lucid-partner source, which I am not currently using". What does this mean, how can I get to use this "lucid-partner source" and install Skype?

3. This may seem a ridiculous problem but it's really annoying and I can't seem to find a way to solve it. At first, I was able to see the title bars of my windows but now somehow I just CAN'T! :???: I don't know why. And it's really annoying and inconvenient because I can't close, minimize or move my windows quickly. Is there any way to bring my title bars back to life?? :p

That was all my questions for now. I would really appreciate it if someone could answer them. It would be really helpful to me. Thank you very much!

---

### Post by deathadder on 2010-07-16
Hi,

1) There's a wiki page about installing [Google Earth]("https://help.ubuntu.com/community/GoogleEart") that should help.

2) The same applies for [Skype]("https://help.ubuntu.com/community/Skype") the wiki page should provide all of the information you require.

3) I've never run into this myself, but there's a couple of threads in the forum that should help you.

[http://ubuntuforums.org/showthread.php?t=363314](http://ubuntuforums.org/showthread.php?t=363314)
[http://ubuntuforums.org/showthread.php?t=580262](http://ubuntuforums.org/showthread.php?t=580262)
[http://ubuntuforums.org/showthread.php?t=251935](http://ubuntuforums.org/showthread.php?t=251935)

[http://www.google.co.uk/search?hl=en&q=+site:ubuntuforums.org+gnome+title+bar+missing&sa=X&ei=cmxATJyPI5L80wSbxs2ZDw&ved=0CBwQrQIwAA](http://www.google.co.uk/search?hl=en&q=+site:ubuntuforums.org+gnome+title+bar+missing&sa=X&ei=cmxATJyPI5L80wSbxs2ZDw&ved=0CBwQrQIwAA)

---

### Post by kukker32 on 2010-07-16
answer on question 1..
yes there are .deb (proberly for debian not ubuntu) but works fine. :)
else we ubuntu users uses terminal to install programs with

answer question 2
download and install skype using this .deb [http://www.skype.com/go/getskype-linux-beta-ubuntu-32](http://www.skype.com/go/getskype-linux-beta-ubuntu-32)

3..
i will try find out

---

### Post by kukker32 on 2010-07-16
hmm to late :( for me

---

### Post by graphixfx on 2010-07-16
.deb files are the easiest files to install into Ubuntu comparable to an .exe

you could try to install google earth through ubuntu software center as well 

if that doesn't work you could try to install through synaptic package manager system> administration> synaptic package manager

logging out then logging in usually brings back window bars

---

### Post by porchrat on 2010-07-16
> **liakosR+ said:**
> Hello! I am pretty much new to Ubuntu but I'm willing to test it out because I think it's worth my effort. Still, I'm facing a couple of problems. I'm having trouble with three issues here:

1. I have downloaded Google Earth and I don't know what application to use to install it. When I was using Windows, when trying to install a program I was usually looking for the .exe file. is there a similar file here in Ubuntu to install and run applications?
Depends on what you have downloaded. If it is a .bin or something and you run it with the "sh" command. Like this:
```
sh filepath/filename
```

You may need to use sudo too.


> 2. Maybe it isn't a "Basic" problem but, still, it is a problem. I have searched the Ubuntu Software Center and found Skype but I could not install it because "This program is available from the lucid-partner source, which I am not currently using". What does this mean, how can I get to use this "lucid-partner source" and install Skype?
You need to activate the repository that the skype files are sitting in. By default they are deactivated.

here is a guide on how to add the repository:
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding%20Canonical%20Partner%20Repositories)

After that just install it through the software center or Synaptic like normal.


> 3. This may seem a ridiculous problem but it's really annoying and I can't seem to find a way to solve it. At first, I was able to see the title bars of my windows but now somehow I just CAN'T! :???: I don't know why. And it's really annoying and inconvenient because I can't close, minimize or move my windows quickly. Is there any way to bring my title bars back to life?? :p
Sounds like a window manager issue I used to get under 8.04. If you change your window manager out and then change it back again it normally fixes the problem. I remember this was easy in 8.04 with compiz (there was a taskbar icon) but I don't know how to handle it in 10.04 without compiz.

If it is just the firefox window then often a quick switch between fullscreen mode and back again does the trick (the hotkey is F11).

---

### Post by liakosR+ on 2010-07-16
> **porchrat said:**
> Depends on what you have downloaded. If it is a .bin or something and you run it with the "sh" command. Like this:
```
sh filepath/filename
```You may need to use sudo too.


Do you mean like this?

sh computer/myusername/downloads/GoogleEarthLinux.bin

( I wrote that in the terminal)

---

### Post by Vaphell on 2010-07-16
almost
sh /home/username/downloads/GoogleEarthLinux.bin
sh or in short ~/downloads/GoogleEarthLinux.bin (~ = home dir of current user)

---

### Post by WorMzy on 2010-07-16
No. For run files (assuming it's for installing something) you should first make it executable by right clicking on the file, choosing Properties, witching to the permissions tab, and checking the box next to "Allow running as a program"
[IMG]http://www.ubuntu-pics.de/bild/106026/vimlaunch_properties_001_o2TZ06.png[/IMG]

Then open a terminal from Applications -> Accessories -> Terminal, and drag the file into the terminal window, then click inside the terminal window and press enter.

As for your window decoration, press Alt+F2, and run 'metacity --replace'.

---

### Post by liakosR+ on 2010-07-16
It worked!!

One last question: Is this the technique to install all .bin files?

---

### Post by liakosR+ on 2010-07-16
All my problems are solved!! :mrgreen: Thank you VERY much people! You've all been a great help!

---

### Post by WorMzy on 2010-07-16
Not all .bin files are actually installers, some are images of disks, like an .iso, and need to be burnt to a CD. But as long as it's an installer, that process should work.

---

### Post by dino99 on 2010-07-16
i wonder why newbies often (always) choose the hard way to install apps  :lolflag:

those apps are into repo: canonical partner and ubuntu-restricted-extras (activate and install with synaptic)

---

### Post by digitalcitizenx on 2010-07-16
Many and sometimes most of the time the software will come packed in a folder. I know Google Earth does not - but back to the point - in this folder will be a read me file and probably an install file - read both of these for tips on installing the software.

Personally I would refrain from installing too many .deb files. They will not update automatically and can be an issue during an upgrade.

Merely looking for the software you want to use in Ubuntu repositories will save you LOTS of time and headaches.

If you need software - ask in Ubuntu Forums first. Let us guide you. 

IMHO the best way to install software is to install it via ppa - this way you get automatic updates when available and if you have issues it is easy to uninstall. 

Good luck and always remember....

---

### Post by viralmeme on 2010-07-16
> **liakosR+ said:**
> 1. I have downloaded Google Earth and I don't know what application to use to install it

Fire up Synaptic Package Manager and install it from there .. same with Skype ...

[Synaptic]("http://www.nongnu.org/synaptic/action.html")

---

### Post by oldsoundguy on 2010-07-16
Actually, IF you install Ubuntu Tweak (3rd party program) and set it up properly (follow the directions), you will  install all of the regular repositories including the restricted and partners,  Then programs such as Google Earth and Skype will be in both Synaptic and in the Software Center.
(and the clean up program is more than cool to remove orphan stuff left behind after updates /installs!)

Google Earth SAYS that you have to have the latest (meaning restricted) drivers installed for your card .. but it will work off of the generic drivers for most cards (NVida-current will install for some, but there is no EASY way to activate the driver right now on many older cards.)

Skype is a piece of 3rd party crap .. does not work for way too many .. either video problems or audio problems or BOTH!  (It won't even turn my Logitech 9000 ON!!) .. so wish you luck on that one!

---

### Post by liakosR+ on 2010-07-16
> **digitalcitizenx said:**
> 

IMHO the best way to install software is to install it via ppa.




What's a "ppa"??

---

### Post by Vaphell on 2010-07-16
ppa is a private repository managed by the 3rd parties, out of scope of official ubuntu one. you can add them to repo list and synaptic sees them. That means you can install stuff via synaptic as usual, people often use them to install newer versions of programs than these available in official repos (ubuntu freezes versions before release to increase stability and help with testing)

easiest way to find out - google 'ppa <software name>', most popular apps have one

---

### Post by oldos2er on 2010-07-16
> **dino99 said:**
> i wonder why newbies often (always) choose the hard way to install apps  

Because Medibuntu and partner repositories aren't enabled by default, and most times new folks are unaware of the concept of repositories. (I know your question was "lol", but I'm treating it seriously, FWIW).

---

