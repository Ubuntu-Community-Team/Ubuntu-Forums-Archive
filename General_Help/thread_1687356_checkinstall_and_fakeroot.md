---
title: "checkinstall and fakeroot"
date: 2011-02-13
forum: General Help
---

### Post by ianc1 on 2011-02-13
I want to install Rubyripper from the source code which you can get at [http://code.google.com/p/rubyripper/](http://code.google.com/p/rubyripper/) , which as its name suggests is in Ruby.  There are instructions to install which seem obvious but if my understanding is correct installing from source will place files here and there throughout the file system with no log of this making remove difficult/impossible.

So I want to build a deb and install with this.  Now the question.  I have seen checkinstall mentioned which will build a deb to install with the package manager.

My concern is this has a dependency called fakeroot.  From its name it sounds dodgy.  Is this safe/secure?

Cheers

---

### Post by luigi_mb on 2011-02-13
I built and installed v0.6.0 on Lucid with no problems. The files are copied to the correct folders. The application can be uninstalled from the source folder (so, keep it and don't change anything after installation):

```

sudo make uninstall

```


/luigi

---

### Post by mc4man on 2011-02-13
> From its name it sounds dodgy. Is this safe/secure?
absolutely fine, just  tool for package building.

something like this should suffice
```
sudo checkinstall --fstrans=no --default --deldoc  --pkgversion 0.6
```

Note: you will find running the rip&encode thru the gui to be quite slow due to a fault in the current ruby used in ubuntu 
easiest way around is to set up in the gui, then call RR thru the command line

```
rrip_cli -d  
```
will just go ahead and rip the complete cd w/ no or little interaction.
The fix for that is in my last post here (174), though does require a little work.
[http://ubuntuforums.org/showthread.php?t=799621&page=9&highlight=rubyripper](http://ubuntuforums.org/showthread.php?t=799621&page=9&highlight=rubyripper)

---

### Post by ianc1 on 2011-02-14
Thanks for all the info.  Two remaining queries.  If I don't use check install how do I know the code installs things in appropriate places and therefore what it should remove.

Regarding fakeroot what exactly does it do?

And thanks for the tip regarding command line usage of ruby ripper I had previously used it from aheck ppa and had ind found it very slow.  If the problem is a ruby one is it worth worth upgrading ruby, if this is at all possible.

Cheers

---

### Post by mc4man on 2011-02-15
> . If I don't use check install how do I know the code installs things in appropriate places .
If it works then things got installed properly. (in most cases..

> therefore what it should remove.
Sources that include a make uninstall will remove whatever they installed, that simple.

The downsides are  - some sources don't have a make uninstall, in those cases you'll need to remove manually.
For those that do you have to keep the source folder 'as is', or sudo make uninstall will not work.

In most cases far better, if possible, to use checkinstall or build debian packages. Removal is easy, and the 'system' knows it's installed,  also useful when the package 'provides' something for other packages

There are some sources not suitable for checkinstall, and once in a while one might want to build and install a source without the 'system' knowing it's been installed.
(I've have a post on building an aoTuV tuned oggenc that uses just that 

I think your looking at "fakeroot" in the wrong light, as mentioned it's just a package building tool, used by checkinstall and also for debian package creation.

Ex.  - from a build log on a unity build I did recently using debuild, the actual build command
>  dpkg-buildpackage -rfakeroot -D -us -uc
I'm not up on the actual tech. explanation, work more on a need to know basis.
Probably allows permissions to be set, ect. and in the case of checkinstall go ahead and install the package without any intervention.

> If the problem is a ruby one is it worth worth upgrading ruby, if this is at all possible.
It's quite possible, in the thread I linked and post # noted (174) is a step by to doing so.
Whether it's worth it is up to the individual.

---

### Post by ianc1 on 2011-02-15
Many thanks for the extra info.  I guess just the name fakeroot puts me off as it implies something is faked or exploited.  I was therefore concerned that fakeroot would leave my pc open to exploits (well more so than it is anyway).

> 
The downsides are  - some sources don't have a make uninstall, in those cases you'll need to remove manually.
For those that do you have to keep the source folder 'as is', or sudo make uninstall will not work.
Do you mean leave the directly where it is when I run check install and do not touch.

Thanks

---

