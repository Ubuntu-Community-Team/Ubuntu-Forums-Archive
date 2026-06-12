---
title: "[Debian] Conky 1.7.2 Without making from source"
date: 2010-03-29
forum: General Help
---

### Post by Psumi on 2010-03-29
Sorry but, I am NOT willing (nor is my IBM T41 for that matter) to make from source the new conky 1.7.2, so can someone give me a deb file for squeeze that I can install to my system to replace my current 1.7.1 conky? I really want to use lua scripts. (Specifically: [http://conky.linux-hardcore.com/?page_id=2869](http://conky.linux-hardcore.com/?page_id=2869))

Also, if someone can, can you tell me how to remove the black area behind conky without using compositing?

---

### Post by Psumi on 2010-03-29
Nevermind, I'll just use a 1.7.1 compatible script I found that looks good.

---

### Post by Zoot7 on 2010-03-29
I found the version in the Debian repos doesn't have some of the features like image rendering or wireless support by default so I just rebuilt it and added back in the features via the configure options.

That's no doubt the best way to do it, but if you're physically opposed to building from source you could try installing the conky .deb packages from the ubuntu repos.
[http://packages.ubuntu.com/lucid/conky](http://packages.ubuntu.com/lucid/conky)

---

### Post by Psumi on 2010-03-29
> **Zoot7 said:**
> I found the version in the Debian repos doesn't have some of the features like image rendering or wireless support by default so I just rebuilt it and added back in the features via the configure options.

That's no doubt the best way to do it, but if you're physically opposed to building from source you could try installing the conky .deb packages from the ubuntu repos.
[http://packages.ubuntu.com/lucid/conky](http://packages.ubuntu.com/lucid/conky)

Installing ubuntu flash from adobe website in debian caused my browsers to crash; installing it from the contrib repo in debian repos though... worked.

I'd rather not go through that again.

---

### Post by Zoot7 on 2010-03-30
Strange, i've had the opposite experience with flash, the one in the repos always gave me trouble. That was on Ubuntu anyway, never tried the Debian repo I always install it off the Adobe site.

Anyway, for the record and since you're pretty opposed to complications, building the .deb from the source is actually pretty easy.
```
apt-get build-dep conky && apt-get install devscripts dh-make
wget http://sourceforge.net/projects/conky/files/conky/1.7.2/conky-1.7.2.tar.gz/download
tar xvf conky-1.7.2.tar.gz
mv conky-1.7.2.tar.gz conky_1.7.2.orig.tar.gz && cd conky-1.7.2
dh_make -s
dpkg-buildpackage -b -j4 -D
cd .. && dpkg -i conky_1.7.2-1_i386.deb
```

---

### Post by Zoot7 on 2010-03-30
And here's one built doing just that for you. ;)

---

### Post by Psumi on 2010-03-30
> **Zoot7 said:**
> Strange, i've had the opposite experience with flash, the one in the repos always gave me trouble. That was on Ubuntu anyway, never tried the Debian repo I always install it off the Adobe site.

I installed from the adobe website, not the ubuntu repo.

I installed conky 1.7.2, I'll check it out later with the lua stuff.

---

### Post by Psumi on 2010-03-30
Well, I tried loading a lua, but it gives me this error:

```
Conky: llua_load: /home/psumi/.scripts/clock_rings-v1.1.1.lua:221: module 'cairo' not found:
	no field package.preload['cairo']
	no file './cairo.lua'
	no file '/usr/local/share/lua/5.1/cairo.lua'
	no file '/usr/local/share/lua/5.1/cairo/init.lua'
	no file '/usr/local/lib/lua/5.1/cairo.lua'
	no file '/usr/local/lib/lua/5.1/cairo/init.lua'
	no file '/usr/share/lua/5.1/cairo.lua'
	no file '/usr/share/lua/5.1/cairo/init.lua'
	no file '/usr/lib/conky/libcairo.so'
	no file './cairo.so'
	no file '/usr/local/lib/lua/5.1/cairo.so'
	no file '/usr/lib/lua/5.1/cairo.so'
	no file '/usr/local/lib/lua/5.1/loadall.so'
Conky: llua_do_call: function conky_clock_rings execution failed: attempt to call a nil value
```

Using this script: [http://conky.linux-hardcore.com/?page_id=2869](http://conky.linux-hardcore.com/?page_id=2869)

---

### Post by Sef on 2010-03-30
Moved to General Help.

---

### Post by stinkeye on 2010-03-30
> **Psumi said:**
> Sorry but, I am NOT willing (nor is my IBM T41 for that matter) to make from source the new conky 1.7.2, so can someone give me a deb file for squeeze that I can install to my system to replace my current 1.7.1 conky? I really want to use lua scripts. (Specifically: [http://conky.linux-hardcore.com/?page_id=2869](http://conky.linux-hardcore.com/?page_id=2869))

Also, if someone can, can you tell me how to remove the black area behind conky without using compositing?
If you download the conky-all package in synaptic it supports lua and cairo.

---

### Post by Psumi on 2010-03-30
> **stinkeye said:**
> If you download the conky-all package in synaptic it supports lua and cairo.

Got a 1.7.2 deb file for this as well? When I installed normal conky, I wasn't lucky enough to get lua scripts.

Debian only has conky, and no conky-all package in squeeze.

---

### Post by stinkeye on 2010-03-30
> **Psumi said:**
> Got a 1.7.2 deb file for this as well? When I installed normal conky, I wasn't lucky enough to get lua scripts.

Debian only has conky, and no conky-all package in squeeze.
Oh, I wondered what squeeze was.
There is a 1.8 conky-all deb from this ppa.
[[COLOR="DarkRed"]**_ Cesare Tirabassi PPA_**[/COLOR]]("https://launchpad.net/~norsetto/+archive/ppa/+packages")

---

### Post by Zoot7 on 2010-03-30
> **Psumi said:**
> Well, I tried loading a lua, but it gives me this error:

```
Conky: llua_load: /home/psumi/.scripts/clock_rings-v1.1.1.lua:221: module 'cairo' not found:
	no field package.preload['cairo']
	no file './cairo.lua'
	no file '/usr/local/share/lua/5.1/cairo.lua'
	no file '/usr/local/share/lua/5.1/cairo/init.lua'
	no file '/usr/local/lib/lua/5.1/cairo.lua'
	no file '/usr/local/lib/lua/5.1/cairo/init.lua'
	no file '/usr/share/lua/5.1/cairo.lua'
	no file '/usr/share/lua/5.1/cairo/init.lua'
	no file '/usr/lib/conky/libcairo.so'
	no file './cairo.so'
	no file '/usr/local/lib/lua/5.1/cairo.so'
	no file '/usr/lib/lua/5.1/cairo.so'
	no file '/usr/local/lib/lua/5.1/loadall.so'
Conky: llua_do_call: function conky_clock_rings execution failed: attempt to call a nil value
```

Using this script: [http://conky.linux-hardcore.com/?page_id=2869](http://conky.linux-hardcore.com/?page_id=2869)

Try this .deb then. I've added the lua and lua cairo configure options, which I hadn't done previously.

For the record this is done by adding the following to the **conky-1.7.2/debian/rules** file (which is produced by running **dh_make -s**), before running **dpkg-buildpackage** as I outlined before.

```
override_dh_auto_configure:
	dh_auto_configure -- --enable-own-window=yes --enable-hddtemp=yes --enable-wlan=yes --enable-alsa=yes --enable-imlib2=yes --enable-math=yes --enable-rss=yes --enable-lua=yes --enable-lua-cairo=yes
```

If you so desire other features, I suggest you add them yourself. ;)

---

### Post by Psumi on 2010-03-30
> **Zoot7 said:**
> Try this .deb then. I've added the lua and lua cairo configure options, which I hadn't done previously.

For the record this is done by adding the following to the **conky-1.7.2/debian/rules** file (which is produced by running **dh_make -s**), before running **dpkg-buildpackage** as I outlined before.

```
override_dh_auto_configure:
	dh_auto_configure -- --enable-own-window=yes --enable-hddtemp=yes --enable-wlan=yes --enable-alsa=yes --enable-imlib2=yes --enable-math=yes --enable-rss=yes --enable-lua=yes --enable-lua-cairo=yes
```

If you so desire other features, I suggest you add them yourself. ;)

I get this error with dpkg:

```
dpkg-deb: `conky_1.7.2-1_i386.deb' is not a debian format archive
dpkg: error processing conky_1.7.2-1_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 conky_1.7.2-1_i386.deb
```

> **stinkeye said:**
> Oh, I wondered what squeeze was.
There is a 1.8 conky-all deb from this ppa.
[[COLOR="DarkRed"]**_ Cesare Tirabassi PPA_**[/COLOR]]("https://launchpad.net/~norsetto/+archive/ppa/+packages")

I don't see conky-all there, just conky.

---

### Post by Zoot7 on 2010-03-30
Copy the following into a script and execute it, to build it yourself.

```

apt-get build-dep conky && apt-get install devscripts dh-make

apt-get install -y libcairo2-dev libasound2-dev libglib2.0-dev locales libxft-dev liblua5.1-0-dev libc6-i686 libxml2-dev libcurl4-gnutls-dev libimlib2-dev libiw-dev gawk libxdamage-dev

wget http://sourceforge.net/projects/conky/files/conky/1.7.2/conky-1.7.2.tar.gz/download

tar xvf conky-1.7.2.tar.gz

mv conky-1.7.2.tar.gz conky_1.7.2.orig.tar.gz && cd conky-1.7.2

dh_make -s

echo 'override_dh_auto_configure:
	dh_auto_configure -- --prefix=/usr/local --enable-own-window=yes --enable-hddtemp=yes --enable-wlan=yes --enable-alsa=yes --enable-imlib2=yes --enable-math=yes --enable-rss=yes --enable-lua=yes --enable-lua-cairo=yes' >> debian/rules

dpkg-buildpackage -b -j4 -D

cd .. 
```

Honestly if you want the 1.7.2 version on Debian you'll have to build it from source as it's not in either the Sid or Squeeze repos at the moment. There is the option of using Ubuntu's ppa but Ubuntu has a different way to packaging conky than Debian does so I wouldn't recommend it.

---

### Post by Psumi on 2010-03-30
> **Zoot7 said:**
> Copy the following into a script and execute it, to build it yourself.

```
apt-get install -y libcairo2-dev libasound2-dev libglib2.0-dev locales libxft-dev liblua5.1-0-dev libc6-i686 libxml2-dev libcurl4-gnutls-dev libimlib2-dev libiw-dev gawk libxdamage-dev

wget http://sourceforge.net/projects/conky/files/conky/1.7.2/conky-1.7.2.tar.gz/download

tar xvf conky-1.7.2.tar.gz

mv conky-1.7.2.tar.gz conky_1.7.2.orig.tar.gz && cd conky-1.7.2

dh_make -s

echo 'override_dh_auto_configure:
	dh_auto_configure -- --prefix=/usr/local --enable-own-window=yes --enable-hddtemp=yes --enable-wlan=yes --enable-alsa=yes --enable-imlib2=yes --enable-math=yes --enable-rss=yes --enable-lua=yes --enable-lua-cairo=yes' >> debian/rules

dpkg-buildpackage -b -j4 -D

cd .. 
```

Honestly if you want the 1.7.2 version on Debian you'll have to build it from source as it's not in either the Sid or Squeeze repos at the moment. There is the option of using Ubuntu's ppa but Ubuntu has a different way to packaging conky than Debian does so I wouldn't recommend it.

Gives this error:
```
./make-conky: 9: dh_make: not found
./make-conky: 12: cannot create debian/rules: Directory nonexistent
./make-conky: 14: dpkg-buildpackage: not found
```

---

### Post by Zoot7 on 2010-03-30
My apologies, I forgot to include the following at the start:
```
apt-get build-dep conky && apt-get install devscripts dh-make
```

---

### Post by Psumi on 2010-03-30
> **Zoot7 said:**
> My apologies, I forgot to include the following at the start:
```
apt-get build-dep conky && apt-get install devscripts dh-make
```

That new line gives this error:
```
E: Could not open file /var/lib/apt/lists/volatile.debian.org_debian-volatile_dists_squeeze_volatile_main_source_Sources - open (2: No such file or directory)
```

---

### Post by Zoot7 on 2010-03-30
Hmm.. what's in your **/etc/apt/sources.list** file?

Here's my own:
```
# Squeeze
deb http://ftp.ie.debian.org/debian/ squeeze main contrib non-free
deb-src http://ftp.ie.debian.org/debian/ squeeze main

deb http://security.debian.org/ squeeze/updates main contrib
deb-src http://security.debian.org/ squeeze/updates main contrib
deb http://www.debian-multimedia.org squeeze main

# Testing
#deb http://ftp.ie.debian.org/debian/ testing main contrib non-free
#deb-src http://ftp.ie.debian.org/debian/ testing main

#deb http://security.debian.org/ testing/updates main contrib
#deb-src http://security.debian.org/ testing/updates main contrib
#deb http://www.debian-multimedia.org testing main

# Unstable
#deb http://ftp.ie.debian.org/debian/ unstable main contrib non-free
deb-src http://ftp.ie.debian.org/debian/ unstable main

# Experimental
#deb http://ftp.debian.org/debian/ experimental main contrib non-free
#deb-src http://ftp.debian.org/debian/ experimental main
```

---

### Post by Psumi on 2010-03-30
> **Zoot7 said:**
> Hmm.. what's in your **/etc/apt/sources.list** file?

This is my sources.list:

```
# deb http://ftp.us.debian.org/debian/ squeeze main

deb http://ftp.us.debian.org/debian/ squeeze main contrib
deb-src http://ftp.us.debian.org/debian/ squeeze main contrib

deb http://security.debian.org/ squeeze/updates main contrib
deb-src http://security.debian.org/ squeeze/updates main contrib

deb http://volatile.debian.org/debian-volatile squeeze/volatile main contrib
deb-src http://volatile.debian.org/debian-volatile squeeze/volatile main contrib

deb http://www.debian-multimedia.org squeeze main non-free contrib
```

---

### Post by Zoot7 on 2010-03-30
> **Psumi said:**
> ```
deb http://volatile.debian.org/debian-volatile squeeze/volatile main contrib
deb-src http://volatile.debian.org/debian-volatile squeeze/volatile main contrib
```
Try commenting those guys out and running aptitude update.
For interest I tried them myself, and I get a 404 not found error. I wouldn't say you'd need the volatile repos, I never had myself anyway.

---

### Post by Psumi on 2010-03-30
> **Zoot7 said:**
> Try commenting those guys out and running aptitude update.
For interest I tried them myself, and I get a 404 not found error. I wouldn't say you'd need the volatile repos, I never had myself anyway.

After a couple minutes...

```
configure: exit 1
dh_auto_configure: ./configure --build=i486-linux-gnu --prefix=/usr --includedir=${prefix}/include --mandir=${prefix}/share/man --infodir=${prefix}/share/info --sysconfdir=/etc --localstatedir=/var --libexecdir=${prefix}/lib/conky --disable-maintainer-mode --disable-dependency-tracking --prefix=/usr/local --enable-own-window=yes --enable-hddtemp=yes --enable-wlan=yes --enable-alsa=yes --enable-imlib2=yes --enable-math=yes --enable-rss=yes --enable-lua=yes --enable-lua-cairo=yes returned exit code 1
make[1]: *** [override_dh_auto_configure] Error 9
make[1]: Leaving directory `/home/psumi/Desktop/conky-1.7.2'
make: *** [build] Error 2
dpkg-buildpackage: error: debian/rules build gave error exit status 2
```

---

### Post by Zoot7 on 2010-03-30
Ah, no need to set the prefix, open up the debian/rules file and delete the --prefix=/usr/local.

As for the error you're getting you're missing some build dependencies by the looks of things. What's the output of trying to run configure directly by doing:
```
./configure --enable-own-window=yes --enable-hddtemp=yes --enable-wlan=yes --enable-alsa=yes --enable-imlib2=yes --enable-math=yes --enable-rss=yes --enable-lua=yes --enable-lua-cairo=yes
```

Also make sure you only add the line with the above once to the debian rules file, in other words only run the echo command in the orignal list once.

---

### Post by Psumi on 2010-03-30
libtolua++5.1-dev was missing, so I installed, configured... made, made installed; but now my lua file won't load--or rather, I should say, it won't show on screen--and no errors are outputted from it.

The Clock Rings lua requires more than one cpu to function, so I edited it to only have one cpu, but it won't show on screen.

---

### Post by Zoot7 on 2010-03-30
Make install isn't the best thing to do, as you've to retain the source directory around to uninstall easily. Hence it's always better to try and build a .deb or at least use checkinstall failing that.

I don't use the lua cabability of conky myself, but I'd wager you'd have to add in the following configure option.
```
--enable-lua-imlib2=yes
```

And for the record here's the debian/rules file I used just there now to build a .deb.
```
#!/usr/bin/make -f
# -*- makefile -*-
# Sample debian/rules that uses debhelper.
# This file was originally written by Joey Hess and Craig Small.
# As a special exception, when this file is copied by dh-make into a
# dh-make output file, you may use that output file without restriction.
# This special exception was added by Craig Small in version 0.37 of dh-make.

# Uncomment this to turn on verbose mode.
#export DH_VERBOSE=1

override_dh_auto_configure:
	dh_auto_configure -- \
		--enable-own-window=yes \
		--enable-hddtemp=yes \
		--enable-wlan=yes \
		--enable-alsa=yes \
		--enable-imlib2=yes \
		--enable-math=yes \
		--enable-rss=yes \
		--enable-lua=yes \
		--enable-lua-cairo=yes \
		--enable-lua-imlib2=yes

%:
	dh  $@
```

---

### Post by Psumi on 2010-03-30
I'll just use my 1.7.1 script, thank you very much. This is very annoying. :|

leaving as unsolved as it never was fully solved. Thanks though.

---

### Post by Zoot7 on 2010-03-30
> **Psumi said:**
> This is very annoying. :|
Yeah well, if you want full control over installing newer versions of applications yourself and not to have to wait for the repos the only way around that is to compile them from source yourself. ;)

---

