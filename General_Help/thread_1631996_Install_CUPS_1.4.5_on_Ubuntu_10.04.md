---
title: "Install CUPS 1.4.5 on Ubuntu 10.04?"
date: 2010-11-27
forum: General Help
---

### Post by lightnb on 2010-11-27
Hi,

I have a server running Ubuntu 10.04 with CUPS version 1.4.3 - the cups version that installs via the package manager. The latest stable release of CUPS is 1.4.5, but an apt-get update/upgrade won't update it to the latest version.

Is there any way to install cups 1.4.4 or 1.4.5 using apt-get? Or do I have to remove the package version and compile from source?

---

### Post by Malta paul on 2010-11-27
Cups 1.4.3 is the default version for Ubuntu 10.04.
But you can download the cups 1.4.5-source.tar.bz2 file and it will install OK. 
First Extract, ./configure, make & then sudo make install. Will do the trick.

---

### Post by lightnb on 2010-11-27
Thanks,

A few questions:

Do I need any arguments for ./configure?

And which packages are "covered" by the CUPS Source?I'm assuming that I need to remove the package version before installing the source version.

"apt-get remove cups" says it will remove "cups cups-driver-gutenprint cupsys foomatic-db foomatic-db-engine ghostscript-cups". Is it safe to remove them all? (ie. will they exist again after installing from source)?

---

### Post by dino99 on 2010-11-27
no more recent cups (natty=1.4.4-7) (you can get it by temporary changing the /etc/apt/sources.list from maverick to natty, then updating and installing the cups packages, and reverting then to maverick and updating again to stay tuned with maverick)

[https://launchpad.net/~maverick-bleed/+archive/ppa](https://launchpad.net/~maverick-bleed/+archive/ppa)

---

### Post by Malta paul on 2010-11-27
Just download the cups file from:[http://www.cups.org/software.php](http://www.cups.org/software.php)

Extract using R/H mouse click the file > extract.
Using the Terminal:
CD to the extracted file.
Type> ./configure (thats all, this will run and check for any dependencys)
Then> Make to compile the file.
Then> sudo make install (to install, don't worry about removing the old version)   
Thats it, :D

---

### Post by lightnb on 2010-11-27
I installed 1.4.5 from source per your instructions, but the configuration tool ([http://localhost:631](http://localhost:631)) still shows version 1.4.3?

EDIT: Never mind- I needed to do a "service cups stop" and "service cups start". Looks like it's working now. Thank you very much!

---

### Post by lightnb on 2010-11-28
I'm reopening this thread because I'm still having some issues with the new version of CUPS. It prints text files fine, but refuses to print png images.

For example "lpr -P MyPrinter SomeImage.png" adds to the print cue correctly, but its status is "stopped. unable to open image file for printing!".

Maybe I needed some ./configure option to get .png support? Or am I missing a dependency?

---

### Post by Malta paul on 2010-11-28
Sorry to hear you are having problems.
My best advice is to revert back to the default for Ubuntu 10.04 which is Cups 1.4.3. As this should work OK for you.

---

### Post by lightnb on 2010-11-28
We're upgrading because 1.4.3 has a bug which causes a 10 second spooling delay between adding a file to the cue and when it actually begins to print. This bug was not present in Ubuntu 8.04, and we're hoping it's been addressed in a later release of CUPS.

I think the issue with printing images may be related to the absence of certain header files. I've added the package "libpng12-dev" which I believe contains the png headers, and the configure script is recognising it.

I'm trying to add the other image format headers, but I'm having a hard time figuring out which packages they're in. Specifically, I'm looking for jpeglib.h and tiff.h.

EDIT: I think it's "libjpeg62-dev", "libtiff4-dev" and "libtiffxx0c2" that I want. Gotta love the intuitive package names!

---

### Post by Malta paul on 2010-11-28
I have a delay like you say on one of my printers.
Just a though, it might be worth giving our friend Dino99's (#4) version a try and see if cups 1.4.4-7 works for you?

---

### Post by lightnb on 2010-11-28
The good news is I got 1.4.5 installed and working with png support. The bad news is the delay is still present.

So... It's a either a bug in CUPS that hasn't been fixed yet, or an issue with the way Ubuntu handles printing in the newer versions. I'm not sure 1.4.4-7 would be any different?

I need a way to see what's causing the delay... like a really verbose log. There's nothing exciting in /var/log/cups/access_log or error_log.

Downgrading to 8.04 seems silly. But for our application, we need fast printing. :/

---

### Post by bazzer on 2010-12-01
I'm chasing the exact same issue at the moment! I thought it was because I use printing 'classes' and only have one printer from a complete class attached at any one time - hot swap printers with different IP addresses. I've identified a couple of lines of code in backend/ipp.c I am about to change and see if it helps:
```
      if (getenv("CLASS") != NULL)
      {
       /*
        * If the CLASS environment variable is set, the job was submitted
	* to a class and not to a specific queue.  In this case, we want
	* to abort immediately so that the job can be requeued on the next
	* available printer in the class.
	*/

        _cupsLangPuts(stderr,
	              _("INFO: Unable to contact printer, queuing on next "
			"printer in class...\n"));

        if (tmpfilename[0])
	  unlink(tmpfilename);

       /*
        * Sleep 5 seconds to keep the job from requeuing too rapidly...
	*/

	sleep(5);

        return (CUPS_BACKEND_FAILED);
```
Obviously I'm going to get rid of the **sleep 5**

---

### Post by bazzer on 2010-12-02
ok, well if anyone is interested, I've had a good result with my setup, removing the 'Sleep 5' from backend/socket.c. The ipp.c file I thought I'd be after must be called under different configuration conditions.

My setup is a class with 2 printers in, different IP addresses and only one is connected at a time. Invariably, CUPS decides it wants to use the one that's not connected all the time, and waits 5 seconds (more) before queuing the job on another printer.

---

