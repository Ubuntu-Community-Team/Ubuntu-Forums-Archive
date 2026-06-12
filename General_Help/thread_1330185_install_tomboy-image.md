---
title: "install tomboy-image"
date: 2009-11-18
forum: General Help
---

### Post by s955401 on 2009-11-18
tomboy-image is a plugin which makes us insert images in tomboy.

I found it recently but I don't know how to install it.

Could anyone help me?

Thanks a lot.

here is the link
Official website&#65306;[http://gitorious.org/tomboy-image]("http://gitorious.org/tomboy-image")
introduction&#65306;[http://gitorious.org/tomboy-image/pages/Home]("http://gitorious.org/tomboy-image/pages/Home")

---

### Post by P4man on 2009-11-18
You need mono-gmcs and git for starters:
```

sudo apt-get install mono-gmcs git-core
```
Then grab the source through git:
```
git clone git://gitorious.org/tomboy-image/tomboy-image.git
```
then compile it

```
cd tomboy-image
make
```

If all goes well that should produce the TomboyImage.dll you have to copy as per linked instructions.

If "make" doesnt work, you may have to install build-essentials first.

---

### Post by s955401 on 2009-11-18
it shows error messages when I try to compile it.
```

gmcs /out:TomboyImage.dll "/r:System.dll" "/r:Mono.Posix.dll" "-pkg:gtk-sharp-2.0" "-pkg:glib-sharp-2.0" "-pkg:glade-sharp-2.0" "/r:System.Xml.dll" "/r:System.Data.Linq.dll" "/r:System.Xml.Linq.dll" "/r:System.Core.dll" "-pkg:tomboy-addins" /noconfig /nologo /warn:4 /debug:+ /debug:full /optimize- /codepage:utf8 /define:"DEBUG" /t:library "/res:gtk-gui/gui.stetic,gui.stetic" "/res:TomboyImage.addin.xml,TomboyImage.addin.xml" "AssemblyInfo.cs" "ImageAddin.cs" "ImageInfo.cs" "ImageTag.cs" "gtk-gui/generated.cs"
/bin/sh: gmcs: not found
make: *** [TomboyImage.dll] Error 127

```
and I have installed mono-gmcs, git-core and build-essential

what should I do?

---

### Post by P4man on 2009-11-18
your still missing something.. not too sure, try
```
sudo apt-get install libmono-system2.0-cil
```

Alternatively if you are on 32 bit karmic I can compile it for you, as it seems to compile fine here..

edit: Here is my compile
[http://www.mediafire.com/?j2ttmbhkcdy](http://www.mediafire.com/?j2ttmbhkcdy)

---

### Post by s955401 on 2009-11-18
I found that libmono-system2.0-cil has been installed already.

but anyway, I can use your file even I use 32bit jaunty. thank you very much

---

### Post by joselitux on 2010-04-28
Shall anyone be so kind of compiling a x64 Lucid Version?

---

### Post by P4man on 2010-04-28
Id rather not pull in all those mono dependencies on this system.
But just do this:

```
sudo apt-get install mono-gmcs git-core build-essential gtk-sharp2

```

Then get the source code:

```
git clone git://gitorious.org/tomboy-image/tomboy-image.git
```

change directory to it and compile:

```
cd tomboy-image
make
```

If you get an error, post it here.

---

### Post by joselitux on 2010-04-28
I got an error when executing make


"AssemblyInfo.cs" "ImageAddin.cs" "ImageInfo.cs" "ImageTag.cs" "gtk-gui/generated.cs"
ImageAddin.cs(9,17): error CS0234: The type or namespace name `Addins' does not exist in the namespace `Mono'. Are you missing an assembly reference?


mono-gmcs git-core build-essential gtk-sharp2   are all installed. I use ubuntu x64


any help will be much appreciated. I really need inserting images in tomboy.


thanks in advance

---

### Post by P4man on 2010-04-28
ok.. try this one:

```
sudo apt-get build-dep tomboy
```

Should pull in all dependencies, whatever they are.
then try compiling again

---

### Post by joselitux on 2010-04-28
Same error


ImageAddin.cs(9,17): error CS0234: The type or namespace name `Addins' does not exist in the namespace `Mono'. Are you missing an assembly reference?
Compilation failed: 1 error(s), 0 warnings

---

### Post by P4man on 2010-04-28
Sorry mate, then I dont know how to help you. perhaps contact the devs?

---

### Post by joselitux on 2010-04-29
I've installed and been testing Zim personal wiki. And it's ok for my purposes. Same as Tomboy, but I can insert images.

thanks for your help

---

### Post by Dict on 2010-05-01
> **joselitux said:**
> Same error
[COLOR="Red"]ImageAddin.cs(9,17): error CS0234: The type or namespace name `Addins' does not exist in the namespace `Mono'. Are you missing an assembly reference?[/COLOR]
Compilation failed: 1 error(s), 0 warnings


[B]I have installed build-dep tomboy, mono-gmcs, git-core, gtk-sharp2, libmono-system2.0-cil and build-essential and so on.

But I also got the same error. [COLOR="Red"]I would like to know what the red message mean.[/COLOR] [/B]

How can I install tomboy-image in Ubuntu 10.04 ?

Help,THX!

---

### Post by &#304;skender on 2010-06-18
After installing all the dependencies as suggested, when trying to compile tomboy-image I still got the error:

"ImageAddin.cs(9,17): error CS0234: The type or namespace name `Addins' does not exist in the namespace `Mono'. Are you missing an assembly reference?"

I don't really know anything about Mono or makefiles, but I managed to get it to compile by inserting a reference to Mono.Addins.dll in the makefile, so it reads:


```
TomboyImage.dll:  gtk-gui/gui.stetic TomboyImage.addin.xml AssemblyInfo.cs ImageAddin.cs ImageInfo.cs ImageTag.cs gtk-gui/generated.cs
        gmcs /out:TomboyImage.dll "/r:System.dll" [COLOR="Red"]"/r:Mono.Addins.dll"[/COLOR] "/r:Mono.Posix.dll" "-pkg:gtk-sharp-2.0" "-pkg:glib-sharp-2.0" "-pkg:glade-sharp-2.0" "/r:System.Xml.dll" "/r:System.Data.Linq.dll" "/r:System.Xml.Linq.dll" "/r:System.Core.dll" "-pkg:tomboy-addins" /noconfig /nologo /warn:4 /debug:+ /debug:full /optimize- /codepage:utf8 /define:"DEBUG" /t:library "/res:gtk-gui/gui.stetic,gui.stetic" "/res:TomboyImage.addin.xml,TomboyImage.addin.xml" "AssemblyInfo.cs" "ImageAddin.cs" "ImageInfo.cs" "ImageTag.cs" "gtk-gui/generated.cs"

install: TomboyImage.dll
        cp TomboyImage.dll ~/.config/tomboy/addins
```


Trying to compile now the error that it can't find Mono.Addins.dll (which is in /usr/lib/cli/Mono.Addins-0.2/ on my version of lucid) - presumably this can be fixed with some path settings, but I just linked Mono.Addins.dll to somewhere that obviously was being searched:

```
sudo ln -s /usr/lib/cli/Mono.Addins-0.2/Mono.Addins.dll /usr/lib/mono/2.0/Mono.Addins.dll
```

It then compiles and works correctly. Hope this helps.

---

### Post by The_Eddster on 2010-07-31
a

---

### Post by The_Eddster on 2010-07-31
Ok I've got it compiled, what do I do next? How do I insert images into a tomboy note? There's no image plugin listed in the plugin options

---

### Post by The_Eddster on 2010-07-31
I've got it working now. I missed a step from the tomboy image [website]("http://gitorious.org/tomboy-image/pages/Home"):

> Compile the dll and copy it to ~/.config/tomboy/addins, restart tomboy,
enable the addin, and then restart tomboy.

Thanks for the help guys :)

---

### Post by ArturoGarcia on 2010-10-05
OK, 
PLEASE someone Put **[SOLVED]** on the tittle post, PLEASE!


[FONT=Book Antiqua][SIZE=3]**How to Install** **tomboy-image**[/SIZE][/FONT]
[I][SIZE=1](I just organize the info, everything was all ready here as you can see)[/SIZE]

[/I]Open a terminal and type:
```
$ sudo apt-get install git-core mono-gmcs gtk-sharp2 gtk-sharp2-examples gtk-sharp2-gapi libglade2.0-cil-dev libmono-cecil-private-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-i18n-west1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-system-data1.0-cil libmono-system-web1.0-cil libmono-system1.0-cil monodoc-base monodoc-browser monodoc-gtk2.0-manual monodoc-manual
``````
$ sudo ln -s /usr/lib/cli/Mono.Addins-0.2/Mono.Addins.dll /usr/lib/mono/2.0/Mono.Addins.dll
``````
$ cd && git clone git://gitorious.org/tomboy-image/tomboy-image.git tomboy-image
``````
$ cd tomboy-image && make
``````
$ cp TomboyImage.dll ~/.config/tomboy/addins/

```Now if you have tomboy in gnome-panel close it,
PRESS: ALT+F2 (and type): killall tomboy
PRESS: ALT+F2 (and type): tomboy

Put your tomboy applet on Gnome-Panel again,
That's it,
Now you can put images on Tomboy Notes!! Cool!!


Thanks.
------------ xxx ------------

---

