---
title: "Webcam upside down in Ubuntu Natty, LD_PRELOAD doesn't help"
date: 2011-05-19
forum: General Help
---

### Post by nick_ub on 2011-05-19
I have an Asus K52F and am running Ubuntu 11.04 (64 bit). lsusb says this about the webcam:
Bus 001 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129

I downloaded the 64 bit deb file of google-chrome and saw that my webcam image was upside down in a video chat session.
I searched around for a while and found that starting chrome with the command below was supposed to fix the problem.
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so google-chrome

when I try this I get the error:
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Strangely when I try this on Firefox (4.0.1 firefox for ubuntu), it gives no error but still the webcam image is upside down.

I have no idea what is wrong here, could someone please help?

---

### Post by gradinaruvasile on 2011-05-19
> **nick_ub said:**
> I have an Asus K52F and am running Ubuntu 11.04 (64 bit). lsusb says this about the webcam:
Bus 001 Device 003: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129

I downloaded the 64 bit deb file of google-chrome and saw that my webcam image was upside down in a video chat session.
I searched around for a while and found that starting chrome with the command below was supposed to fix the problem.
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so google-chrome

when I try this I get the error:
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Strangely when I try this on Firefox (4.0.1 firefox for ubuntu), it gives no error but still the webcam image is upside down.

I have no idea what is wrong here, could someone please help?

The problem is that you want to use the paths to the compat library that are used in 32-bit machines. The error is that the .so is not found there.
So, you must find the library (it has slightly different path on 64-bit):

```

sudo updatedb
locate v4l1compat.so

```

and use that path.

---

### Post by nick_ub on 2011-05-19
I did this and it took some time to run the first command, then gave me the exact same address I was using. I put in that address and tried starting Chrome, same error.

---

### Post by no2498 on 2011-05-19
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so google-chrome
needs to be made as a bash script
i do not think it will help with the upside down cam aynway

---

### Post by nick_ub on 2011-05-24
I'm sorry for bumping but I still haven't got a fix for this.

---

### Post by no2498 on 2011-05-25
[http://www.google.com/search?client=opera&rls=en&q=webcam+upside+down+linux&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=webcam+upside+down+linux&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)

---

### Post by malucao on 2011-07-22
> **no2498 said:**
> [http://www.google.com/search?client=opera&rls=en&q=webcam+upside+down+linux&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=webcam+upside+down+linux&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)
Dude, but what about firefox and chrome.

Skype is no problem to solve, see my post [here]("http://ubuntuforums.org/showpost.php?p=11076358&postcount=16"), but how to do it with firefox (flash)? You know, like tinychat etc.

I remember that I didnt had this problem with 32bit Ubuntu, I have no idea why its a problem now with 64bit.

---

### Post by sn0m on 2011-09-15
Hi
I am running a 64 Natty and had the same problem.
I think you might need the 32 bit installed anyway.
I dealt with Hans who is doing work on this problem and posting the correspondence that I had with him.
It might be usefull.
Reg Sokol

  Hi,

Thanks for providing the requested information. I've just made
a new (test) release of v4l-utils (which includes libv4l) which
contains your laptop info in its upside down table, and as such
should fix (work around) the upside down issue for you.

You can download this new version here:
[http://people.fedoraproject.org/~jwrdegoede/v4l-utils-0.9.0-test.tar.bz2](http://people.fedoraproject.org/~jwrdegoede/v4l-utils-0.9.0-test.tar.bz2)

1. Install
==========

libv4l needs make, a working C-compiler (gcc), and libjpeg +
its header files to build. If you don't have these you need to install them
first. See your distributions documentation on how to install make and
the compiler (often called development tools / chain). For libjpeg,
you need to install the libjpeg62-dev under Debian/Ubuntu and the
libjpeg-devel package under Fedora / RHEL.

Howto install and test libv4l depends on your system. There are
different instructions for if you have a 32 bit system or a 64 bit system.
which is using multilib. A 64 bit system without multilib is the same as
a 32 bit system.

To find out what you have do:
ls -d /usr/lib64

If this command gives a "No such file or directory" error, use the
Non multilib instructions, if this command is successfull, you likely have multilib.

Note: I've received some reports that there us a /usr/lib64 directory on some 32
bit installs of Ubuntu. If you're quite sure you are running a normal (32 bit) version
of Ubuntu you likely are and you should follow the Non multilib instructions.

Ok, so you have a multilib system, to find out which (dubbed Fedora and Ubuntu
multilib, because those are the most well known examples, do):

ls -d /usr/lib32
If this command gives a "No such file or directory" error, use the Fedora multilib
instructions. If this command succeeds use the Ubuntu multilib instructions. Note
the ubuntu multilib instructions also apply to gentoo and the Fedora multilib instructions
also apply to [open]Suse.


Non multilib instructions:
--------------------------
tar xvfj v4l-utils-<version>.tar.bz2
cd v4l-utils-<version>/lib
make PREFIX=/usr
sudo make install PREFIX=/usr

Fedora Multilib instructions:
-----------------------------
Basic 64 bit install:
tar xvfj v4l-utils-<version>.tar.bz2
cd v4l-utils-<version>/lib
make PREFIX=/usr LIBDIR=/usr/lib64
sudo make install PREFIX=/usr LIBDIR=/usr/lib64

If you also want to use 32 bit apps (such as skype), you
will need to have the 32 bit libc headers installed, on Fedora
this can be done like this:
Fedora 10-: "sudo yum install glibc-devel.i386"
Fedora 11:  "sudo yum install glibc-devel.i586"
Fedora 12+: "sudo yum install glibc-devel.i686"
[open]Suse: install glibc-devel-32bit and gcc-32bit

Then do:
make clean
make PREFIX=/usr CFLAGS=-m32 LDFLAGS=-m32
sudo make install PREFIX=/usr

Ubuntu Multilib instructions:
-----------------------------
tar xvfj v4l-utils-<version>.tar.bz2
cd v4l-utils-<version>/lib
make PREFIX=/usr
sudo make install PREFIX=/usr

If you also want to use 32 bit apps (such as skype), you
will need to have the 32 bit libc headers installed, on Ubuntu
this can be done like this:
sudo apt-get install libc6-dev-i386
On gentoo this can be done like this:
sudo emerge -v app-emulation/emul-linux-x86-compat
Then do:
make clean
make PREFIX=/usr CFLAGS=-m32 LDFLAGS=-m32 LIBDIR=/usr/lib32
sudo make install PREFIX=/usr LIBDIR=/usr/lib32


2. Testing
==========
You have a chance that your webcam app use libv4l or have an appropriate
script starting it. In that case you don't have to do anything. Just run
the application. This is the most common situation with Ubuntu and Fedora
packages. If your problem remains unsolved, then your app might not use libv4l.
In that case start the application from a terminal like this:

Non multilib:
----------------
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so <your favorite webcam app>

Note on Ubuntu sometimes skype is using a wrapper script, so if skype
does not work try:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real

Fedora multilib:
--------------------
For 64 bit applications (allmost all apps):
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so <your favorite webcam app>

For 32 bit applications (you only need it for proprietary softwares, which
don't have a 64 bit version, like skype):
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

Ubuntu multilib:
--------------------
For 64 bit applications (allmost all apps):
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so skype

For 32 bit applications (you only need it for proprietary softwares, which
don't have a 64 bit version, like skype):
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

Note on Ubuntu sometimes skype is using a wrapper script, so if skype
does not work try:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real


Please let me know if this version of v4l-utils turns the image the
right way up for you.

Thanks & Regards,

Hans

---

### Post by AIM Systems on 2011-09-15
I'm having issue just starting the webcam in Natty 32bit.
My webcam works properly in Cheese (right-side-up) but in Skype, all I am allowed is voice and chat.  
Video appears a a red outline and nothing else.
I've tried the LD_PRELOAD command line to no success.

---

### Post by fat yak on 2011-11-01
This is my solution for the skype upside down webcam issue, which was worked out from this link:

techspalace.blogspot.com/2010/02/upside-down-web-cam-simple-fix.html

I have done this twice now, once on Natty and now on the new Ocelot. It worked out of the box on Natty but I have had to work out where things were on Ubuntu 11.10.

Firstly I have an Asus N10, and a suyin webcam which works fine 
on cheese but was upside down on skype.

From the above link I installed libv4l ppa but when I ran:
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
in terminal I got:
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

So I looked in the file system at /usr/lib and could find no file libv4l. So I ran a search of the file system for libv4l and found it in /usr/lib/i386-linux-gnu.
From all the solutions I have seen on the forums and searches regarding this problem, there are different solutions depending on where your particular version of linux stores the file libv4l so the instruction needs to be LD_PRELOAD= "location of your libv4l file" compat.so 

And yes having done this I now know it's obvious, but I didn't get it for ages and there are obviously people like me stumbling around in the dark trying to find the solution, judging by the number of posts I found regarding this skype issue.

So I tested it in terminal and it worked, the question was how to get it to work like that every time you use skype. You either start skype from terminal every time or you change the start up.

I went to /usr/share/applications and changed the properties of skype (need to change permissions first).

Where the box next to command had the word skype in it, I deleted skype and wrote 
bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype'

Now I haven't solved it totally because if I put the shortcut into my launcher bar, skype is still upside down but if I start skype from the icon in /usr/share/applications then the webcam is the right way up.

---

### Post by dugannaz on 2011-11-08
For skype you should use 32 bit libraries:

LD_PRELOAD="/usr/lib32/libv4l/v4l1compat.so /usr/lib32/libv4lconvert.so.0" skype

would work.

---

### Post by bertbiker on 2011-12-25
The following thing worked on my ASUS u35jc with Oneiric 64 bit. It may probably work on other ASUS laptops with the same issue:

Make sure you have skype 64 bits installed from the skype website, not the 32 bits version from the repository.

Make a script:

/usr/bin/skype-webcam-fixed

Then paste the following:

> 
#!/bin/sh
export LIBV4LCONTROL_FLAGS=3 
LD_PRELOAD="/usr/lib32/libv4l/v4l1compat.so /usr/lib3/libv4lconvert.so.0" skype


Make it executable:
> 
chmod +x /usr/bin/skype-webcam-fixed


And use skype-webcam-fixed to run skype. I adapted it from a post by Flupke:
[http://ubuntuforums.org/showthread.php?t=1569380](http://ubuntuforums.org/showthread.php?t=1569380)

---

### Post by sn0m on 2011-12-26
Thanks, it worked for me with Asus 64 X53E
one thing, how do you edit skype launcher in menu, so when i click skype it lauches with skype-webcamfixed-starter. Thanks Sokol

---

### Post by Halfling Rogue on 2012-01-08
> **sn0m said:**
> Hi
I am running a 64 Natty and had the same problem.
I think you might need the 32 bit installed anyway.
I dealt with Hans who is doing work on this problem and posting the correspondence that I had with him.
It might be usefull.
Reg Sokol

  Hi,

Thanks for providing the requested information. I've just made
a new (test) release of v4l-utils (which includes libv4l) which
contains your laptop info in its upside down table, and as such
should fix (work around) the upside down issue for you.

You can download this new version here:
[http://people.fedoraproject.org/~jwrdegoede/v4l-utils-0.9.0-test.tar.bz2](http://people.fedoraproject.org/~jwrdegoede/v4l-utils-0.9.0-test.tar.bz2)

Tried this version myself on a 64 bit Fujitsu Lifebook LH531 and got the following errors when I tried to compile:

```
cc -Wp,-MMD,"libv4lconvert.d",-MQ,"libv4lconvert.o",-MP -c -I../include -fvisibility=hidden -fPIC -DLIBDIR=\"/usr/lib\" -DLIBSUBDIR=\"libv4l\" -I../../include -I../../lib/include -D_GNU_SOURCE -DV4L_UTILS_VERSION='""' -g -O1 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -o libv4lconvert.o libv4lconvert.c
In file included from libv4lconvert.c:26:
libv4lconvert-priv.h:25:21: warning: jpeglib.h: No such file or directory
In file included from libv4lconvert.c:26:
libv4lconvert-priv.h:53: error: field ‘jerr’ has incomplete type
libv4lconvert-priv.h:56: error: field ‘cinfo’ has incomplete type
libv4lconvert.c: In function ‘v4lconvert_destroy’:
libv4lconvert.c:198: warning: implicit declaration of function ‘jpeg_destroy_decompress’
make[1]: *** [libv4lconvert.o] Error 1
make[1]: Leaving directory `/home/[username]/v4l-utils-0.9.0-test/lib/libv4lconvert'
make: *** [all] Error 2

```

The original version installed fine but didn't work; the picture is still upside-down in all programs (all of which are 64-bit, including Skype).

---

### Post by Halfling Rogue on 2012-01-08
> **sn0m said:**
> Thanks, it worked for me with Asus 64 X53E
one thing, how do you edit skype launcher in menu, so when i click skype it lauches with skype-webcamfixed-starter. Thanks Sokol

Go to System -> Preferences -> Main Menu, find Skype, highlight it, and click the Properties button on the right. In Command, where it says "skype", change it to "skype-webcamfixed-starter skype" or however the loader functions.

---

