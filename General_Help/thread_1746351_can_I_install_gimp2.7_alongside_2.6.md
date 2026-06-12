---
title: "can I install gimp2.7 alongside 2.6?"
date: 2011-05-01
forum: General Help
---

### Post by bobdobbs on 2011-05-01
Hi all.

I'm running gimp2.6 on ubuntu 10.10.

I need to use gimp for everyday work. 2.6 is stable, but I'm curious about the development version. A recent post on the gimp developers list referred to 2.7 as "only mildly buggy".

Is there a way to install 2.7 alongside 2.6? I'd like to be able to run one or the other. I'd like to be able to install 2.7, but have the option of running 2.6 with all it's neccessary libraries unintefered with.

Is this possible? Is there an existing guide?

Thanks.

---

### Post by electricmaster on 2011-05-01
Uh, as far as I know, it's not possible to have two versions of a program installed at the same time.

---

### Post by bobdobbs on 2011-05-01
In theory it is quiet possible. 

On my own system, I've got more then one version of the ruby interpreter.

As far as I can tell, you would have to have the binaries either named differently or sitting in different paths for a start. That part seems easy.

The difficult part, as far as I can work out, is handling dependencies. If multiple versions of the same program are installed, they might require different versions of the same libraries. That's where things get tricky. But even that's possible to resolve with commandline switches.

There might be other issues that I'm not aware of. But I'm certain that it is possible to install more then one version of a program.

---

### Post by stoneage on 2011-05-01
With some applications this is easy, with others it is more difficult.

Mostly it depends how you intend to install. Installing from a .deb will overwrite the version you already have installed, but if you build from source you can specify a custom install location. As you say, it is possible a later version will require dependencies you don't have, though these can also be built from source, and in some cases you can use the development libs that are already available.

I have two versions of Gimp installed, but one of them is compiled from source.

---

### Post by bobdobbs on 2011-05-01
Do those two version happen to be 2.6 and 2.7?

If so, how did you do it?

Do you know if there is a guide somewhere online?

---

### Post by stoneage on 2011-05-01
No, they don't, and to be honest it was a royal pita to get it all working. I even managed to do some damage installing an updated glib from source. Nothing serious, just parts of the system were using the newer version of glib, which other libs were too old to utilise, and hence things broke.

There are guides on building Gimp:-
[http://www.gimp.org/source/#source](http://www.gimp.org/source/#source)
[http://www.gimp.org/source/howtos/gimp-git-build.html](http://www.gimp.org/source/howtos/gimp-git-build.html)

It is pretty straightforward, but be careful with installing updated dependencies.

If you can stand losing 2.6 there is a Gimp ppa which is updated fairly regularly:-
[https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn](https://launchpad.net/~matthaeus123/+archive/mrw-gimp-svn)

---

### Post by bobdobbs on 2011-05-01
I want to avoid losing 2.6. 
I need it for the work I do.

Martins guide is good for installing gimp2.7, but no good if you want to keep 2.6 at the same time. As far as I can tell, the guide assumes that you have the prerequisites installed. However, afaik you have to have latest builds of gegl and babl - which aren't in the ubuntu repos.


I've found a guide here:
[http://gimpchat.com/viewtopic.php?f=10&t=1261](http://gimpchat.com/viewtopic.php?f=10&t=1261)

I've stepped through most of it, installing everything in the prefix /home/me/opt

The problem I'm having now is that when I run make in the gimp directory, gimp just refuses to pick up the babl libs, no matter what I do.

I'm pointing BABL_LIBS at the directorties '/home/me/opt/lib/babl-0.1' '/home/me/opt/lib', /home/me/opt/babl', with no avail.
I'm also providing those same parameters to PKG_CONFIG_PATH.

This is what always gets me when I try to build things from source on linux: make scripts often produce dreadfully frustrating results: the requisites are present, but the build scripts stubbornly refuse to pick them up. :(

---

