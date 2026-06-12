---
title: "Using Ubuntu (Gnome) programs in Xubuntu (XFCE)"
date: 2012-07-08
forum: General Help
---

### Post by AnotherMuggle on 2012-07-08
Evening All,

I am very interested in Xubuntu and I've been testing the Live environment on my netbook with great success.

The only question I have is regarding installation of Ubuntu (Gnome) programs in Xubuntu (XFCE).  I am familiar with and use regularly programs such as Meld, LibreOffice and Eclipse.

What exactly is the deal with using these programs in Xubuntu?  I notice that installing them pulls in a lot more libraries, many of them referencing Gnome, than they do in Ubuntu.  Is this OK, normal, messy?  It seems messy but I don't know.

Any input welcome.

Cheers.

---

### Post by AlbertJB on 2012-07-08
It depends on the applications implementation language... Some apps are implemented in c++ (qt libraries required), others in GTKmm (GTK2/GTK3 libraries required).. This fact may be the reason sometimes a gnome app installation on xubuntu 12.04 requires more extra libraries. Apart from that, it's the same distro with just a different DE... In fact Xubuntu is Xfce + lots of Gnome stuff.

---

