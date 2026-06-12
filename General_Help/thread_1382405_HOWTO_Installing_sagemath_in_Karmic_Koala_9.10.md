---
title: "HOWTO: Installing sagemath in Karmic Koala 9.10"
date: 2010-01-15
forum: General Help
---

### Post by process91 on 2010-01-15
I created this how to because the official instructions from sagemath are close to correct, but slightly off due to different package names in Karmic 9.10. If you don't care about customizing your installation, and just want the full installation of sage installed automatically please feel free to download the script attached to this post. Details regarding this script are in the last paragraph at the bottom.

**Initial Conditions**
 Fairly fresh install of Ubuntu 9.10 desktop edition. I had installed some other unrelated programs, but all my instructions should work from a freshly installed (and updated) state as well.

**Why not use the Binary?**
 It didn't work. I received a cryptic error which didn't seem promising, and since building from scratch didn't look too difficult I decided to give it a shot. If you can use the binary, by all means please do. It's considerably easier than compiling, and certainly takes less time as well.

**Dependencies**
 Sage needs gcc, make, m4, perl, ranlib, tar, ssh-keygen, and (optionally) latex (see the site listed in references for a complete list). Instead of running through particulars, the following commands will set up everything you need.

Base Requirements
```
sudo apt-get install build-essential m4
```

Recommended Additional Software
```
sudo apt-get install readline-common libreadline-dev
```

LaTeX (Listed as optional, but I highly recommend it)
```
sudo apt-get install texlive xpdf evince
```

Tcl/Tk Libraries (optional)
```
sudo apt-get install tk8.5-dev
```

All in one shot
```
sudo apt-get install build-essential m4 readline-common libreadline-dev texlive xpdf evince tk8.5-dev
```

**Download Source**
 Download the source TAR from [http://www.sagemath.org/download-source.html](http://www.sagemath.org/download-source.html). At the time of this writing, the newest version was 4.3, and you can download this version from a world mirror by using
```
wget http://mirror.switch.ch/mirror/sagemath/src/sage-4.3.tar
```

**Build and Compile from Source**
 Extract the downloaded tar file.
```
tar xvf sage-x.y.z.tar
```
At this point you should move the newly created sage-x.y.z directory to its final location. In theory you should be able to move the directory around even after it's built, but some links for the dependencies are hardcoded and so it's best to make the move now (if at all). I chose to put mine in /opt, you can do so as well if you'd like:
```
sudo mv sage-x-y-z /opt/
```

Wherever you chose to keep the program, it's time to build the source. Move into the directory, and run make. It's not necessary to run make as root.
```
cd sage-x-y-z
make
```

This part should take some time, on my machine it took >20min.

**Finishing Up**
 We're in the home stretch now, and technically you can actually run sage just the way it is. The last two steps just make sage easier to run from anywhere on the server. First, add a link to sage in the local binaries folder (here I use the opt location I installed to, you should point it wherever you installed it to)
```
sudo ln -s /opt/sage/sage /usr/local/bin/sage
```

And now edit the sage file itself (using vi or nano) to correspond to the sage root.
```
vi /opt/sage/sage
```
(Change the line which reads *SAGE_ROOT="....."* to read *SAGE_ROOT="/opt/sage/"*, or wherever you installed sage to.

**Finished**
 Now you should be able to run sagemath by typing in 'sage', and run sage notebook by typing in 'sage -n'.

**The Script**
 I made a small script which performs this installation automatically. Please note that the script installs all optional components, downloads sage 4.3, and puts sage into the /opt/sage directory. The script is attached to this post, simply download it and make it executable, then run it in a terminal.

**References**
 [http://www.sagemath.org/doc/installation/source.html](http://www.sagemath.org/doc/installation/source.html)

---

### Post by soelk on 2010-02-25
Good guide. Worked well for me. 

It took about four hours to compile on my old A64, although I was doing a lot of other stuff at the same time.

---

### Post by atentik on 2010-04-21
This works for me. Thanks

---

### Post by asadniazi on 2010-04-22
The Sagemath package (4.3.4) I had compiled on my Ubuntu 9.04 and 9.10 installation fails for any algebra based problem, seemingly due to a problem with the version of Maxima that comes with Ubuntu 9.10 (and even 9.04). After reading on this forum and elsewhere, I managed to fix the issue:

I had installed Sage in '/usr/local/share/sage', and made links to the program in 'usr/local/bin/'. I first deleted the contents of '/usr/local/share/sage/' as well as /usr/local/bin/maxima' to remove the installed sage. Then I installed maxima 5.21 from the following ppa 'https://launchpad.net/~blahota/+archive/wxmaxima/'. After that I downloaded the source of Sage from [www.sagemeth.org](www.sagemeth.org) (version 4.3.5), unpacked the contents (as sudo), to '/usr/local/share/sage/' and then recompiled sage by running 'make'. It works.

---

### Post by atentik on 2010-04-25
Have you ever been able to get the vtk and mayavi to work with sage? I am not successful in my efforts.

---

### Post by zeevb on 2010-05-08
Very good guide. Used it to build and install sagemath 4.4.1 on Ubuntu Lucid. The only missing part was to install fortran (otherwise the build failed) using the following command ```
sudo aptitude install gfortran
```

---

### Post by Innigo on 2010-08-26
I followed this and got it compiled OK but then it gave an import error re. SciPy as soon as I tried to plot somethig. 

I'd installed all the non-optional dependencies using Synaptic to the Ubuntu repo, except Maxima for which I added the repo for the PPA given above. I upacked sage-4.5.2 under /opt and the make took a couple of hours and reported a successful build after I manually pointed it at the gfortran I'd got as described in the README. I set the SAGE_ROOT variable and made a link in /usr/local/bin as instructed in the finishing up section. 

After I got the error and checked the Sage FAQ, I tried sage: import _tkinter and got an error so I rebuilt sage's version of python with 'sage -f python-2.6.4.p9' and after much scolling of stuff up the screen, 'sage: import _tkinter' worked.

Can I do something similar to point it at SciPy? From what I've read SciPy is supposed to come as a bundled package within Sage. Maybe I've been a bit optimistic using the latest version of sage or is it a PATH thing I can fix easily?

Alternatively there's a pre-built binary for Ubuntu10.04 on the sage download page. Would this be likely to work with Karmic9.10?

Anyone?

---

### Post by process91 on 2010-08-26
You certainly could try installing the compiled binary from Sage's site, if it's going to fail it will fail quickly. Chances are it will, I know there are some differences in the package names which Sage uses from 9.10 to 10.04. Any reason not to upgrade to 10.04?

---

### Post by Edward G on 2010-12-21
> Alternatively there's a pre-built binary for Ubuntu10.04 on the sage download page. Would this be likely to work with Karmic9.10?

Anyone?

It didn't work for me.

---

