---
title: "AMD Drivers + Gnome Shell (Fallback) problems"
date: 2011-10-16
forum: General Help
---

### Post by jmtast on 2011-10-16
Hello guys! How are things?

I am creating this thread because I'm having some problems with my Sony Vaio VPCYB15AL with AMD E-350 graphics and its drivers.

The thing is, I have installed 11.10 so I could easily install Gnome Shell. First I had problems as I was using old propietary drivers, so I installed the open-source ones, as I have read that the propietary ones didn't have support for Gnome Shell.

Everything worked well except for one issue I have when waking up from sleep with that drivers, and the issue is that it "looks like" when you have a wrong refresh rate set up. Eventually it "fixes itself" over time (with 30/60 minutes of use without going under sleep) but it's really annoying (will make a video if needed).

On the other hand, I read that the 11.9 propietary drivers had Shell support, so I decided to give them a try, and here's where my problems begun.

I couldn't install them with the software center because it says "'Error: BrokenCount>0' This usually means that your installed packages have unmet dependencies"

"Another error I encounter is:
Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

Tried to put the content of that file in a spoiler but couldn't. If needed, ask for some specifics or I can upload the file itself.

I also got a "broken packages" message. I don't know where to start to fix things. Is there a way to "restore to previous system state" or some kind of "system rewind"?

I also tried installing them manually with a couple of guides but without any luck (ie. [this one]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:__Need_to_fully_remove_-fglrx_and_reinstall_-ati_from_scratch")).

After all that, I gave up so decided to uninstall everything, go back to the open-source drivers and move on, but I can't seem to get that right, as Gnome goes into fallback mode and the Unity 3D support test (/usr/lib/nux/unity_support_test -p) says it doesn't suppport it anymore:


OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  1.4 (2.1 Mesa 7.11)

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  no
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

And it said "yes" in every aspect before.

I don't know what else to do. I prefer to deal with the "refresh rate issue" before having this driver mess performing less than they should, so any help is appreciated (if I can't solve this I'll just have to reinstall the OS I guess :()

Thanks for reading.

Best regards.

---

### Post by jmtast on 2011-10-16
Guys let me bump this a bit to see if I can find any help. Thanks again for your time!

---

### Post by jmtast on 2011-10-16
I only wish to erase all the garbage left by both the open source and the propietary drivers and reinstall one of them from scratch, but I seem to be having problems with that too :(

---

### Post by Amgad elsaiegh on 2011-10-17
i have the same problem too ](*,)

---

