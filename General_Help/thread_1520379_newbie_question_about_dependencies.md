---
title: "newbie question about dependencies"
date: 2010-06-29
forum: General Help
---

### Post by matteosistisette on 2010-06-29
Hi,

I am new to Ubuntu.

When I install a package using Synaptic Package Manager (package available from some repository), if the package has dependencies that are not satisfied, Synaptic automatically offers to install all the needed packages, so I do "OK" and all the needed packages are installed.

However, if I download a package directly from the internet (no repository, just download the package file), then when I double-click on it, it opens a Package Installer, and if all dependencies are satisfied the package is installed; but if some dependency is not satisfied it will only warn me and won't give me the option to automatically install the needed packages. I have to manually go and install the needed packages with Synaptic untill all the dependencies are satisfied. That can be quite boring if there are a few unsatisfied dependencies.

Isn't there a way to install a package file _and_ have all the missing packages (which _are_ correctly detected) automatically installed as well, just like Synaptic does?

Thank you in advance
m.

---

### Post by Brandon Williams on 2010-06-29
There's no simple way to do this that I can think of, but it's easy enough to get the list of dependencies for a package and install them. Here's one method:
```
DEPS=$(dpkg-deb -f pkg.deb Depends | sed 's/,//g; s/([^)]*)//g;')
sudo apt-get $DEPS
```

The first list extracts (and cleans up) a list of dependencies from pkg.deb, and the second line installs all the dependencies.

---

### Post by matteosistisette on 2010-06-29
Great, thank you!

---

### Post by dino99 on 2010-06-29
sudo dpkg -S yourpackage

---

### Post by matteosistisette on 2010-06-29
> **Brandon Williams said:**
> There's no simple way to do this that I can think of, but it's easy enough to get the list of dependencies for a package and install them. Here's one method:
```
DEPS=$(dpkg-deb -f pkg.deb Depends | sed 's/,//g; s/([^)]*)//g;')
sudo apt-get $DEPS
```The first list extracts (and cleans up) a list of dependencies from pkg.deb, and the second line installs all the dependencies.

Hi, I get a strange error when doing the second:

```
teo@XXX:~$ sudo apt-get $DEPS
[sudo] password for teo: 
E: Invalid operation xterm

```

'xterm' is the first dependency in the list, but I don't know what 'E' is.

The output from *dpkg-deb [...] | sed* is:
```
teo@XXX:~$ dpkg-deb -f mypackage.deb Depends | sed 's/,//g; s/([^)]*)//g;'
xterm | x-terminal-emulator ttf-bitstream-vera x-ttcidfont-conf tcllib  freeglut3 libasound2  libbz2-1.0 libc6  libc6  libdv4 libfftw3-3 libflite1 libfreetype6  libftgl2  libgcc1  libgl1-mesa-glx | libgl1 libglib2.0-0  libglu1-mesa | libglu1 libgsl0ldbl  libimlib2 libjack0  libmagick++1 libmagickcore1 libmp3lame0  libmpeg3-1  libogg0  libpng12-0  libquicktime1  libspeex1  libstdc++6  libtheora0  libvorbis0a  libvorbisenc2  libvorbisfile3  libx11-6 libxext6 libxv1 libxxf86vm1 tcl8.4  tk8.4  zlib1g 

```

By the way, if the list contains package that are already installed they won't be reinstalled, will they??

---

### Post by matteosistisette on 2010-06-29
> **dino99 said:**
> sudo dpkg -S yourpackage

Man says -S is for searching a package owning a file. Doesn't seem related at all. Or am I missing something??

---

### Post by philinux on 2010-06-29
I think Brandon means to put those two commands into a bash script.

---

### Post by matteosistisette on 2010-06-29
> **philinux said:**
> I think Brandon means to put those two commands into a bash script.

Same result

---

### Post by nothingspecial on 2010-06-29
Install the original deb with

```
sudo dpkg -i package.deb
```

then type
```

sudo apt-get install -f
```

As long as the dependencies are in the ubuntu repos that should do it.

---

### Post by matteosistisette on 2010-06-29
> **nothingspecial said:**
> Install the original deb with

```
sudo dpkg -i package.deb
```then type
```

sudo apt-get install -f
```As long as the dependencies are in the ubuntu repos that should do it.

(guessing the "original deb" is the one i want to install in the first place, which depends on missing packages)

I did that. Result:
*sudo apt-get install -f* actually installed some packages, and it REMOVED the 'original package'.

I tried again installing the 'original one' with the Package Installer, but it still complains about the dependencies

---

### Post by nothingspecial on 2010-06-29
```
sudo apt-get install xterm  x-terminal-emulator ttf-bitstream-vera x-ttcidfont-conf tcllib  freeglut3 libasound2  libbz2-1.0 libc6  libc6  libdv4 libfftw3-3 libflite1 libfreetype6  libftgl2  libgcc1  libgl1-mesa-glx | libgl1 libglib2.0-0  libglu1-mesa  libglu1 libgsl0ldbl  libimlib2 libjack0  libmagick++1 libmagickcore1 libmp3lame0  libmpeg3-1  libogg0  libpng12-0  libquicktime1  libspeex1  libstdc++6  libtheora0  libvorbis0a  libvorbisenc2  libvorbisfile3  libx11-6 libxext6 libxv1 libxxf86vm1 tcl8.4  tk8.4  zlib1g 

```Then install the deb

---

### Post by matteosistisette on 2010-06-29
Ok it seems it is because the 'original' package depends on (at least) one package that is not in any repository. I'll have to fix that by hand.

---

### Post by Brandon Williams on 2010-06-29
> **matteosistisette said:**
> Hi, I get a strange error when doing the second:

```
teo@XXX:~$ sudo apt-get $DEPS
[sudo] password for teo: 
E: Invalid operation xterm

```

Sorry, I screwed that up. The second command should be:
```
sudo apt-get install $DEPS
```

Of course, as you note, it won't work if there's a package in the dependency list that isn't in the standard repos, but at least you'll be notified of which ones you'll have to find elsewhere.

---

### Post by matteosistisette on 2010-06-29
> **Brandon Williams said:**
> Sorry, I screwed that up. The second command should be:
```
sudo apt-get install $DEPS
```


Oh sorry i didn't figure it out myself, I am a total newbie :)

I have succesfully installed the software (and learned a little bit about packages). Thank you very much for your help.

---

