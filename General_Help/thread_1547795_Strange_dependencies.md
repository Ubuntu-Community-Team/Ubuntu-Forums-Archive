---
title: "Strange dependencies"
date: 2010-08-07
forum: General Help
---

### Post by palmito04 on 2010-08-07
Hi all. I have an HP printer supported by hplip. hplip and hplip-data are installed in my system, now I want install the hplip-gui, then:

```
sudo apt-get install hplip-gui
```

but from output I read this:

```
  **gimp gimp-data** hplip-cups libart-2.0-2 libbabl-0.0-0 libcroco3 libgail18      
  **libgegl-0.0-0 libgimp2.0** libpoppler-glib4 librsvg2-2 libsoup2.4-1
  libwebkit-1.0-2 libwebkit-1.0-common libwmf0.2-7 python-cairo python-gtk2
  python-renderpm python-reportlab python-reportlab-accel xsane xsane-common
```

Why for use my hplip-gui I need gimp? Ok, gimp is required by xsane, but in any case it make no sense. From [this page]("http://packages.ubuntu.com/lucid/xsane") Gimp is in *suggests* not in *depends*. I'm doing something wrong?

---

### Post by Bachstelze on 2010-08-07
xsane depends on libgimp, which recommends gimp.  By default, Apt will install all "recommended" packages.

---

### Post by palmito04 on 2010-08-07
Ok, then how I can not install *recommended* packages?

Thanks, regards.

---

### Post by Bachstelze on 2010-08-07
> **palmito04 said:**
> Ok, then how I can not install *recommended* packages?


You have to put something in /etc/apt/preferences.  I don't remember what it is from the top of my head, use your favourite search engine.

---

### Post by palmito04 on 2010-08-07
Ok, thanks for the hint.

You must ad this line to /etc/apt/apt.conf

```
APT::Install-Recommends "false";
```

Regards.

---

