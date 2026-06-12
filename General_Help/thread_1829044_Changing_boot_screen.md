---
title: "Changing boot screen"
date: 2011-08-20
forum: General Help
---

### Post by Macrotus on 2011-08-20
Hi all

I have successfully changed the Ubuntu Lucid Lynx splash screen with [this tutorial]("http://www.n00bsonubuntu.net/content/install-ubuntu-10-04-and-10-10-plymouth-splash/"). When the computer boots, the look of the screen is terrible! There's no transparency, it's small image stretched to fit my 1680x1050 and the colors failed.

I tried [this]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml"). I didn't use the 1280x1024 resolution, I put my own 1680x1050 there. Now when it boots, my monitors say "Out of range" until Ubuntu is 100% loaded.

What should I do?

---

### Post by frankbooth on 2011-08-20
> **Macrotus said:**
> I didn't use the 1280x1024 resolution, I put my own 1680x1050 there. Now when it boots, my monitors say "Out of range" until Ubuntu is 100% loaded.

"Out of range" would indicate that the resolution is too high for the monitor to display.

Are you sure your resolution is 1680x1050 during boot? I don't have prior knowledge in editing plymouth, but you might want to check what resolution it uses? [COLOR="Red"]*(if you decide to edit it, make a backup)*[/COLOR]

Launch a terminal, or press *ALT+F2* and type:
```

gksudo gedit /etc/default/grub

```

Look for something like: (this should be the resolution it uses)
```

GRUB_GFXMODE=1024x768

```

You could add this line: [COLOR="Red"]*(again, make a backup before doing this)*[/COLOR]
```

GRUB_GFXMODE=1024x768
**GRUB_GFXPAYLOAD_LINUX=1024x768**

```

Save it and update GRUB by opening a terminal and type:
```

sudo update-grub

```

This *could* fix your resolution problems, but I'm *NOT* sure if it will.

---

