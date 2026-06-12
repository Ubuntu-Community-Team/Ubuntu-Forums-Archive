---
title: "GNOME critical failure"
date: 2011-03-09
forum: General Help
---

### Post by nkae100 on 2011-03-09
Ubuntu - 10.04 LTS
zlib - 1.2.5


Why does GNOME fail to start correctly after compiling the latest version of Zlib?

I have analyzed the situation. Zlib does not change or delete any file on the file system.

I have asked this on three occasions over the last 8 months and no one has been able to give me an explanation, so it would be a great challenge for the Ubuntu lovers. I am also EXTREMITY interested to find out why, because I have had a hard spot negative opinion against GNOME since this occurred.

---

### Post by nkae100 on 2011-03-11
So the problem is too complex for everyone?

---

### Post by cchhrriiss121212 on 2011-03-11
> **nkae100 said:**
> So the problem is too complex for everyone?
Perhaps it is, but you could help by offering more information on the problem:
How exactly is gnome behaving?
The output of any error messages
Why you need the latest zlib instead of the ones in the repos
etc.

---

### Post by nkae100 on 2011-03-11
It just doesn't load. Take a look for yourself. Its a perfect demonstration how pathetic GNOME is becoming.

I went to report it to GNOME, but theirs no simple contact point on their head ache of a website.

---

### Post by cchhrriiss121212 on 2011-03-12
You would be better off filing a bug with Ubuntu or zlib.

---

### Post by nkae100 on 2011-03-14
Ubuntu arn't the developer of GNOME, nor is Zlib.

---

### Post by cchhrriiss121212 on 2011-03-14
You have not yet determined whether the issue stems from zlib or Ubuntu's implementation of GNOME.

Try it out on a Debian GNOME system first if you want to take this to GNOME. Or better yet, switch to a newer OS, if you want the latest software (like zlib 1.2.5) then a long term release of Ubuntu is not for you.

---

### Post by nkae100 on 2011-03-15
Like I said, when I compiled Zlib it did not touch any existing file on the file system... all it did was place about 10 files in a directory. What I am saying is that if placing a few files in a directory is all it takes to brake GNOME, then GNOME is crap in terms of survivability.

I don't really see how Debian is going to make a difference. Debian and Ubuntu are just distributors. At the end of the day they use common software with the exceptions of a few art modifications. Know what I mean?

I don't think there is any perfect distro for me. I would like to build my own, but people like gnome.org make it ridicously difficult to download their software.
For example, I went to 'Latest Release' on the front of their webpage. It talks about getting GNOME and the tarballs for it etc, yet doesn't actually provide a link to them. How stupid. I also tried to find a contact point to report this stupid design, yet couldn't find an easily accessable one, so I fell back on contacting WHOIS data. I didn't get a reply so I've given up on GNOME, which is a shame.

---

### Post by cchhrriiss121212 on 2011-03-15
> I don't really see how Debian is going to make a difference.
Because Ubuntu does not use a straight GNOME desktop, it has it's own modified version (they do more than just swap a few icons). When filing a bug report, you should go through the channels set up by your distro, that is what they are there for. 
> 
 For example, I went to 'Latest Release' on the front of their webpage.  It talks about getting GNOME and the tarballs for it etc, yet doesn't  actually provide a link to them. 
Linux distros make use of a unified package management system, that means you don't need to download everything from maintainer websites. You are using the Windows approach to software installation, which is why you are getting problems.

> I would like to build my own, but people like gnome.org make it ridicously difficult to download their software.
Try a Debian net install for complete control, or even Arch if you like the very latest packages. If you start using the package manager, installing software is incredibly easy.

---

### Post by nkae100 on 2011-03-15
Yes, I totally agree with you about the ease of packages, but I don't want some modified vendor version of the software, I like the generic version direct from the developer. :)

---

### Post by cchhrriiss121212 on 2011-03-15
Package maintainers do not modify the software, they just make it easier to install. If any maintainer does deliberately modify the software they have to change the name (to use our example above, Ubuntu has the package ubuntu-desktop instead of gnome-desktop). If you compare any software package in tar.gz and .deb format, they will both be the same.

FWIW I also avoided the package manager when I started using Ubuntu, and I had similar problems to yourself. Once I got used to always going through the package manager, everything got so much easier.

---

### Post by nkae100 on 2011-03-15
Still, the problem I faced didn't actually change any files on the drive what so ever, it just added files... Try it yourself in a virtual machine and you will see this yourself... You'll then see GNOME fail on restart. Once you delete the files it added, everything works again. Pretty pathetic IMO.

---

### Post by cchhrriiss121212 on 2011-03-15
I did try it, and it did fail (why it failed I have no idea).

But the problem stems from the fact that you are not using the official sources. Ubuntu 10.04 is built for stability, not for using the latest packages. You are using the OS in a way that is not designed for.

Is there any reason why you need zlib 1.2.5 instead of the stable version 1.2.3 that is included with Ubuntu?

---

### Post by nkae100 on 2011-03-16
I was new at the time to Linux and wasn't aware of packages made for different distro's etc.

But I don't like this version for this distro and that version for that. It makes Linux not have any traction. I believe everything should be compiled from the official source code only.

Library regression shouldn't be happening at all. Its wrong to call a library 'stable' when it suffers regression.

My next distro install may be Debian stable... but if I get time I would like to download the Linux kernal and compile it, along with GNOME and every other application out there using the official source only.

---

### Post by cchhrriiss121212 on 2011-03-16
> Library regression shouldn't be happening at all. Its wrong to call a library 'stable' when it suffers regression.
There isn't any library regression going on here, so I don't know what you are referring to.

> but if I get time I would  like to download the Linux kernal and compile it, along with GNOME and  every other application out there using the official source only.
[B]Please do not do this. 
[/B]
I think you are still unclear on how packaging works on Linux. You have confused official software with stable software, perhaps that is my fault for not explaining properly.
 
The versions in  the repository are the official versions, but they are older  versions from the ones you will find on maintainer websites. They are older because it takes time to get all packages working together nicely without breakages.

When you go to a software developers site, you will be given their latest version, not the version that has been widely tested for your distro.

> My next distro install may be Debian stable... 
If you start compiling everything from source, you will no longer be using Debian stable. Stability is achieved through many months of testing packages, if you ignore the repos you will have a complete mess of a system.

If you want to ignore repositories, there is essentially no point to using Debian, Ubuntu or any other usable Linux OS. **The repositories are the distro**, I can't stress that point enough.

---

### Post by nkae100 on 2011-03-16
The question I guess is why don't latest stable versions work without braking other things? Is this because they use shared libraries.. updated libraries are not so compatible as they were in the previous version? Preferably, coders should be doing a better quality job then, but then they could also use the option of using a dedicated library which ships with their software.

Repositories make you have to be dependent on another party - having to wait while the package is made by them. How annoying. Compiling from source does not have this issue.

---

### Post by cchhrriiss121212 on 2011-03-16
> The question I guess is why don't latest stable versions work without breaking other things?Well that is just the nature of software, "stable" versions have to be released with unknown amounts bugs in (as it is easier to let users report them, than pay someone to do it). This is the advantage of using something like Debian stable, which actually lives up to it's name with the hard testing work and methods they have developed over many years.
> 
Repositories make you have to be dependent on another party - having to  wait while the package is made by them. How annoying. Compiling from  source does not have this issue.If you really want the latest software, you need a rolling release distro. Ubuntu and Debian are fixed distros.

You just have to be pragmatic about this: do you want the latest software with potential breakages every update? Or do you want reliable stability with slightly older software? You can't have the best of both worlds.

I have tried a few rolling distros, and for my usage, they are not worth it. If you want a machine you can rely on, then a stable OS is the way to go, the types who prefer Arch and such are those who enjoy tinkering and fixing things for fun (which is fine if you like that sort of thing).

---

### Post by nkae100 on 2011-03-19
I guess you can still go about compiling only, but using stable source releases, right?

---

### Post by cchhrriiss121212 on 2011-03-19
You could do that, but it would take hours of extra research. Some factors to consider:
which version will work? - it is near impossible to select this with a completely customised distro
dependency issues - literally thousands of libs out there, in addition to [Dependency hell]("http://en.wikipedia.org/wiki/Dependency_hell")
un-/installation procedures - you will need to set up your own methods of which directory to install to, using [checkinstall]("https://help.ubuntu.com/community/CheckInstall") would help, but it is not great compared to apt-get or aptitude

If you want to do this as a learning experience, or for fun, then you should go for it. Just don't expect it to work properly.

---

### Post by nkae100 on 2011-03-20
The way I see it is if something is stable then it should not suffer any regression. If libraries are suffering regression then they are not stable.

If developers could produce stable software like this, then the only thing should matter is that you find out if its the minimal version required.


This is why I hate talk of 'distro'. Software is software. All a distro indicates is a version and potential modification to that software, which then means your not really running the official software.

If there are thousands of libs out there, then all software developers should include direction to the official source of that lib, or, include that lib with the application itself (like Windows software does = no installation drama)

> If you want to do this as a learning experience, or for fun, then you should go for it. Just don't expect it to work properly.

I would like to create my own distro, where everything is official software with 0 modification.

Fedora is an example of a bull **** way of calling something its not. Fedora aint Linux in my book. Its a modified version of Linux... Know what I mean?

---

### Post by cchhrriiss121212 on 2011-03-20
> The way I see it is if something is stable then it should not suffer any regression. If libraries are suffering regression then they are not stable.
All software suffers regression, if it doesn't, then it is not being worked on. That's why we have fixed stable distros, and rolling unstable distros.
> All a distro indicates is a version and potential modification to that software, which then means your not really running the official software.
I don't follow your logic here at all.
> If there are thousands of libs out there, then all software developers should include direction to the official source of that lib, or, include that lib with the application itself (like Windows software does = no installation drama)
I will try to make this simple:
This is Linux, Linux is not Windows. 
On Linux you do not compile everything from source.
Use the package manager and there will be no drama.
> Fedora is an example of a bull **** way of calling something its not. Fedora aint Linux in my book. Its a modified version of Linux... Know what I mean?
Not really. Could you explain more? What exactly do you mean by modified?

---

### Post by mcduck on 2011-03-20
> **nkae100 said:**
> Yes, I totally agree with you about the ease of packages, but I don't want some modified vendor version of the software, I like the generic version direct from the developer. :)

In that case you don't want Ubuntu, or Debian, or Arch, or Gentoo. Or any other existing distribution, for the matter.

What you are looking for is [LFS]("http://www.linuxfromscratch.org/lfs/").

Of course once you get a working setup that way, you actually are running a Linux distribution, it's just one that you have made yourself. But it's still a selection of certain versions of oftware from different sources, built to work together and behave based on some person's idea how things should be. Which is pretty much the definition of a Linux distribution. :D

Also you are confusing stability of a single software package and stability of the complete working operating system. A single package from it's developers is stable if the developers consider it's as free of bugs as possible and works correctly, while introducing it into working system with all the other packages would still result in unstability. Simply because the package is differetn than what all the orther  packages are expecting. A new version of a program is of course different fro the old version, otherwise it wouldn't even be anew version. :D

What comes to including all the used versions of libraries bundled with the software, I'd rather have a single library that works with all my programs than hundreds of copies of the same library, all eating my hard drive space and memory. That's just not effective way of handling things. Not from any point of view.

---

### Post by nkae100 on 2011-03-21
> Use the package manager and there will be no drama.


This is not true. Prior this week I did not have the INTERNET for two months. I would goto internet cafes and download packages, come home and try to install them, only to find the package depended on other packages. Unbelievable - completely defeated the purpose of being packaged.

> "Not really. Could you explain more? What exactly do you mean by modified?"

Compile the official relative Linux kernal and then compile the 'Linux' kernal which is shipped with Fedora and then run an MD5 checksum. You will see they do not match.

The Fedora distro claims to be Linux, they should stop kicking **** and state its a modified version.


mcduck you are absolutely spot on with what I would like to do.

Yeah, I know Ubuntu is modified as well. The install of Ubuntu that I have installed is the original install of Linux onto my system. I didn't know much about Linux at the time. My next install will be Linux from scratch for sure!

> What comes to including all the used versions of libraries bundled with the software, I'd rather have a single library that works with all my programs than hundreds of copies of the same library, all eating my hard drive space and memory. That's just not effective way of handling things. Not from any point of view.

I agree it will eat allot of space. But what really needs to happen is that updated library versions need to be better quality coded, so they are backwards compatible with their previous libraries.

---

### Post by cchhrriiss121212 on 2011-03-21
> **nkae100 said:**
> This is not true. Prior this week I did not have the INTERNET for two months. I would goto internet cafes and download packages, come home and try to install them, only to find the package depended on other packages. Unbelievable - completely defeated the purpose of being packaged.

The package management system is reliant on a net connection. There are some places that will offer packages (and their dependencies) on a DVD and ship them to you. Users without internet connections say they are quite useful.

---

### Post by nkae100 on 2011-03-21
Yeah, thats where Linux developers fail hard.

---

