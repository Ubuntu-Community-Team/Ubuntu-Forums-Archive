---
title: "Does anyone use Java Comm API?"
date: 2010-03-26
forum: General Help
---

### Post by Colo2 on 2010-03-26
Hey

[COLOR="Red"]Please can someone move this if it's in the wrong catagory.[/COLOR]

I need to install Java Comm API on my ubuntu machine:

[http://java.sun.com/products/javacomm/](http://java.sun.com/products/javacomm/)

However, there is no download link, and all of the mirror links on other sites seem to be broken.

I was wondering. Is it available somehow for linux users? Is it in the ubuntu repo? Otherwise how can I get hold of it?

Thanks :)

- Tom

---

### Post by doas777 on 2010-03-26
it looks like the javax.comm is part of the SE jdk 1.4.2 already. that is a very old jdk however, so you may have problems with client runtimes if you try to deploy an app based on it now. there is likely an upgraded version of the lib in 1.6.x. 

we are about to part ways with one vendor, because they steadfastly refuse to update their product to run with a 1.5x+ jdk, or provide vista support. My department is well behind all the others in my org in terms of desktop replacement, because we can't get any more xp and this peice of crap software won't work on anything even remotely modern. now the powersupply fans (and thus the power supplies) are going bad in lots.

---

### Post by Colo2 on 2010-03-26
Hey, SE jdk 1.4.2 is discontinued :( So I guess I'm out of luck?

---

### Post by doas777 on 2010-03-26
> **Colo2 said:**
> Hey, SE jdk 1.4.2 is discontinued :( So I guess I'm out of luck?
see if it is included in 1.6x. I would assume it is there, but 1.5 deprecated a lot of stuff from java 2/3/4. it was a milestone release that added a lot of kewl features and data structures, but that places a compatibility barrier between the two versions.

---

### Post by sikakraa on 2010-03-26
I remember reading few years ago that Sun's Java Comm API was deprecated for all except Solaris. They unofficially suggested in some blog to use Rxtx([http://www.rxtx.org/](http://www.rxtx.org/)) instead. Worked for me. Might work for you. :)

---

### Post by kalohr on 2010-07-06
rxtx works fine for serial comm

I personally could'nt make it work for parallel ports

---

