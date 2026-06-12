---
title: "using diff.gz , orig.tar.gz and .dsc"
date: 2009-09-28
forum: General Help
---

### Post by Darksmac on 2009-09-28
i understand what they are but u have no idea how to combine them 
plz help

---

### Post by Bachstelze on 2009-09-28
You can build a binary DEB package from those files using for example [pbuilder](https://wiki.ubuntu.com/PbuilderHowto).

---

### Post by Darksmac on 2009-09-28
thanks bachstelze for the advice but i have also discoverd how to do this.

just for others searching

tar xfvz <file name>.orig.tar.gz
gunzip <file name>.diff.gz
cd ./<filename>
patch -p1 -i <file name>.diff  <-- i screwed up on this one a few times diff file NOT dsc

---

### Post by Bachstelze on 2009-09-28
That won't let you build a DEB, so it's pretty useless. If you just want to compile the source, get it from the developer's website.

---

### Post by chrisharrington on 2010-07-27
Hate to hijack an old thread, but I am also trying to compile from source downloaded from launchpad where there is a ~orig.tar.gz file, a ~diff.gz file, and a ~.dsc file.

[https://launchpad.net/ubuntu/+source/lxlauncher/0.2.1-2ubuntu2](https://launchpad.net/ubuntu/+source/lxlauncher/0.2.1-2ubuntu2)

> **Bachstelze said:**
> That won't let you build a DEB, so it's pretty useless. If you just want to compile the source, get it from the developer's website.

Doesn't the .diff file mean that there could be something wrong with using the original source from the developer's website and a patch needs to be applied to compile on Ubuntu?

I am encountering such an issue trying to compile lxlauncher on Lucid. I get an infinite loop when running make on the original source from the developer and with the apparently patched (using patch suggested above) source from launchpad. Not relevant to the discussion, but for background, lxlauncher has a theming deficiency such the background color of the launcher is hard coded, so I have to recompile just to change the color, and I'm unable to compile source due to the loop bug. There is a patch file in the lxlauncher-0.2.1/debian/patches directory addressing that very issue it seems by patching configure.in ('01_fix_infinite_loop.dpatch'), but I'm obviously not doing it right, because even hand patching the relevant files (read the diff file and copy and paste) does not solve the infinite loop on make.

Obviously the binaries based on this source work (have installed and run with no problem) so pbuilder looks extremely promising and is probably the way to go but [the how to available here]("https://wiki.ubuntu.com/PbuilderHowto") is not entirely legible, and I am unable to get passed a fail that says dependencies could not be collected.

---

### Post by chrisharrington on 2010-07-28
Everything you could possibly want to know and more is answered in these videos.

[https://wiki.ubuntu.com/MOTU/Videos](https://wiki.ubuntu.com/MOTU/Videos)

These describe in detail how to set up your environment and create .deb files from the orig.tar.gz, diff.gz, and .dsc files in a way easy to understand for the relative beginner.

---

