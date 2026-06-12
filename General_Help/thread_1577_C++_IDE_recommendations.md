---
title: "C++ IDE recommendations?"
date: 2004-10-21
forum: General Help
---

### Post by akadajet on 2004-10-21
I'm fairly new at Linux and would like to mess around with C++ in Ubuntu. I'm used to Visual Studio 6 in Windows, and was wondering what you would recommend as a IDE in Ubuntu. I'm getting the KDevelop package right now, and was wondering if there is anything else I should try.

Thanks!

---

### Post by JProgrammer on 2004-10-21
You could try [anjuta](http://anjuta.sf.net) it is a gnome based IDE so might be more suited to a Ubuntu install rather than KDevelop

---

### Post by akadajet on 2004-10-21
[quote=JProgrammer]You could try [anjuta](http://anjuta.sf.net) it is a gnome based IDE so might be more suited to a Ubuntu install rather than KDevelop[/quote]

Will give it a try. Thanks!

---

### Post by FLeiXiuS on 2004-10-22
For a sweet C++ Compiler I would recommend 'G++'. 8)

---

### Post by elwis on 2004-10-22
Actually, KDevelop is superior, but it's true that it won't fit that nicely into your GNOME Desktop. And if you're like me, you like a GNOME Desktop to contain GTK applications, no mixing thank you! ;)

Hopefully, Anjuta will catch up, until then.. and if you won't like it, there's always Emacs.. just read the manuals ;)

---

### Post by soulglo83 on 2007-07-19
[http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu]("http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu")

code::blocks is easily the best c++ ide for ubuntu.  if you want code completion and great default syntax highlighting you want to use code::blocks.  get the latest available svn though, there last stable release is way outdated and bug riddled.  if you have ever used visual studio you will feel right at home (albeit without some of the .net stuff :( )

---

### Post by Immolatus on 2007-07-19
Mono

---

### Post by soulglo83 on 2007-07-27
[geany]("http://geany.uvena.de/")

I forgot to mention what I use when I'm on the road w/ my old puppy linux laptop (p2 266 48mb ram).  Even on a crumby computer I still have syntax highlighting, code completion/folding/etc.  Really nice IDE has lots of features that are unbelievably useful (like built in terminal emulation).  Oh and its very extendable and requires few dependancies.  Geany is very polished, easy to use, and extendable, probably better than code::blocks now that I think about it!

---

### Post by capturesteve on 2007-07-27
> **soulglo83 said:**
> [http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu]("http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu")

code::blocks is easily the best c++ ide for ubuntu.  if you want code completion and great default syntax highlighting you want to use code::blocks.  get the latest available svn though, there last stable release is way outdated and bug riddled.  if you have ever used visual studio you will feel right at home (albeit without some of the .net stuff :( )
Yeah code::blocks is the most similar to VS.

---

### Post by Lord Illidan on 2007-07-27
geany is v. good

---

### Post by Akacko on 2007-10-16
i'm new in linux too. I've tried Geany and i can only recommend it!

---

### Post by twright on 2007-10-29
I'm happily using eclipse C++

just one thing, you need to run sudo apt-get install sun-java6-jre first

---

### Post by doctorbighands on 2007-11-02
[EDIT]

I recommend Geany. Anjuta is NOT (I repeat, NOT) intuitive or user-friendly. If you've ever used VS (or if you just want something that works easily and perfectly), use Geany. You'll feel right at home.

---

### Post by deadimp on 2007-11-03
Just installed geany and screwed around with it some and it was pretty nice. Thing is, can you customize syntax highlighting?

> just one thing, you need to run sudo apt-get install sun-java6-jre first
Shouldn't that be included in the list of dependencies?

---

### Post by twright on 2007-11-10
it's just distributed as a .tar.gz so it doesn't have dependencies, you just extract it where you want it (it's one package for all Linux based systems)

if you install it from a repository using sudo apt-get eclipse you will just get eclipse classic (for java) and it will do something else for a virtual machine


you can get it from here:
[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)

it has the best interface of any IDE i've worked with

---

### Post by Serpentinsek on 2008-02-22
What about Eclipse CTD - C++/C "plugin"
If you have eclipse allready installed here is a instalation tutorial 
[http://max.berger.name/howto/cdt/ar01s04.jsp#installingcdt](http://max.berger.name/howto/cdt/ar01s04.jsp#installingcdt)

---

### Post by FunkyJack on 2008-02-22
Geany is very good.

---

### Post by azizus on 2008-03-17
Try Java NetBeans IDE 5 or greater with C/C++ package. Works good for me 

Regards

---

### Post by spupy on 2008-03-17
I just read the Emacs tutorial, and it looks (geek-ish) cool. Is it worth to continue learning Emacs, or switch to Eclipse/C++ or Geany? Anjuta is bloated for my standarts; I use Eclipse for Java at work, but I've never tried Geany.

---

### Post by twright on 2008-03-20
emacs is great but you will have to compile and everything manually so if you are comfortable with the terminal then emacs is a good choice

---

### Post by kpkeerthi on 2008-03-20
+1 for Eclipse + CDT

---

### Post by ShrapnelHunter on 2008-05-23
Netbeans, fer sure

---

### Post by gmagno on 2008-07-13
Geany is just great!! I just would like to ask if Geany has code completion feature.

---

### Post by cajmrn on 2008-07-14
Just finished setting up Eclipse + CDT, easy and works great! it gets my vote for sure.

---

### Post by auxis on 2008-07-15
> **gmagno said:**
> Geany is just great!! I just would like to ask if Geany has code completion feature.

Yes, it has code completion, which is a great plus for me.

Also, for those of you that are having trouble figuring out where to edit syntax highlighting (quoted from the help file):

The system-wide configuration files can be found in $prefix/share/geany and are called filetypes.$ext, where $prefix is the path where Geany is installed (commonly /usr/local) and $ext is the name of the filetype. For every filetype there is a corresponding definition file. There is one exception: filetypes.common -- this file is for general settings, which are not specific to a certain filetype. It is not recommended to edit the system-wide files, because they will be overridden when Geany is updated.

To change the settings, copy a file from $prefix/share/geany to the subdirectory filedefs in your configuration directory (usually ~/.geany/).

For example:
```

% cp /usr/local/share/geany/filetypes.c /home/username/.geany/filedefs/

```
Then you can edit the file and the changes are also available after an update of Geany because they reside in your configuration directory. Alternatively, you can create a file ~/.geany/filedefs/filetypes.X and add only these settings you want to change. All missing settings will be read from the corresponding global definition file in $prefix/share/geany.

---

