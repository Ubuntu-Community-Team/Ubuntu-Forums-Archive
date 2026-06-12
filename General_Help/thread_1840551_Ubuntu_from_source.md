---
title: "Ubuntu from source"
date: 2011-09-07
forum: General Help
---

### Post by math4tots on 2011-09-07
Is there a nice tutorial on how to build Ubuntu from source?

I know Ubuntu Customization Kit provides some customization abilities, but I felt building from source would be fun to learn and is something I feel I should learn how to do at some point.

When I Google "Ubuntu from source" most of the hits return how to build various applications from source, but not Ubuntu itself.

There are also a lot of tutorials on how to make your own distro, and stuff like that, but I was hoping along the lines of something specific to Ubuntu and reasonably recent so that I don't have to worry about different flavors of commands and how to do things, at least the first time I build an OS from source.

---

### Post by MG&amp;TL on 2011-09-07
You could extract the .iso. That has some interesting source code you could probably tweak. The problem is re-packing it again.

---

### Post by haqking on 2011-09-07
> **math4tots said:**
> Is there a nice tutorial on how to build Ubuntu from source?

I know Ubuntu Customization Kit provides some customization abilities, but I felt building from source would be fun to learn and is something I feel I should learn how to do at some point.

When I Google "Ubuntu from source" most of the hits return how to build various applications from source, but not Ubuntu itself.

There are also a lot of tutorials on how to make your own distro, and stuff like that, but I was hoping along the lines of something specific to Ubuntu and reasonably recent so that I don't have to worry about different flavors of commands and how to do things, at least the first time I build an OS from source.


here is the source for ubuntu though 10.04 [http://old-releases.ubuntu.com/releases/releases/10.04/release/source/](http://old-releases.ubuntu.com/releases/releases/10.04/release/source/)

---

### Post by WorMzy on 2011-09-07
It's not Ubuntu, but I recommend [Linux from Scratch]("http://www.linuxfromscratch.org/").

---

### Post by oldos2er on 2011-09-08
> **math4tots said:**
> When I Google "Ubuntu from source" most of the hits return how to build various applications from source, but not Ubuntu itself.

That's because the source is distributed by package, including the kernel source. [S]As far as I know the "Ubuntu" source code is not available as a single package or download.[/S]

Edit: It appears the source for 10.04 *is* available as a single file download.

---

### Post by haqking on 2011-09-08
> **oldos2er said:**
> That's because the source is distributed by package, including the kernel source. As far as I know the "Ubuntu" source code is not available as a single package or download.


My link contains the Ubuntu source

---

### Post by oldos2er on 2011-09-08
Interesting, I didn't know that existed. Wonder why it's 10.04 only?

---

### Post by haqking on 2011-09-08
> **oldos2er said:**
> Interesting, I didn't know that existed. Wonder why it's 10.04 only?

its not, just change the version in the URL such as following

[http://old-releases.ubuntu.com/releases/releases/9.04/release/source/](http://old-releases.ubuntu.com/releases/releases/9.04/release/source/)

not all version though

[http://old-releases.ubuntu.com/releases/releases/](http://old-releases.ubuntu.com/releases/releases/)

---

### Post by math4tots on 2011-09-08
By a tutorial for "building from source" I meant, a tutorial that went through putting Ubuntu together from various parts. So I guess I wasn't being exactly accurate, because as far as I'm concerned, bringing together various binaries/libraries to "build the OS" might have been what I was looking for also.

Linux from Scratch is awesome, but I don't exactly want to start from scratch.

I imagine that there would be a "makefile" equivalent that packages Ubuntu together right? I was hoping there would be some information on how to use something like that, and in particular, use it to build Ubuntu from the components from, for instance, [http://old-releases.ubuntu.com/relea...elease/source/]("http://old-releases.ubuntu.com/releases/releases/10.04/release/source/")

How painful would it be for the developers if Ubuntu builds were done manually "From Scratch" every new build?

---

### Post by haqking on 2011-09-08
> **math4tots said:**
> By a tutorial for "building from source" I meant, a tutorial that went through putting Ubuntu together from various parts. So I guess I wasn't being exactly accurate, because as far as I'm concerned, bringing together various binaries/libraries to "build the OS" might have been what I was looking for also.

Linux from Scratch is awesome, but I don't exactly want to start from scratch.

I imagine that there would be a "makefile" equivalent that packages Ubuntu together right? I was hoping there would be some information on how to use something like that.

How painful would it be for the developers if Ubuntu builds were done manually "From Scratch" every new build?


but packages change and get updated and replaced all the time.

a makefile to compile ubuntu ?

using the links i posted you can download the source and then compile yourself.

as for packages thats what they are in any distro, packages, added at will as needed

---

### Post by sisco311 on 2011-09-08
> **math4tots said:**
> 
I imagine that there would be a "makefile" equivalent that packages Ubuntu together right? 

Nope, that's the job of the installer.

Not sure for what are you looking for... maybe debootstrap?

---

