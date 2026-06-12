---
title: "Running 32-bit applications on 64-bit Ubuntu"
date: 2011-10-06
forum: General Help
---

### Post by hoffmastera on 2011-10-06
All,

I'm a casual Ubuntu user and ran into an interesting problem that I've yet to find a real solution to.

When running a 32-bit app on 64-bit Ubuntu, version 11.04, if the application has dependencies on gtk, I continually get problems with parts of the application. The root of the problem seems to be that gtk is assuming items are in /usr/lib. On my Ubuntu, /usr/lib contains the 64-bit versions of libraries. So essentially, the 32-bit gtk is referencing 64-bit libraries for dependent items (e.g. immodules, gio, etc...). I have not been able to cleanly solve this. I do have ia-libs (sic?) installed.

Any guidance on this issue? Web searching seems to suggest this is a known issue. Possible workarounds were to create a launcher script that would set the GTK_PATH and then launch the application. Is that the best way to handle this?

Thanks,

Andy

BTW, this is my first post, so be gentle :)

---

### Post by Frogs Hair on 2011-10-06
Hello and Welcome

As 64 bit user I have not had any problem finding 64 bit versions of applications   . Could you list the applications please .  I don't know if I could help , but it may help someone to help you .

---

### Post by hoffmastera on 2011-10-10
The issue seems to be with the gnome gtk. The 32-bit gnome is looking for libs in the /usr/lib on the 64-bit install. So there are quite a few issues that arise. You do raise a good point. Why don't other 32-bit apps have this issue. I'll look into that and try to post what I find. Some solutions to this issue proposed included writing a script that would set the GTK_PATH variable and using that script to start the application. I have since switched over to the kubuntu-desktop, and the same applications seem to run fine. It may take me a bit to reinstall the xubuntu-desktop and try it out again but i'll try to get back to this soon.

Thanks for your interest in my problem.

---

