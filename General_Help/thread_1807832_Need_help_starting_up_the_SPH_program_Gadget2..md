---
title: "Need help starting up the SPH program Gadget2."
date: 2011-07-19
forum: General Help
---

### Post by MutantJohn on 2011-07-19
Hello Everybody,

I'm a complete noob to this whole Linux thing. Ironically enough, when I first learned IDL I was using Linux and didn't even realize it lol but I digress. So basically, for my research I need to use Gadget2. The only problem is, I have no idea how to "install" it, I guess. I've looked in the user help guide but I think it was written more or less for those that actually know what they're doing, hence why my research professor doubted my abilities to get it running.

So, I've downloaded all that .tar.gz files and gotten rid of the .gz part and now I have a bunch of .tar files (Gadget2.0.7, gsl-1.15, fftw-3.2.2, openmpi-1.4.3 and hdf5-1.8.7-freebsd-static). I've also done the whole tar -xvf thing to just extract the files and now I have 5 folders. I looked in their help guides and I think I might've done something right 'cause now I have some lib folders and some etc and some share ones. 

I think my message passing interface is operational because every time I shut down my computer now there's this weird screen about some pretty harmless looking stuff like my computer is openly passing messages so I think I'm fine there. But how do I make sure all the other stuff is good? I've tried installing and configuring (maybe not in that order, mind you) but I'm still kinda lost.

Is there anything I need to tell you guys to get some help started or perhaps I'm in the wrong place? References would be much appreciated, I'm still just a little baby Ubuntu 11.04 user.

---

### Post by MutantJohn on 2011-07-21
So, I think I might just need help figuring out how to use the message passing interface or whatever it's called so that way Gadget can communicate with all its other whatnot. Any ideas?

---

### Post by MutantJohn on 2011-07-21
Okay, so I saw that I got more views which is awesome. I'm definitely going to keep this updated until my grad student mentor comes back into town lol. Anyway, I checked out the documentation that comes with the open mpi and I found I could configure what I think were called f77 progams? I'm sorry but I don't recall exactly, the command to compile was something like mpif77 my_code_here.f

And when I tried to do that it told me it couldn't because I was missing the gfortran library and when I tried to get that running I got even more confused. So, does anyone wanna teach me how to fortran?

---

### Post by MutantJohn on 2011-07-23
This feels more like a blog than it does anything else. So I shall continue to write me experiences. Basically, I googled the proper text permutation of gadget2 installation guide. Who would of thought, right? And I found this website: [http://astrobites.com/2011/04/02/installing-and-running-gadget-2/](http://astrobites.com/2011/04/02/installing-and-running-gadget-2/)

I started following and I got up to the fftw part because every time I type in: ./configure --enable-mpi --enable-type-prefix --enable-float

I get told that fftw can't find my mpi library which I so configured and installed. So I have a new question for you all, how do I make fftw find my mpi library? I'm certain I have it and installed it properly. If not then how does one test to make sure that their open message passing interface is functioning properly?

And as a side note, am I the only astrophysics person here? Ooh, is that one of the forums here? I think I need to go check now lol.

---

### Post by MutantJohn on 2011-07-24
And now let's finish this small little blurb I've been writing for the past couple of days. Or is it a week now? Eh, who knows. But either way, I found in Synaptic Device Manager a bunch of mpicc stuff so I actually installed everything and I just ran my first simulation not too long ago.

While writing this I sort of felt like I was being ignored mostly because if there are veterans here they'd like to see if the baby deer struggling to stand can actually stand on its own feet. Well, I can. And I love Ubuntu as well. Wine handles WC3 and battle.net better than Windows 7 ever could and plus, have you guys felt how stable this operating system is? It's epic! And I can even monitor my CPU and GPU temps at a whim and everything. Basically, life ain't so bad.

---

