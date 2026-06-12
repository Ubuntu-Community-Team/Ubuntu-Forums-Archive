---
title: "dpkg fails, maybe a problem with the status file, or mono."
date: 2011-09-13
forum: General Help
---

### Post by kooia on 2011-09-13
Whenever I try to install or remove software from the command line, I now get an error.  

```
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 63266 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 63267 package 'virtualbox-3.1':
 error in Config-Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
(Reading database ... 366893 files and directories currently installed.)

```It does install most things, but it still returns this error.  From what I've read, it sounds like this is a problem with the status file.  However, I think it's a problem with mono.  I don't know how that would affect dpkg, but I've tried to install/remove a lot of software, and I've always gotten an error about mono.  I think this is because I was messing around with mono, and probably deleted or modified something I shouldn't have.  

An error when I tried to run banshee:

```
The assembly mscorlib.dll was not found or could not be loaded.
It should have been installed in the `/usr/lib/mono/2.0/mscorlib.dll' directory.

```I can't get any sound either.

Any ideas?  Should I post the whole error message when I try to install something?

---

### Post by fdrake on 2011-09-13
try this and see if it resolves the problem:
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-old2
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status 

```

or you can also try to delete the /var/lib/dpkg/status from the beginning . dpkg will use staus-old since it is the only known left status file.

---

### Post by kooia on 2011-09-13
Tried it, but I still get the same errors.

Thought this might be useful:

```
Errors were encountered while processing:
 libnunit2.4-cil
 libnunit-cil-dev
 libmono-cil-dev
 libwebkit1.1-cil
 mono-devel
 monodoc-browser
 monodoc-manual

```And all the errors: [http://kooia.info/kooia/KiconEditInstallationErrors.txt](http://kooia.info/kooia/KiconEditInstallationErrors.txt)

Also - the sound is working - my speakers got unplugged.

---

### Post by fdrake on 2011-09-13
it looks like you have dependencies problems, try ;

```

sudo aptitude install linux-image-$(uname -r) linux-headers-2.6.32-34-386 linux-headers-2.6.32-34-generic linux-image build-essential dpkg-dev patch
sudo apt-get -f update && sudo apt-get -f upgrade

```

---

### Post by kooia on 2011-09-13
Tried that - it doesn't work.

Here's the error messages.

[http://kooia.info/kooia/headersinstallation.txt](http://kooia.info/kooia/headersinstallation.txt)
[http://kooia.info/kooia/updateupgrade.txt](http://kooia.info/kooia/updateupgrade.txt)

---

### Post by kooia on 2011-09-13
So I figured out that there's actually two problems here:
One is that there were underscores in the dpkg status file, in the virtualbox section.[http://ubuntuforums.org/showthread.php?t=1591201](http://ubuntuforums.org/showthread.php?t=1591201)

The other is that it can't finish installing  libnunit2.4-cil,  libnunit-cil-dev, libmono-cil-dev, libwebkit1.1-cil, mono-devel, monodoc-browser, and monodoc-manual.  What should I do - it won't let me do anything until it finishes installing those packages.  I can't reinstall them.  I think I have to restore mono to what it was before I started fiddling with it - how would I do that?

---

### Post by directhex on 2011-09-15
> **kooia said:**
> So I figured out that there's actually two problems here:
One is that there were underscores in the dpkg status file, in the virtualbox section.[http://ubuntuforums.org/showthread.php?t=1591201](http://ubuntuforums.org/showthread.php?t=1591201)

The other is that it can't finish installing  libnunit2.4-cil,  libnunit-cil-dev, libmono-cil-dev, libwebkit1.1-cil, mono-devel, monodoc-browser, and monodoc-manual.  What should I do - it won't let me do anything until it finishes installing those packages.  I can't reinstall them.  I think I have to restore mono to what it was before I started fiddling with it - how would I do that?

Remove them via dpkg --purge. Critically, I suspect you've corrupted your mscorlib, which is causing Mono to break when it tries to handle library installation. Purge the lot.Then install again anew.

---

### Post by fdrake on 2011-09-15
if purge fails try:
```

sudo aptitude clean && sudo aptitude autoclean
sudo aptitude -f update && sudo aptitude -f upgrade

```
i am out of ideas....

---

