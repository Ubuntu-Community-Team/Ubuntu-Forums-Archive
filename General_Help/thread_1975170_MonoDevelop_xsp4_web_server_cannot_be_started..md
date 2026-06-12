---
title: "MonoDevelop xsp4 web server cannot be started."
date: 2012-05-07
forum: General Help
---

### Post by Lazy Vulpes on 2012-05-07
Hi, I hope some kind soul will be able to help me with this problem of mine. :)

First of all, I'd like to add that I've just installed Ubuntu 12.04 last night, so I'm quite the newbie.. 

I'm having some difficulty running a .net web page in MonoDevelop, this is the error I get.

```
Could not launch web server. The "xsp4" web server cannot be started. Please ensure that it is installed.
```The error tells me to insure that xsp4 is  installed, I haven't even been able to do this. I'm assuming that it  comes with MonoDevelop?

I've done some extensive googeling, but to no avail. Basically I read about two solutions. Use the Mono/.net 4.0 framework (which I am), and install xsp4 (Which resulted in an error telling me that is was unable to locate package)

I've tried a few commands but none of them worked. Perhaps I'm doing it wrong?

I've tried to search the keyword "xsp4" in the Ubuntu Software Center and two links show up mono-xsp4-base and mono-xsp4. When I click them I get this message: "There isn&#8217;t a software package called &#8220;mono-xsp4&#8221; in your current software sources."

If no solution is possible to reach for whatever reason, perhaps an alternative is available? (besides uploading the project to an actual server)

btw the target server which my web project should run on in the end is windows based.


Edit: In case it matter, I'm using the AMD64 desktop distribution.

---

### Post by directhex on 2012-05-07
> **Lazy Vulpes said:**
> Hi, I hope some kind soul will be able to help me with this problem of mine. :)

First of all, I'd like to add that I've just installed Ubuntu 12.04 last night, so I'm quite the newbie.. 

I'm having some difficulty running a .net web page in MonoDevelop, this is the error I get.

```
Could not launch web server. The "xsp4" web server cannot be started. Please ensure that it is installed.
```The error tells me to insure that xsp4 is  installed, I haven't even been able to do this. I'm assuming that it  comes with MonoDevelop?

No, it comes in the [mono-xsp4](apt:mono-xsp4) package.

> I've done some extensive googeling, but to no avail. Basically I read about two solutions. Use the Mono/.net 4.0 framework (which I am), and install xsp4 (Which resulted in an error telling me that is was unable to locate package)

The name of a program, and the name of a package which contains that program, often do not match

> I've tried a few commands but none of them worked. Perhaps I'm doing it wrong?

I've tried to search the keyword "xsp4" in the Ubuntu Software Center and two links show up mono-xsp4-base and mono-xsp4. When I click them I get this message: "There isn’t a software package called “mono-xsp4” in your current software sources."

Sounds like a Software Center bug? xsp4 should work fine and install fine.

---

### Post by Lazy Vulpes on 2012-05-07
SOLVED!

I downloaded the package(s) from [http://www.ubuntuupdates.org](http://www.ubuntuupdates.org)
I then installed the package manually using "sudo dpkg -i package-name.deb" (This command needs to be run from the location in which the .deb file is located of course (You might need to restart))

The link you provided btw resulted in an error telling me that the package was not found..

---

### Post by directhex on 2012-05-07
> **Lazy Vulpes said:**
> The link you provided btw resulted in an error telling me that the package was not found..

Sounds like you don't have all your software sources enabled, i.e. "main" but not "universe" in the Software Sources menu of Software Centre

---

### Post by Lazy Vulpes on 2012-05-08
You're right, the software center does claim that I don't have the universe source enable, however under "Edit > Software Sources" I *have* enabled all the boxes (main, restricted, universe & multiverse)

I tried to install "Shutter" just now and it said that Universe Source wasn't enabled, so I clicked the enable button. It started a process, but didn't seem to go anywhere. I then restarted the Software center and apparently it have processed it just fine and shutter is now installed.. (I think it might have been because I had the edit Software sources window open that it didn't seem to process, idk)

---

