---
title: "Grub 2 update-grub2 issues"
date: 2009-10-02
forum: General Help
---

### Post by Trentor on 2009-10-02
I successfully upgraded to the new version of Grub, however I've been having a few issues actually editing the grub menu.

This is a few current excerpts from my current grub file in /etc/default:
```

GRUB_DEFAULT=saved
GRUB_TIMEOUT=5
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_GFXMODE=1680x1050

```

The Default=saved, and gfxmode does not reflect any changes whenever I run 'sudo upgrade-grub2' or 'sudo update-grub'.

I went into my 00_header to manually change the gfx mode to 1680x1050 and it works fine, but what I am wondering is why editing my /etc/default/grub file is not saving changes.

Also, does anyone know how to add themes from this website ([http://grub.gibibit.com/index](http://grub.gibibit.com/index)) without manually editing the /boot/grub/grub.cfg file?  I cannot figure out how to use that text file to enable a theme, tried using it as an entry in /etc/grub.d but it didn't work.

Anyway, just these few questions, thanks for help w/ Grub 2 transition.

Trentor.
:popcorn:

---

### Post by drs305 on 2009-10-20
Trentor,

I stumbled upon this thread when doing a search. Did you figure out the solution?

I tried changing my resolution in /etc/grub/default and it successfully imported it into line 24 of /boot/grub/grub.cfg  

From *the Grub2 command line*, you could run "vbeinfo" to see if that resolution is supported. I don't know if Grub 2 is smart enough to prevent an inappropriate resolution from being entered (although it did just let me add 1200x10  ;-)  ).

As to Theming, I don't think G2 is ready to support Themes without a lot of tweaking. Although eventually a single entry into *grub* Grub2 may load a theme, I don't think it's there yet.

Here is an Arch theme page that seems pretty thorough just for reference.

I have a few links in my signature line that cover other aspects of Grub 2.

---

### Post by philinux on 2009-10-20
> **Trentor said:**
> I successfully upgraded to the new version of Grub, however I've been having a few issues actually editing the grub menu.

This is a few current excerpts from my current grub file in /etc/default:
```

GRUB_DEFAULT=saved
GRUB_TIMEOUT=5
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_GFXMODE=1680x1050

```

The Default=saved, and gfxmode does not reflect any changes whenever I run 'sudo upgrade-grub2' or 'sudo update-grub'.

I went into my 00_header to manually change the gfx mode to 1680x1050 and it works fine, but what I am wondering is why editing my /etc/default/grub file is not saving changes.

Also, does anyone know how to add themes from this website ([http://grub.gibibit.com/index](http://grub.gibibit.com/index)) without manually editing the /boot/grub/grub.cfg file?  I cannot figure out how to use that text file to enable a theme, tried using it as an entry in /etc/grub.d but it didn't work.

Anyway, just these few questions, thanks for help w/ Grub 2 transition.

Trentor.
:popcorn:

 Thought this link from Karmic testing forum might help.
[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

---

### Post by lordskid on 2009-11-23
you will have to compile the older version of grub2 version 1.96 with gfxmenu it is available at grub.gibibit.com.

I tried compiling but haven't got any luck. check out my site at [http://karmic-koala.totalh.com]("http://karmic-koala.totalh.com")

the normal grub2 that can be apt-get installed does not have the gfxmenu patch.

Edit: I have got it to work with my acer travelmate 3210.

I am still trying to make it work for my samsung n140 netbook. I posted the steps for how to compile it for anyone who might want it. I believe someone from this forums have made a package for it. so try searching a bit.

---

