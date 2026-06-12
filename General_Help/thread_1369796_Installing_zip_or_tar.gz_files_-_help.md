---
title: "Installing zip or tar.gz files - help"
date: 2010-01-01
forum: General Help
---

### Post by mersey on 2010-01-01
HI,
I'm new to Ubuntu. I've loaded it as dual boot with Windows XP & I'm now trying to find equivalents for some Windows utilities. I have found two possible replacements for *allway sync* but how do I install them?

One is Synkron and the other is FreeFileSync both downloadable from sourceforgenet. But they come as packages, one as a tar.gz and one as a zip.

What do I do now? In Windows there is an .exe or install file. But I can't see anything like that in these.

---

### Post by sisco311 on 2010-01-01
Try [rsync]("apt://rsync") or if you need a GUI [grsync]("apt://grsync"). Both are in the repositories. You can install them via *Ubuntu Software Center* or *Synaptic*.

[uhelp]community/rsync[/uhelp]
[uhelp]community/BackupYourSystem[/uhelp]

---

### Post by northrup on 2010-01-01
[http://www.cyberciti.biz/faq/install-tarballs/]("http://www.cyberciti.biz/faq/install-tarballs/")

That should help with guiding you through the process of installing from tar.gz archives.  It's a handy skill to be familiar with when you start running into software outside of the repositories.

That I know of, .zip archives aren't suitable for installation on Linux, though, depending on the contents, it might be possible.

---

### Post by Wardje on 2010-01-01
> **northrup said:**
> That I know of, .zip archives aren't suitable for installation on Linux, though, depending on the contents, it might be possible.

The type of container doesnt really matter as long as you got the program to unpack the contents, does it?
Whether your files are packaged in a tarball or a zip file, the unpacked files are the same O:)

---

### Post by mersey on 2010-01-02
I realise you are all trying to be helpful but are you really telling me that to simply install a program in Ubuntu I have to start compiling a program and running command line instructions?

In Windows I just download a program and run the install  routine. 

When I Installed Ubuntu everything went very smoothly and just worked. It found all the drivers I needed. It even recognised my wireless mouse. I was very impressed but now it looks like it's going pear shaped fast.

---

### Post by mkvnmtr on 2010-01-02
I think it depends on how the package is written, I installed gdeb installer and quite often I just double click on the tar and the installer just installs it. That said it is very rare that you will need to go outside the repositories for software.  It is much better to me to enable a repository for a package and get updates than just install and have to remove to update the program.

---

### Post by underquark on 2010-01-02
sisco311 is suggesting alternatives for you which will install like you want.  If you go "off-piste" i.e. find software not in the Repository then you will most likely encounter them in a tarball or other compressed file.  It's the same with a lot of Windows shareware and freeware - they don't all come with installers.  Download the tarball, create a new directory, put the tarball in there and extract its files in that directory.  There often will be a ReadMe file to help with installation.

---

### Post by sisco311 on 2010-01-02
> **mersey said:**
> I realise you are all trying to be helpful but are you really telling me that to simply install a program in Ubuntu I have to start compiling a program and running command line instructions?

In Windows I just download a program and run the install  routine. 

When I Installed Ubuntu everything went very smoothly and just worked. It found all the drivers I needed. It even recognised my wireless mouse. I was very impressed but now it looks like it's going pear shaped fast.

[http://psychocats.net/ubuntu/installingsoftware]("http://psychocats.net/ubuntu/installingsoftware")

---

### Post by mersey on 2010-01-02
> **sisco311 said:**
> [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

Thanks, but I've been through that. I got down to the end where it says:

If you have trouble installing a .tar.gz file, you can ask for help on [the Ubuntu Forums]("http://www.ubuntuforums.org/"). :)

I've now tried something else. I found Synkron has been packed up by Pete Deremer - see

[https://launchpad.net/~sportman1280/+archive/ppa]("https://launchpad.net/%7Esportman1280/+archive/ppa")

Went through all the process given there to set up the software source, ran the recommended sudo commands but it just fails.

Come on guys. This is no way to promote a serious operating system. Windows installation just works easy peasy, and every time in my (long) experience.

---

### Post by 3rdalbum on 2010-01-02
> **mersey said:**
> When I Installed Ubuntu everything went very smoothly and just worked. It found all the drivers I needed. It even recognised my wireless mouse. I was very impressed but now it looks like it's going pear shaped fast.

You're attempting to use Linux like you would use Windows.

In this order, look for:

1. Programs in the Ubuntu repository (Ubuntu Software Center or Synaptic Package Manager)
2. Programs available from other repositories that can be added to your system
3. Programs in Debian package format (.deb)
4. Programs in RPM (.rpm) package format or 'binary installers' (where it's precompiled and you run the file to install it)
5. Source code that must be compiled.

When in Rome, do as the Romans do.

Source code is the lowest common denominator - it works regardless of distribution, CPU architecture (as precompiled binaries can only be used on the CPU architecture they were compiled on) and sometimes even operating system. That's why it's so widely distributed.

On Windows, all software developers got into the habit of just making a binary installer for everything. This practice caught up with them when Microsoft ported Windows to the Itanium architecture, and it continues to cause problems today with Windows' transition to 64-bit. And if Microsoft wants to port regular Windows to the ARM CPU architecture (which has been rumoured) then NONE of the existing Windows software will work on it.

We've never had those problems.

If a program does not have a PPA repository or a .deb package made of it, then it's not popular enough or mature enough for you - that's what I say. If it has been packaged for Ubuntu, that means that at least one unrelated person has considered it worthwhile.

Now I'm not familiar with any of that software you've mentioned, but there's Ubuntu One preinstalled to provide a cloud sync solution - is this what you're talking about?

---

### Post by 3rdalbum on 2010-01-02
> **mersey said:**
> 
I've now tried something else. I found Synkron has been packed up by Pete Deremer - see

[https://launchpad.net/~sportman1280/+archive/ppa]("https://launchpad.net/%7Esportman1280/+archive/ppa")

Went through all the process given there to set up the software source, ran the recommended sudo commands but it just fails.

How old exactly is that software? They stopped packaging it 49 weeks ago (the last package was for Ubuntu 8.10). Sounds like an abandoned project.

> Windows installation just works easy peasy, and every time in my (long) experience.

Not if you try to install old software in Vista/7, which is the equivilant of what you're trying to do here.

And it's not like all is rosy on Windows with recent software; I tried installing the latest Paint.NET on a friend's Win7 computer and ran into dependency hell with the .NET framework. Atrocious.

---

### Post by Leppie on 2010-01-02
> **3rdalbum said:**
> > Windows installation just works easy peasy, and every time in my (long) experience
And it's not like all is rosy on Windows with recent software; I tried installing the latest Paint.NET on a friend's Win7 computer and ran into dependency hell with the .NET framework. Atrocious.

In my long and extensive experience, windows installs are by far from "always easy peasy". one of the things that imho is really weak on windows systems is for example installing software for unprivileged users. even large companies and corporations have to work with workarounds for this (like providing *permanent* local admin rights) in order to achieve these simple tasks. also, like 3rdalbum stated, windows does not at all take care of the dependencies. some of the software houses built this into their installer as a courtesy, but the system does not care at all.

---

### Post by mersey on 2010-01-02
> **3rdalbum said:**
> You're attempting to use Linux like you would use Windows.

In this order, look for:

1. Programs in the Ubuntu repository (Ubuntu Software Center or Synaptic Package Manager)
2. Programs available from other repositories that can be added to your system
3. Programs in Debian package format (.deb)
4. Programs in RPM (.rpm) package format or 'binary installers' (where it's precompiled and you run the file to install it)
5. Source code that must be compiled.

When in Rome, do as the Romans do.

Source code is the lowest common denominator - it works regardless of distribution, CPU architecture (as precompiled binaries can only be used on the CPU architecture they were compiled on) and sometimes even operating system. That's why it's so widely distributed.

On Windows, all software developers got into the habit of just making a binary installer for everything. This practice caught up with them when Microsoft ported Windows to the Itanium architecture, and it continues to cause problems today with Windows' transition to 64-bit. And if Microsoft wants to port regular Windows to the ARM CPU architecture (which has been rumoured) then NONE of the existing Windows software will work on it.

We've never had those problems.

If a program does not have a PPA repository or a .deb package made of it, then it's not popular enough or mature enough for you - that's what I say. If it has been packaged for Ubuntu, that means that at least one unrelated person has considered it worthwhile.

Now I'm not familiar with any of that software you've mentioned, but there's Ubuntu One preinstalled to provide a cloud sync solution - is this what you're talking about?

Hi thanks for the comments.

Re-Ubuntu One - no, I just want to sync files between my hard disc and a memory stick. Something with a nice graphical front end. It also needs to have a windows version so I can use it in either platform. I've tried Unison but it doesn't recognise my memory stick.

---

### Post by Mark Phelps on 2010-01-02
> **mersey said:**
> I realise you are all trying to be helpful but are you really telling me that to simply install a program in Ubuntu I have to start compiling a program and running command line instructions?

In Windows I just download a program and run the install  routine. 

When I Installed Ubuntu everything went very smoothly and just worked. It found all the drivers I needed. It even recognised my wireless mouse. I was very impressed but now it looks like it's going pear shaped fast.

If you're going to hang around in the Linux community, you need to be willing to learn new ways of doing things -- like installing software that isn't offered through the usual package channels.  

Whining about how it's easier in MS Windows won't get you sympathy or help.

---

### Post by mersey on 2010-01-03
> **Mark Phelps said:**
> If you're going to hang around in the Linux community, you need to be willing to learn new ways of doing things -- like installing software that isn't offered through the usual package channels.  

Whining about how it's easier in MS Windows won't get you sympathy or help.

I am willing to learn new ways of doing things. That's why I'm learning Ubuntu. I've been learning all through my computing career, from mainframe programming to PC and network support.

But if you and the Linux community want it to be more than a playground for computer geeks; if you want Linux to be a serious player in the desktop OS world, then you need to understand that:
1. Command line processing went out with DOS. It's been a GUI world for the last 14/15 years, since Windows 95.

2. Applications should just install smoothly with a single clickable installion routine.

When in Rome do as the Romans do - yes, but the Roman Empire collapsed 1500 years ago.  If you don't want Linux/Ubuntu to disappear into history then it needs to get its act togther.  Ubuntu 9.10 is excellent in many ways and some of the mainstream packages (Open Office, Firefox, etc.) are excellent. But a useful OS needs lots of crackingly good utilities as well - installable at the click of a mouse.

Well that's my opinion. Take it or leave it.

---

### Post by Wardje on 2010-01-03
> **mersey said:**
> I am willing to learn new ways of doing things. That's why I'm learning Ubuntu. I've been learning all through my computing career, from mainframe programming to PC and network support.

But if you and the Linux community want it to be more than a playground for computer geeks; if you want Linux to be a serious player in the desktop OS world, then you need to understand that:
1. Command line processing went out with DOS. It's been a GUI world for the last 14/15 years, since Windows 95.

2. Applications should just install smoothly with a single clickable installion routine.

When in Rome do as the Romans do - yes, but the Roman Empire collapsed 1500 years ago.  If you don't want Linux/Ubuntu to disappear into history then it needs to get its act togther.  Ubuntu 9.10 is excellent in many ways and some of the mainstream packages (Open Office, Firefox, etc.) are excellent. But a useful OS needs lots of crackingly good utilities as well - installable at the click of a mouse.

Well that's my opinion. Take it or leave it.

Main ones do install with a single clickable installation routine. You cant expect beginning projects or outdated ones to provide specific packages etc for every single architecture/distro/whatever out there and that for each build they make.
Linux is diverse, the choice lies with the end-user.

---

### Post by 3rdalbum on 2010-01-03
> **mersey said:**
> 
1. Command line processing went out with DOS. It's been a GUI world for the last 14/15 years, since Windows 95.

I've barely used Windows, but I know there are things that can only be accomplished on Windows through the MS-DOS prompt or through registry edits.

And Microsoft is working on improving its command-line as well.

> 2. Applications should just install smoothly with a single clickable installion routine.

Ubuntu can do repositories, Debian packages, and of course it can do binary installers like on Windows. If certain software developers won't make their software available like this, then that's their fault, not Ubuntu's fault.

NOT our fault.

Ubuntu even provides tools to generate Debian packages at every stage of a program's development.

Microsoft doesn't tell software developers how to package software for Windows, but of course the task there is much easier because Windows only runs on one CPU architecture.

Also may I add that the "clickable installation routine" is NOT the best method. The best method currently is the 3rd-party repository method, because it will keep the software up-to-date. Developers on Linux are moving in this direction, but it doesn't surprise me that the developer of some obscure software that he abandoned in 2007 hasn't taken advantage of this method of installation.

---

