---
title: "Has anyone installed SPICE (remote desktop protocol) on Ubuntu"
date: 2010-06-17
forum: General Help
---

### Post by bmullan on 2010-06-17
I'm trying to build the server side SPICE application as documented at:

[Installing SPICE on Ubuntu by Comp Sci Labs at Clarson Univ]("http://docs.cslabs.clarkson.edu/wiki/SPICE")

[INDENT]*SPICE is a protocol that allows for high-quality virtual machine access using VDI over a network. It could be used as a communication layer between thin clients and their associated virtualized operating systems, or it could be used as it is in the COSI lab for normal machines to have quick access to a variety of different operating systems, or in any other configuration where it is better for a virtual machine to be running remotely.*[/INDENT]

I get to the following instructions:

[INDENT][I][I]# install qcairo
wget [http://www.spice-space.org/download/qcairo-1.8.7.1-git74d6b5.tar.bz2](http://www.spice-space.org/download/qcairo-1.8.7.1-git74d6b5.tar.bz2)
tar xf qcairo-1.8.7.1-git74d6b5.tar.bz2
cd qcairo-1.8.7.1-git74d6b5/
./autogen.sh --disable-xlib --disable-ps --disable-pdf --disable-svg --includedir=/usr/include --libdir=/usr/lib64
make
sudo make install[/I][/I][/INDENT]

But it fails to build because it can't find the pixman Library files
I did a google search and found only 2 references to this error:

[I][INDENT]Pixman 0.18.0 is installed in /usr/local/lib (which I believe is the usual location).

Configure for Cairo 1.8.10 can't find it:

checking for cairo's image surface backend feature... checking for pixman... no no checking whether cairo's image surface backend feature could be enabled... no (requires pixman-1 >= 0.12.0 [http://cairographics.org/releases/](http://cairographics.org/releases/)) configure: error: mandatory image surface backend feature could not be enabled 

I've tried setting environment variable pixman_LIBS=/usr/local/lib but wihtout any luck.

Any idea what is going wrong? Is it possible for me to see where is cairo's configure looking for pixman? Search paths or something like that?

==Answer==

/usr/local/lib is not the usual place. 64-bit libraries are under lib64 of some sort. Use file to verify the libraries under there.

Also, /usr/local is not on most of the paths, so you may need to use $LIBDIR as well.[/INDENT][/I]

I have tried moving files etc but the build still fails.   This may not be enough for someone to go on but if anyone has installed SPICE "server" on Ubuntu 10.04 I'd appreciate your sharing how you got it built successfully.

Brian

---

