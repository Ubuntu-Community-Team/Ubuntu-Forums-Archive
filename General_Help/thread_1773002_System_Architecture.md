---
title: "System Architecture?"
date: 2011-06-01
forum: General Help
---

### Post by etienne@Rofti on 2011-06-01
Hi there!

I was wondering about what the system architecture of Ubuntu would look like. I have attempted to create my own idea of what goes where. I'm not a programmer, so these are my best guesses from what I can understand from Wikipedia.

If anyone has any suggestions about what it should rather be like, please post them. This is more for interest's sake than anything else, but I have been wondering for a while.

See the attached file for my mock-up/idea.

Thanks!

---

### Post by doas777 on 2011-06-01
overall looks reasonable. I would put a box around the kernel/systemlibs/drivers to show that they are all part of the same whole.

---

### Post by etienne@Rofti on 2011-06-01
Thanks for the quick reply doas777!

I have updated the diagram. Does anyone think that this is now more accurate?

See attachment...

---

### Post by doas777 on 2011-06-01
ok, making progress. not sure what tools you are using to mark it up.

The only suggestion i have, is that you show the stack as taller in the middle. for instance Gnome rides atop X, and Compiz atop Gnome.

is this just for personal understanding, or do you need to present the chart?

---

### Post by etienne@Rofti on 2011-06-01
> **doas777 said:**
> ok, making progress. not sure what tools you are using to mark it up.

The only suggestion i have, is that you show the stack as taller in the middle. for instance Gnome rides atop X, and Compiz atop Gnome.

is this just for personal understanding, or do you need to present the chart?
Dear doas777

Thank you for the friendly reply! I am simply drawing the shapes in LibreOffice, mostly for my own understanding. I have been an Ubuntu/Linux user for about 3 years now, moving from XP, and I have no idea still how the system actually works.

I saw an Apple diagram while searching for information on this topic, and they drew a nice beautiful picture showing Darwin and Quartz and everything. I can't remember where I saw that picture though. That's why I thought of a diagram for Ubuntu, but I couldn't find a good one.

---

### Post by etienne@Rofti on 2011-06-01
I have drawn a new system architecture mock-up. Please let me know if it is accurate or not. Thanks!

See attachment:

---

### Post by idoitprone on 2011-06-01
The linux kernel is monolithic kernel which means the system call through the whole stack. [http://en.wikipedia.org/wiki/Monolithic_kernel](http://en.wikipedia.org/wiki/Monolithic_kernel) 
There is a very good diagram on the linux kernel there.

The xserver is a beast of an implementation. It is complex and it should die. The problem it is a very old protocol and when it a came out it was just a hack. To get modern rendering capibilities, they bypass its own api and use its plugin model. Compiz is essentially a plugin to the xserver. gnome and kde sits on top of gui toolkits such as gtk/qt
[http://wayland.freedesktop.org/architecture.html](http://wayland.freedesktop.org/architecture.html)

[http://wayland.freedesktop.org/](http://wayland.freedesktop.org/)

some papers of plan9, an operating made by the same people who used unix
[http://plan9.bell-labs.com/wiki/plan9/papers/](http://plan9.bell-labs.com/wiki/plan9/papers/)
There are some papers on operating system design.

Pulseaudio and alsa cannot coexist with each other. Pulseaudio supports alsa as a plugin
[http://en.wikipedia.org/wiki/File:Pulseaudio-diagram.svg](http://en.wikipedia.org/wiki/File:Pulseaudio-diagram.svg)


an example diagram, so you can get ideas
[http://www.google.com/imgres?imgurl=http://www.promwad.com/images/stories/technologies/mobile_platforms/moblin-architecture-diagram.jpg&imgrefurl=http://www.promwad.com/technologies/mobile-platforms.html&usg=__MpawnohmEmg8gO5TqZ131YjG8s0=&h=484&w=800&sz=82&hl=en&start=146&zoom=1&um=1&itbs=1&tbnid=XhAERoAQAaLa5M:&tbnh=87&tbnw=143&prev=/search%3Fq%3Ddiagram%2Bof%2Blinux%2Bapi%26start%3D140%26um%3D1%26hl%3Den%26sa%3DN%26ndsp%3D20%26tbm%3Disch&ei=i-vmTY-MHYGmsQP205SIDg](http://www.google.com/imgres?imgurl=http://www.promwad.com/images/stories/technologies/mobile_platforms/moblin-architecture-diagram.jpg&imgrefurl=http://www.promwad.com/technologies/mobile-platforms.html&usg=__MpawnohmEmg8gO5TqZ131YjG8s0=&h=484&w=800&sz=82&hl=en&start=146&zoom=1&um=1&itbs=1&tbnid=XhAERoAQAaLa5M:&tbnh=87&tbnw=143&prev=/search%3Fq%3Ddiagram%2Bof%2Blinux%2Bapi%26start%3D140%26um%3D1%26hl%3Den%26sa%3DN%26ndsp%3D20%26tbm%3Disch&ei=i-vmTY-MHYGmsQP205SIDg)

[http://translate.google.com.hk/translate?hl=zh-CN&ie=UTF8&sl=zh-CN&tl=en&u=http://www.microsoft.com/china/windowsserver2003/sfu/default.mspx](http://translate.google.com.hk/translate?hl=zh-CN&ie=UTF8&sl=zh-CN&tl=en&u=http://www.microsoft.com/china/windowsserver2003/sfu/default.mspx)
here is a good diagram of a possible unified kernel. It show the complexity of both windows and linux
the forum which i found the link
[http://www.reactos.org/forum/viewtopic.php?f=2&t=7720&hilit=linux+kernel&start=30](http://www.reactos.org/forum/viewtopic.php?f=2&t=7720&hilit=linux+kernel&start=30)

---

