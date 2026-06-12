---
title: "windows 7 wifi with ndiswrapper?"
date: 2010-09-24
forum: General Help
---

### Post by jaya28inside on 2010-09-24
I just realized after reading the ebook 
entitled, Ubuntu Linux for Dummies 2007, published by John Wiley & Sons.

I have some question after read PART II : Chapter 7 : Using Windows Device Driver; ndiswrapper to enable the Windows Driver inside the Linux.

Is this ndiswrapper support taking the Windows 7 Drivers as well?
Since I open up google and found some statements that saying ndiswrapper intended to take Windows XP drivers only.

Here's the source:
> [http://wiki.debian.org/NdisWrapper](http://wiki.debian.org/NdisWrapper)

They're saying;
> NDISwrapper uses Windows XP driver files - which may have been supplied with your hardware - to operate your device. This driver wrapper is only available for use on the x86 and x86-64 architectures (Debian i386 and AMD64 ports respectively).

is there anyone have tried taking windows 7 driver and 
put it on linux using ndiswrapper? 

Due to the difference of the OS mentioned, what's the possibility outcome anyway(error, and etc) ?

---

### Post by jaya28inside on 2010-10-07
well to continue this story.
I collect the Drivers for the Windows 7 into a single directory. Including its *.inf file, 

here they're (the **Broadcom 802.11n Wireless Network Adapter'**s Driver files):

```

[I]bcm43xx.cat
bcm43xx64.cat
bcmwl5.inf
bcmwl5.sys[/I]

```

If i'm not mistaken ndiswrapper-utility need the *.inf files as the main thing to be put on the command line.
Next, all of them are copied into **/etc/ndiswrapper/** directory

And then, I execute;

```

$> sudo ndiswrapper -i /etc/ndiswrapper/bcmwl5.inf

```

BING BONG!
it said "INSTALLING..."

and thus, I wanted to check it out. Whether it really succeess or not?

i try to execute;

```

$> sudo ndiswrapper -l

```

and I Got this message... duh!

> 
bcm43xx64.cat : invalid driver!
bcm43xx.cat : invalid driver!
bcmwl5 : driver installed
bcmwl5.inf : invalid driver!
bcmwl5.sys : invalid driver!


any other suggestion?
or is there something i forgot? 


I really need some tips for this. Confused mode : ON. :confused:

---

