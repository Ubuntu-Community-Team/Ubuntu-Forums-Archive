---
title: "amazon mp3 downloader on 32bit system"
date: 2010-02-16
forum: General Help
---

### Post by ubunterooster on 2010-02-16
i can only get 64bit from amazon's site. I tried running windows version in wine but it failed to work.

edit: due to a mislabeled CD, I had errantly installed the 64bit version of Ubuntu and had not known until I was told later in this thread.

---

### Post by Swagman on 2010-02-16
I have the 32 bit version installed. It works great

[http://www.amazon.com/gp/dmusic/help/amd.html](http://www.amazon.com/gp/dmusic/help/amd.html)

It says V9:04 but it works on my 9:10 installation

---

### Post by switch10 on 2010-02-16
Ya the 32 bit version is definitely on the amazon site.  I installed it 3 days ago...  

Clink on the Ubuntu button here...  [http://www.amazon.com/gp/dmusic/help/amd.html](http://www.amazon.com/gp/dmusic/help/amd.html)

---

### Post by ubunterooster on 2010-02-16
gdebi package installer: wrong architechture 'i386'.
  ???

---

### Post by DrMelon on 2010-02-16
That means you have 64-bit I guess.

---

### Post by Dragonbite on 2010-02-16
This is good news for Linux in general, that there's enough of us to make some major sites begin trying to accomodate us!

---

### Post by oldos2er on 2010-02-16
> **ubunterooster said:**
> gdebi package installer: wrong architechture 'i386'.
  ???

Can you post the output of **uname -a** ?

---

### Post by ubunterooster on 2010-02-16
josiah@josiah-desktop:~$ uname -a
Linux josiah-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

---

### Post by Slim Odds on 2010-02-16
> **ubunterooster said:**
> i can only get 64bit from amazon's site. I tried running windows version in wine but it failed to work.

They don't even have a 64 bit version. I've asked them about it.

The 32 bit version will work fine if you use the getlibs script [http://ubuntuforums.org/showthread.php?t=474790&highlight=getlib](http://ubuntuforums.org/showthread.php?t=474790&highlight=getlib)

---

### Post by ubunterooster on 2010-02-16
[hits head on wall] how did I not know I was using 64? thankyou all; this explains much.

---

### Post by oldos2er on 2010-02-16
I use this (64-bit) software for Amazon mp3 downloads: [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

### Post by ubunterooster on 2010-02-16
the truly free downloader does make more sense, Ann, but :( I've yet to install a program from a tar.gz file. I have papers on how to do it, but neglected to read them...time for me to read up...

---

### Post by ubunterooster on 2010-02-16
josiah@josiah-desktop:~/clamz-0.2$ sudo ./configure
[sudo] password for josiah: 
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for XML_ParserCreate in -lexpat... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBCURL... configure: error: Package requirements (libcurl) were not met:

No package 'libcurl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBCURL_CFLAGS
and LIBCURL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Ummm...???

---

### Post by MinimalBin on 2010-02-16
You are missing one of it's dependencies - [libcurl3-dev]("http://packages.ubuntu.com/karmic/libcurl3-dev").

---

### Post by ubunterooster on 2010-02-16
thankyou minimalbin, that helped w/ some but terminal now says:
(partial quote)

".....checking for LIBCURL... yes
checking for libgcrypt-config... no
checking for LIBGCRYPT - version >= 1.2.0... no
configure: error: libgcrypt not found"acccording to synaptic I have version 11 of libgcryptinstalled.  

---still confused.

---

### Post by MinimalBin on 2010-02-16
You need the development libraries, too - [libgcrypt11-dev]("http://packages.ubuntu.com/karmic/libgcrypt11-dev").

---

### Post by ubunterooster on 2010-02-16
installed dev files for libgcrypt11got to make install where I got:
"josiah@josiah-desktop:~/clamz-0.2$ sudo make install
/usr/bin/install -c -d -m 755 /usr/local/bin
/usr/bin/install -c -m 755 clamz /usr/local/bin
/usr/bin/install -c -d -m 755 /usr/local/share/man/man1
/usr/bin/install -c -m 644 clamz.1 /usr/local/share/man/man1
josiah@josiah-desktop:~/clamz-0.2$ "

What now?

---

### Post by MinimalBin on 2010-02-16
Run it ( type *clamz* in Terminal ) :)

---

### Post by ubunterooster on 2010-02-16
much thanks! I could not have done it w/o you (obviously)

---

