---
title: "configure: error:"
date: 2011-07-28
forum: General Help
---

### Post by Jhf4473 on 2011-07-28
using = 10.04 LTS - the Lucid Lynx
trying to ./configure gweled 0.9.1
get error  librsvg-2.0 is required to compile gweled
tried to install  librsvg-2.0 but version installed now is newer than 2.0

any help would be appreciated

---

### Post by Theredbaron1834 on 2011-07-29
First off, enless you have a really slow computer, and hope compiling yourself will give you a little bit of an edge and let you play it, you can get it [here]("https://launchpad.net/%7Ednax88/+archive/gweled"). The earliest is for 10.10, [here]("https://launchpad.net/%7Ednax88/+archive/gweled/+build/2606328/+files/gweled_0.9.1%2Br86%7Emaverick1_i386.deb") is the deb for that. It might work, it might not. Depends on what it depends on. :)

On to the compiling stuff:
When compiling programs, and it says it needs XXX, that doesn't mean install just XXX, it needs XXX-dev to work. The -dev programs add the files need for developers, and yourself, to compile programs.

So, in this case, I believe you need the program librsvg2-dev installed. So either from term "sudo apt-get install librsvg2-dev" or search for it in synaptic and click install.

And if you already knew that, and done it, then the only thing left to do is go [here]("http://librsvg.sourceforge.net/"), and make your own from the source. 



I hope this helps. I am not really that good with nix myself, I just looked through the forums and saw this with no 0 posts, and thought you should get at least a little help, even if just from me, :)

---

### Post by Jhf4473 on 2011-07-29
Thanks I got it installed now

---

### Post by Theredbaron1834 on 2011-07-29
Cool, glad you got it working.

---

