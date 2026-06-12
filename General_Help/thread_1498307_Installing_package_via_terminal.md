---
title: "Installing package via terminal"
date: 2010-05-31
forum: General Help
---

### Post by WeaponsTheyFear on 2010-05-31
Hello all,
I am in need of some help building an application.  The app is mupen64plus.  I installed from the software center, but it's an old version and certain things don't work that now do in the newer version.

My problem is I cannot build this thing, following the directions.  I have extracted the source and tried to make install, make all, etc and I get 'no rule to make target' error.

If anyone has any experience, I would really appreciate the help.  Thanks guys, and gals.

---

### Post by mikewhatever on 2010-05-31
From what I can see, the tar.gz packages for Linux on the home page are not source code but binaries. Is that what you downloaded? The page also have the source code package. Hope you can clarify that.

---

### Post by WeaponsTheyFear on 2010-05-31
> **mikewhatever said:**
> From what I can see, the tar.gz packages for Linux on the home page are not source code but binaries. Is that what you downloaded? The page also have the source code package. Hope you can clarify that.

I've downloaded both but can't seem to figure out how to work either.  I tried to build the source package, and this is where the errors comes from.  The binary I just tried cd to the folder and calling the binary file.  I think it expects me to supply a file to open but I can't figure out how I am supposed to type this in (no examples provided).  I tried supplying binary file name - /media/Multimedia/path-to-file.z64 but it still wouldn't work.

The thing I am after is the cheats not working in the available 1.5 version from the Software Center.  I tried them, and then collected a Big Key, but now I can't use the key, can't use the cheats, and worst of all I can't go back and recollect the big key, so I am just stuck (in the Shadow Temple, I don't wanna go back through the entire game again, and certainly not the Water Temple).  Just trying to breeze through the game for screenshots of important events (for a fan site I have).

Thanks for your response, hope this helps clarify a bit better.

---

### Post by mikewhatever on 2010-05-31
To install the binaries, save the extracted folder to the desktop, then
cd ~/Desktop/mupen64plus-bundle-linux32-1.99.3

and run the installation script
./install.sh

Whatever errors you get, post them here.
As for cheats keys and temples, I've no idea what you are talking about.:P Just trying to help you install the thing.

---

### Post by WeaponsTheyFear on 2010-05-31
> **mikewhatever said:**
> To install the binaries, save the extracted folder to the desktop, then
cd ~/Desktop/mupen64plus-bundle-linux32-1.99.3

and run the installation script
./install.sh

Whatever errors you get, post them here.
As for cheats keys and temples, I've no idea what you are talking about.:P Just trying to help you install the thing.

Thanks for a quick reply.  I ran the install.sh, but can't find anything after that point.  I can run ./mupen64plus through terminal, but it mentions something about supplying the rom path, which I can't figure out how to tell it this.

It says in the docs it installs at usr/local/bin, but that directory is empty for me.  Another location it says is .local/share/mupen64plus, but there is nothing in there but source files (I think it's source) and some folders for saves and screenshots.

Wish the latest version would just be pushed to the Software Center, or I could add some repository to install :/

---

### Post by mikewhatever on 2010-05-31
Just tried that, and here's the output:
```
./install.sh
Installing Mupen64Plus Binary Bundle to /usr/local
install: cannot create regular file `/usr/local/lib/libmupen64plus.so.2.0.0': Permission denied

```

That means you have to run the scrip as superuser - **sudo ./install.sh**.
Once again, it you get any errors, post them here.

---

### Post by WeaponsTheyFear on 2010-05-31
> **mikewhatever said:**
> Just tried that, and here's the output:
```
./install.sh
Installing Mupen64Plus Binary Bundle to /usr/local
install: cannot create regular file `/usr/local/lib/libmupen64plus.so.2.0.0': Permission denied

```

That means you have to run the scrip as superuser - **sudo ./install.sh**.
Once again, it you get any errors, post them here.

I did run sudo, and haven't been able to find the files they say in usr/bin.  I have gotten a bit further in trying to build, but upon running make it tells me there are no SDL libraries?  I tried to fix running apt-get install build-essentials but doesn't seem to help.

---

### Post by Serpher on 2010-05-31
Perhaps you'll find [this](http://code.google.com/p/mupen64plus/wiki/CompilingFromHg) useful. I hope somebody develops easier emulator software for Ubuntu.

---

### Post by mikewhatever on 2010-05-31
Well, the source code package has build.sh and install.sh scripts inside. Have you tried them?

Edit: ...and here is the compiling wiki page. Note the requirements section.
[http://code.google.com/p/mupen64plus/wiki/CompilingFromHg](http://code.google.com/p/mupen64plus/wiki/CompilingFromHg)
The sdl libraries you mentioned are a requirement, the package is probably libsdl-dev.

---

### Post by WeaponsTheyFear on 2010-05-31
Thanks guys, will give them both a try.  Yes, I have tried the build.sh and install.sh files.  The build pretty much creating a directory of files, which is how I've been able to continue.  There is a dir it tells you to go into and run make all, but when I do I get the SDL libraries error.

Will try the links and see if it helps.

Thanks again for your help.

Edit - I've reached the end of everything building/making.  After make all, and make install, everything seems successful with no error messages.  However, now I cannot figure out how to run mupen.  Trying mupen64plus through terminal tells me there is no such command and to run apt-get install mupen64plus.  It lists off the dirs everything was installed to but I still cannot find any binary for it.

---

### Post by Bjornar93 on 2010-06-12
Hi!
I have tried alot of getting Mupen64Plus 1.99.3 to work, and finally - it does :p

The first thing I did was to run
```
sudo apt-get install libsdl-ttf2.0-0 libsdl-ttf2.0-dev
```.
After that did I download "mupen64plus-bundle-linux32-1.99.3.tar.gz"
Unpack the folder that is inside and run the folder in terminal, and write ```
sudo ./install.sh
```.
And now we are coming to a special part that did surprise me, this version does not have a GUI! :?
After searching a lot on Google I found [this little post]("http://forums.opensuse.org/get-help-here/games/437992-mupen64plus-opensuse.html#post2159303") over at the OpenSuSE board.
To finally start playing you have to press for example ```
mupen64plus /home/bjornar/Dokumenter/test/Zelda.z64
``` (it will not accept roms with spaces in the name :confused: )
To get better known with the commands in Mupen64Plus, just press
```
mupen64plus --help
```

---

