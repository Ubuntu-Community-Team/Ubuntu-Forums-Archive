---
title: "Debian building e17 bash: ./configure: No such file or directory"
date: 2010-03-10
forum: General Help
---

### Post by wsonar on 2010-03-10
I just installed a fresh debian install and am trying to follow the instructinos to build e17

[http://debe17.com/cvs_page/cvs_install_page.html]("http://debe17.com/cvs_page/cvs_install_page.html")

after I cd to the directory and run ./configure I get the no such file or directory

build essential in installed, I've read the readme which says to simply run ./configure

there is a configure.ac file in the directory

any suggestions i hate following directions that don't work

I've compiled lots of other stuff with out this problem before

---

### Post by wsonar on 2010-03-10
I tested ./configure out on another source and it works

how do I build e17?

---

### Post by wsonar on 2010-03-10
looks like I have to build pkg-config first

---

### Post by wsonar on 2010-03-10
do I have to manually add a line to each configure.ac file to use the pkg-config?

---

### Post by wsonar on 2010-03-10
I tried adding this line to the configure.ac file and still didn't work

    PKG_CHECK_MODULES([GNOME], [gtk > 1.2.8 gnomeui >= 1.2.0])


What do I ndo to build e17 these instructions didn't mention any of this

---

### Post by wsonar on 2010-03-11
Has anybody build e17 from source?

---

### Post by VCoolio on 2010-03-11
When compiling from svn most of the time you'll need to run './autogen.sh' in order to create a configure file, but it will be run automatically. So first ./autogen.sh, then 'make', then 'make install'; you may want to specify /opt as prefix, so everything gets installed there: ./autogen --prefix=/opt

Also there is a easy_e17.sh script that helps, but since the e17 svn tree has changed a lot lately it may throw errors. You could use [this]("http://svn.enlightenment.org/") for a start.

And yes, people do build e from svn (I'm using it for two years now), but you need to be a bit fanatic about it :P. There is some support at irc.freenode.net #e.

---

### Post by gmargo on 2010-03-11
Did you try the procedure outlined in the wiki? [http://trac.enlightenment.org/e/wiki/Installation](http://trac.enlightenment.org/e/wiki/Installation)

---

### Post by wsonar on 2010-03-11
I've been trying to e17_easy.sh but get

```
Package freetype2 was not found in the pkg-config search path.

```

I did a 

```
whereis freetype2 
```

and got this

```
freetype2: /usr/include/freetype2
```


i tried to include it in the path but still no luck

I've tried the OzOS cd but figured I'd give it a try from scratch

---

### Post by wsonar on 2010-03-11
It's been years any rumor's on a real stable version

---

### Post by VCoolio on 2010-03-11
When compiling you need -dev packages; try for example to install libfreetype6-dev and see if that solves it.

And yes a release is coming close. They're cleaning up the svn tree, only the core will be released as far as I've understood. Don't ask for a release date in #e though or you'll be shot.

---

### Post by gmargo on 2010-03-11
> **wsonar said:**
> I've been trying to e17_easy.sh 
I'm currently compiling the basic packages using the easy_e17.sh script.  So far I had to edit the script to remove "esmart" and "entrance" which are no longer in the repository.

Update: It completed; the basic packages compiled and installed.

---

### Post by wsonar on 2010-03-12
> **VCoolio said:**
> When compiling you need -dev packages; try for example to install libfreetype6-dev and see if that solves it.



```
libfreetype6-dev is already the newest version.
libfreetype6-dev set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by wsonar on 2010-03-12
> **gmargo said:**
> I'm currently compiling the basic packages using the easy_e17.sh script.  So far I had to edit the script to remove "esmart" and "entrance" which are no longer in the repository.

Update: It completed; the basic packages compiled and installed.

What section or lines did you edit I was looking through the script

this was funny

```
        
echo "The most incredible and really unbelievable dream has become true:"
echo "You compiled e17 successfully!"

```

---

### Post by gmargo on 2010-03-12
> **wsonar said:**
> What section or lines did you edit 
Removed "esmart" from the "efl_basic" definition.
Removed "entrance" from the "bin_basic" definition.

Then I tried going the next step and adding --packagelist=half, which quickly bogged down.  Several of the listed modules don't compile.  So I'm done with it.  Clearly one cannot properly compile this stuff unless one is following the development mailing list closely.

---

