---
title: "How to apply Gconf patch for UFraw?"
date: 2009-09-02
forum: General Help
---

### Post by seanlano on 2009-09-02
As part of my photograph processing, I use the "Develop in UFraw" extension of F-spot to process raw images. However, I would like to be able to save these images as .png's, not .jpeg's, but the extension won't seem to let me. I found something in bugzilla about a patch that would fix this problem (see: [http://bugzilla.gnome.org/show_bug.cgi?id=555820]("http://bugzilla.gnome.org/show_bug.cgi?id=555820")) but I have no idea what to do with this. It says something about changing Gconf to allow you to save as a .png. 

What do I do with the patch file? Please help!

---

### Post by paradigm2 on 2009-09-02
Generally go to the directory which is the parent directory which contains:

f-spot-0.5.0.2-orig/extensions/Tools/DevelopInUFraw/DevelopInUFRaw.cs

(the one right above "f-spot-0.5.0.2-orig")

Then execute:

```

sudo patch -p0 < NAME OF PATCH FILE HERE

```

Assuming it suceeds you probably need to do a

```

cd f-spot-0.5.0.2-orig
sudo make
sudo make install

```

Something like this anyway. Consider this just a hint. Patching source code is usually considered to be fairly advanced.

You will need to have downloaded the source code somewhere to do this.  You will be patching the source, configuring it, and then compiling and finally installing it.  You will need the build-essentials package installed.

---

