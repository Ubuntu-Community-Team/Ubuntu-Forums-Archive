---
title: "Picture Gallery ?"
date: 2010-06-07
forum: General Help
---

### Post by asearle on 2010-06-07
Hi Everyone,

I am currently looking for a simple photo-management program like F-Spot that will work under Linux, Mac and Windows.  The main requirement that I have is that the tool should be able to generate simple HTML photo-galleries which can then be viewed directly or FTPed to the web.

There seems to be an enormous variety of these tools, many with more functionality/automation than I want (e.g. Picasa), so I am hoping that someone out there has a 'pet tool' that they can recommend to me.

Many thanks,
Alan Searle
Cologne, Germany

---

### Post by philinux on 2010-06-07
Well the cross platform bit is the problem but then **gimp** but can do it with a plugin, but it is not simple.

Not sure if this plugin is in ubuntu repo.
[http://www.skylab.org/~plumpy/gg/](http://www.skylab.org/~plumpy/gg/)

Someone else may chime in.

---

### Post by StuartN on 2010-06-07
> **asearle said:**
> I am hoping that someone out there has a 'pet tool' that they can recommend to me

Yes, gThumb is an excellent image browser / EXIF tag viewer / photo cataloguer that works very well alongside Gimp.

It also has a template-driven web gallery creator that will make a gallery from images in a directory, a catalogue or a search.

---

### Post by prshah on 2010-06-07
> **asearle said:**
> The main requirement that I have is that the tool should be able to generate simple HTML photo-galleries which can then be viewed directly or FTPed to the web.

I use a command-line utility called "album" which is available in the repositories. 

To use, go to your pictures directory, and run the command```
album
``` it will generate and index.html file and thumbnails, which will link to the full size pictures.

It's customizable in many ways, so please give it a try.

---

### Post by asearle on 2010-06-07
Hi everyone,

Many thanks for your tips.

Yes, I would like to have it as a plug-in for GIMP but found that that the source files were very old (2002) and somehow it would not appear in the plug-ins.  That was a shame.

I tried Album and that looks good but I need to adjust the settings (or the template) because the images are coming through oversized.

And a found a tool called XnView which is absolutely great under windows:  It has a really simple way of generating HTML galleries and also has Linux and Mac versions (fantastic!) ...

[http://www.xnview.com/en/index.html](http://www.xnview.com/en/index.html)

However, the Linux version is a bit clunky and although it started to generated the gallery it locked up my PC which was rather irritating.  However, I will probably use the windows version (under VirtualBox) and keep an eye on the Linux version to see when it 'comes of age'.

Indeed, this throws up a second question:  This programme locked up my Ubuntu 10.4 system and I had to do a very ugly power-down to get it going again.  As it was I tried all kinds of things but my keyboard and mouse were dead and I simply couldn't kill the rogue programme.

So does anyone have any tips on avoiding this kind of situation?  Maybe a secret key combination which will return control to me?

Many thanks for your help.

Regards,
Alan

---

### Post by prshah on 2010-06-07
> **asearle said:**
> Maybe a secret key combination which will return control to me?

Dunno about returning control, but you can try the [magic sysreq keys]("http://en.wikipedia.org/wiki/Magic_SysRq_key") to (relatively) safely reboot your system in such a situation.

Note that these are understood by the kernel, so it will work in any situation except a kernel lockup / panic (indicated by flashing capslock and scroll lock keys).

As for oversize thumbnails, you can use the "-medium" switch to control sizes of the thumbnails. More details in the man pages, or post back in case of difficulties.

---

### Post by asearle on 2012-03-10
I found that gThumb has a rather good and very easy web-gallery function.

Regards,
Alan Searle

---

