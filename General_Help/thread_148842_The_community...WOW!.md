---
title: "The community...WOW!"
date: 2006-03-22
forum: General Help
---

### Post by Patrick-Ruff on 2006-03-22
hey all, I'm VERY impressed with the Ubuntu community, its the only reason I switched from SUSE 10. but yeah, I was just curious to know how the whole Apt-get thing works...does like the community add programs to it or what? because there seems to be an immense library of programs on it...

---

### Post by neoroses on 2006-03-22
anyone can add a program to it but you kan only apt-get it if u have the repo =)

and hell yea this is one good community

---

### Post by taurus on 2006-03-22
If you want to install something, use apt-get or if you are not sure the exact name of the program, use synaptic (GUI) and search for it.
```

sudo apt-get install <program name>

```

---

### Post by Jedeye on 2006-03-22
Glad to have you! the community here was one of the key factors for me as well. I saw this guide on apt-get a couple of weeks ago on digg.com it might be just what you are looking for: [http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html]("http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html") it has all the ins and outs of apt-get

---

### Post by kybishop on 2006-03-22
apt-get is based off repositories, which people put files into

there are official ubuntu repositories, which the ubuntu team puts files into.

in addition there are unofficial repositories, where you can find a number of things, such as legeally tricky software (things like mplayer and dvd rippers)

you can find your list of repositories in /etc/apt/sources.list

i recommend the source-o-matic for generating a better sources.list, just google source generator under google and use away

to use apt-get:
type apt-get update to update your list of packages
type apt-get upgrade to upgrade your packages (upgrades are choosen for your list of packages)
type apt-get dist-upgrade to upgrade your distribution
last, type apt-get install (package name, without ()'s of course)

those are the basics

---

### Post by az on 2006-03-22
[QUOTE=Patrick-Ruff] I was just curious to know how the whole Apt-get thing works...does like the community add programs to it or what? because there seems to be an immense library of programs on it...[/QUOTE]

People write free-libre open source software for a lot of reasons.  Mainly it is because they beleive that software is not property and that you should not have to reinvent the wheel.

Software is a services industry.  The programmer gets paid for writing code.  The code remains free for anyone to use and improve.  Someone else can get paid for imrpoving existing code and so on and so on.  Lots of businesses make money by supporting open-source software like that.  

A surprisingly small percentage of code written by programmers ends up as shrink-wrapped boxed software you buy at the store.  Most code is written by in-house people who are there to solve specific problems.  Free-libre software just makes life easier.

So, applications are written and then they are packaged in a form that makes them interact properly with each other.  That's why there are so many other linux distributions.  They all use pretty much the same applications, but with different versions and configurations.

So each package has a maintainer.  Whatever is in the main and restricted repositories is officially supported by Canonical (a paid maintainer and ofter, a developer).  Most of the other packages (in universe and multiverse) are maintained by the community  - people from MOTU (masters of the universe)

So, yes, there are a lot of packages and a lot of people who tend to them.  There are also people who contribute to documentation (official documentation, forums and mailing lists, IRC) as well as translations, artwork, events...it's almost endless.

---

### Post by Patrick-Ruff on 2006-03-22
yeah it wasent a matter of not knowing and all that, this was mainly a compliment thread. I wanted to know how the apt-get system worked as far as the files on the server. however, can anyone update the Yabasic version on the apt-get servers? its 2 versions old and theres some big changes on the new ver. (this is a programming language btw.) [www.yabasic.de](www.yabasic.de) thank guys.

---

### Post by rossjman1 on 2006-03-22
Here's the complete Apt-get manual: [http://www.us.debian.org/doc/manuals/apt-howto/index.en.html](http://www.us.debian.org/doc/manuals/apt-howto/index.en.html)

---

### Post by Patrick-Ruff on 2006-03-22
yeah thats cool man, but I don't know how to add the new ver, I never got it to install, the apt-get install yabasic was the only way I got it in the first place, but the new ver has alot better stuff in it so yeah


-Patrick

---

### Post by rossjman1 on 2006-03-22
Not everything in the repositories are bleeding edge. If that were so, we would have a very unstable system. Once Dapper gets released, almost everything will(should) be updated. I havn't experienced a new release in Ubuntu, as I come from using Debian Testing, but that's the way Debian did things.

---

### Post by az on 2006-03-22
[QUOTE=Patrick-Ruff]however, can anyone update the Yabasic version on the apt-get servers? its 2 versions old and theres some big changes on the new ver. (this is a programming language btw.) [www.yabasic.de](www.yabasic.de) thank guys.[/QUOTE]

[http://packages.ubuntu.com/dapper/interpreters/yabasic](http://packages.ubuntu.com/dapper/interpreters/yabasic)

The newest version is in Dapper.  To get it, either compile it,  find a backport or wait until Dapper is released and upgrade.

---

### Post by Patrick-Ruff on 2006-03-22
lol thanks man, I'll wait :D. also, another Q. will dapper be an easy upgrade? like will I have to reformat my comp or will it be a smooth install?

---

### Post by NewWithoutClue on 2006-03-22
[QUOTE=Patrick-Ruff]lol thanks man, I'll wait :D. also, another Q. will dapper be an easy upgrade? like will I have to reformat my comp or will it be a smooth install?[/QUOTE]
You don't have to, but comming from Mandriva i did. Basically, you would change every instance of the word "Brezzy" in /etc/apt/sources.list to "Dapper". After that you would issue these commands ```
# apt-get update && apt-get dist-upgrage
```
Again, i know this will upgrade your distro.. but i haven't done this for Dapper. Keep in mind that Dapper is still BETA.

p01n7

---

