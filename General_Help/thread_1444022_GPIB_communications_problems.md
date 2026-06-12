---
title: "GPIB communications problems"
date: 2010-03-31
forum: General Help
---

### Post by kentpend on 2010-03-31
Here's the scenario: I need to create a test setup in my lab that will run power supplies for an indefinite amount of time.  It could be anywhere from days to months at a time.  This rules out matlab, as its memory leaks won't let it run that long, and LabView is too buggy (at least in my experience.  and it has memory leaks as well).  So I need a way to program GPIB (since that is the interface these power supplies have)

So far, PyVISA seems to be the most likely way to be able to do this.  However, I keep receiving the following error:

```
pyvisa.visa_exceptions.VisaIOError: VI_ERROR_LIBRARY_NFOUND: A code library required by VISA could not be located or loaded.

```

Searching around, this apparently means that I'm missing GPIB drivers, but I'm not.  linux-gpib installed, and the card appears in /dev.
That being said, every now and then the gpib interfaces simply disappear from /dev,and the only way I can get them back is to reinstall linux-gpib.
Any ideas why this might happen, or how I can fix it?

Also, has anybody else succeeded in working with GPIB outside of LabView and Matlab, and if so how?  I'm also open to other options, having made no progress on this after over a week.

The two real requirements is that I need programming interface to be scpi commands, and I would prefer to code in python or C/C++.

Thanks in advance for any help or advice.

---

### Post by Calash on 2010-03-31
NI has some linux support pages, though they do not list and Debian based as supported.

[http://www.ni.com/linux/support.htm](http://www.ni.com/linux/support.htm)

From there you get a link to 

[http://linux-gpib.sourceforge.net/](http://linux-gpib.sourceforge.net/)

They have source as well as Debian packages on the Sourceforge page.

We run a ton of GPIBs for Mass Spectrometers, but not of them are on Linux so I am not much help outside of the links.

---

### Post by kentpend on 2010-04-01
I've been looking through both of those already.  Unfortunately, it was even with that I'm running into these problems.

Actually, installing NI-488 broke PyVISA completely,and now python simply aborts when I try to load the module.

I'm currently working through a couple different, albeit similar tutorials for this on the NI support forums ([http://decibel.ni.com/content/docs/DOC-6742](http://decibel.ni.com/content/docs/DOC-6742) and [http://decibel.ni.com/content/docs/DOC-4140]("http://decibel.ni.com/content/docs/DOC-4140") , but am still encountering problems, such as the scripts in the NI packages not behaving correctly.

---

### Post by Chronon on 2010-04-01
From [http://pyvisa.sourceforge.net/vpp43.html#connecting-to-the-visa-shared-object](http://pyvisa.sourceforge.net/vpp43.html#connecting-to-the-visa-shared-object)
> [SIZE="4"]Connecting to the VISA shared object
[/SIZE]
vpp43 tries to find the VISA library for itself. On Windows, this is not a big problem. visa32.dll must be in your PATH. If it isn't, move it there or expand your PATH.

However, on Linux you may need to give the explicit path to the shared object file. You do so by saying for example:

import pyvisa.vpp43 as vpp43
vpp43.visa_library.load_library("/path/to/my/libvisa.so.7")

By default, vpp43 looks for the library in /usr/local/vxipnp/linux/bin/libvisa.so.7. Please pay attention to the fact that the library must have been successfully loaded before any VISA call is made.

Alternatively, you can tell PyVISA so by creating a file ~/.pyvisarc. This has the format of an INI file. For example, if the library is at /usr/lib/libvisa.so.7, the file .pyvisarc must contain the following:

[Paths]

VISA library: /usr/lib/libvisa.so.7

Please note that [Paths] is treated case-sensitively.

You can define a site-wide configuration file at /usr/share/pyvisa/.pyvisarc. (It may also be /usr/local/... depending on the location of your Python.)


Is this possibly the problem you were having initially?  

In second reading, probably not.  Maybe this leads somewhere new, though.

---

### Post by wannabegeek on 2011-01-11
hi....did you have any luck ?

I am trying to use GPIB with 10.04 on a lab computer and found this: 
[http://decibel.ni.com/content/docs/DOC-13584](http://decibel.ni.com/content/docs/DOC-13584)

haven't tried it yet....it seems that the kernel has to be 2.6.x.x for the linux-gpib to work...
please correct me if I am wrong.

wbg

---

### Post by kentpend on 2011-01-12
Sorry... the only place I got was a lot of headaches and a sleep shortage.  I eventually gave up and used a windows machine sitting around the lab.  I couldn't do the other things with it I had hoped to, but I at least got the core of my system working.

---

