---
title: "Mono 2.6.1"
date: 2010-02-10
forum: General Help
---

### Post by melon1234 on 2010-02-10
Hi everyone,

It seems that the Mono version in ubuntu 9.10 is 2.4. But the lastest Mono is in 2.6.1. I wonder why ubuntu provides this package so delayed. 

I have downloaded the source code of Mono 2.6.1 and gtk 2.0-2.4 and built them from ground up. However there are several I18N problems. My mono 2.6 can only run English programs. If the program contains any foriegn character, mono 2.6 will throw exception from CreateZStream. Therefore, maybe, many works should be done by ubuntu package builders before the release of mono 2.6.1 upgrade package. :(

--
ShenLei

---

### Post by Satoru-san on 2010-02-10
you need to look at the README that comes with the code it will tell you configure tags. That is the whole point of configure.

You probably need to do --with-unicode, but I dont know for sure, let me take a look at the website.

not sure if this is the same mono 
```
dev-lang/mono-2.4.2.3  USE="-minimal -moonlight -xen" 24,234 kB
``` 
Note: You will never see this!

Basically if that is the mono program you are talking about there is no utf8 or unicode --with for it.

---

### Post by melon1234 on 2010-02-10
> **Satoru-san said:**
> 
Basically if that is the mono program you are talking about there is no utf8 or unicode --with for it.

Yes. Mono documents only tell us using "mcs -codepage=xxx" to compile the source code containing unicode characters. For running mono programs, "mono xxx.exe" will refer to $LANG variable to determine the codepage for display.

---

### Post by bikeboy on 2010-02-10
Why do you need the latest version? Is it for development with things only in the newer versions?

---

### Post by melon1234 on 2010-02-10
> **bikeboy said:**
> Why do you need the latest version? Is it for development with things only in the newer versions?

Eh... I want to use the latest Mono+MonoDevelop to write C# codes. Current debugger addin (mdb) does not work correctly (Mono 2.4, MonoDev 2.0, mdb 2.0), especially "Step over" function usually gives me assembly list. I hope and assume it is fixed in latest version.

Furthermore, I'm running KeePass 2.09, but it only shows foriegn texts as hollow square in Mono 2.4. The developer of KeePass told me that it is because a bug in mono 2.4, it would be ok in mono 2.6. Therefore I built mono 2.6 from source code. However mono 2.6 even cannot start KeePass 2.09 if the GUI contains any foriegn characters. So panic...

--
ShenLei

---

### Post by bikeboy on 2010-02-10
That's fine. It's just that many people post about not having the latest versions of things when a piece of software in the repository would do them fine. Ubuntu provides a relatively stable base, without unexpected surprises until you do a full version. A lot of people aren't used to that (search Recurring Discussions for 'rolling' releases).

For development on Ubuntu, I guess you're somewhat expected to handle manual installation yourself or go with a distro that's provides significant updates *between* stable releases. Though I'm not a developer of any kind so really wouldn't know.

---

### Post by SKLP on 2010-02-13
> **melon1234 said:**
> Current debugger addin (mdb) does not work correctly (Mono 2.4, MonoDev 2.0, mdb 2.0), especially "Step over" function usually gives me assembly list. I hope and assume it is fixed in latest version. 

Yeah, I've tried Mono 2.6 + MonoDevelop 2.2 (with the new soft debugger) on openSuse and it seems to work a lot better. 
It is not strange that Mono 2.4 is default in Ubuntu karmic though, as packages are mostly updated for security issues and critical bugs. However, it does seem lucid will come with Mono 2.4 as well, which seems a bit sad :(

The directhex/monoxide ppa ([https://launchpad.net/~directhex/+archive/monoxide](https://launchpad.net/~directhex/+archive/monoxide)) provides MonoDevelop 2.2 for karmic, though. The problem is that the soft debugger requires Mono 2.6. Hopefully someone will make a nice PPA with Mono 2.6 (or later 2.8 ) and latest MonoDevelop compiled for it. It would be great or both karmic and lucid.

---

### Post by Haber_Nir on 2010-02-13
i hope too that someone will make a ppa with mono 2.6 .
maybe mono-team?

---

### Post by brianbourke75 on 2010-02-15
I to have wished upon many a falling star that ubuntu will packaged up mono/monodevelop with a functional debugger so that I can use it for my work development.  I have been trying to find a good ppa for this forever, but this far my only choice is to compile from source.  The bad part about that (kinda) is that I use a bunch of packages such as banshee which depend on mono, so this can cause me all sorts of grief.  I totally feel your pain.

---

