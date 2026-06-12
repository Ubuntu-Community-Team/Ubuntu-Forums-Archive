---
title: "Canon Pixma ip1500"
date: 2010-05-30
forum: General Help
---

### Post by D0M1N8 on 2010-05-30
I know it has been asked many times before, but how can I set up my Canon ip1500 in ubuntu Lucid? I've seen lots of solutions, but none that worked for me. I don't know much about CUPS, either.

Printing is the one thing that I still have to do in windoze, and I hate having to switch over just to print the sheet music for Hey Jude!

Any help would be much appreciated. Thanks!

---

### Post by D0M1N8 on 2010-06-01
Any ideas?

---

### Post by frankb_1602 on 2010-06-02
Try the following (everything is quoted from [https://wiki.ubuntu.com/CanonPixmaIP1500](https://wiki.ubuntu.com/CanonPixmaIP1500), only step 6a is my recommendation):

1. download the driver from Canon: 
```
wget http://software.canon-europe.com/files/soft22415/software/iP1500Linux.tar.gz
```2. Extract it: 
```
tar -xzf iP1500Linux.tar.gz
```3. Install alien:  
```
sudo apt-get install alien
```4. Convert rpm to  deb using alien (I got some error messages here, but don't worry about them)
```
cd iP1500
sudo alien *i386.rpm
```5. Install the deb files: ```
sudo dpkg -i *.deb
```6. Create  symlinks: 
```
cd /usr/lib
sudo ln -s libtiff.so.4 libtiff.so.3
sudo ln -s libxml2.so.2 libxml.so.1
```The ubuntu wiki shows another line here: "sudo ln -s libpng12.so.0 libpng.so.2". I believe that this one is not necessary or even wrong, as the libpng file is now (i.e. in Ubuntu 10.04) located in /lib instead of /usr/lib.

So, I'd suggest the following to do:

6a. Go to the /lib directory and create the last symlink there:
```
cd /lib
[FONT=DejaVu Sans]sudo ln -s libpng12.so.0 libpng.so.2[/FONT]
```Now, go ahead as described in the ubuntu wiki - or go straight to step 8 there:

8. Turn the printer on, and restart cups: 
```
sudo /etc/init.d/cups restart
```or if you get an "command not found" try: 

```
sudo /etc/init.d/cupsys restart
```9. Add the  printer to cups: For gnome just  use System>>Administration>>Printing and click add printer.  Canon Pixma iP1500 should be  available. 

----

BTW Step 6a is not my own creation - I found it following the instructions of the German [Ubuntuusers wiki]("http://wiki.ubuntuusers.de/Canon-Drucker?highlight=ip90%20canon#Links-setzen").

---

### Post by D0M1N8 on 2010-06-02
> **frankb_1602 said:**
> 4. Convert rpm to  deb using alien (I got some error messages here, but don't worry about them)
```
cd iP1500
sudo alien *i386.rpm

```


when I run this step, I get ```
error: incorrect format: unknown tag
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: Compatibility levels before 5 are deprecated.
dh_installdirs
dh_installdirs: Compatibility levels before 5 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 5 are deprecated.
dh_installchangelogs
dh_installchangelogs: Compatibility levels before 5 are deprecated.
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/bjfilter-common
dh_compress
dh_compress: Compatibility levels before 5 are deprecated.
dh_makeshlibs
dh_makeshlibs: Compatibility levels before 5 are deprecated.
dh_installdeb
dh_installdeb: Compatibility levels before 5 are deprecated.
dh_shlibdeps
dh_shlibdeps: Compatibility levels before 5 are deprecated.
dpkg-shlibdeps: warning: debian/bjfilter-common/usr/local/bin/bjcups contains an unresolvable reference to symbol poptGetOptArg: it's probably a plugin.
dpkg-shlibdeps: warning: 3 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: dependency on libpopt.so.0 could be avoided if "debian/bjfilter-common/usr/local/bin/bjcups debian/bjfilter-common/usr/lib/cups/filter/pstocanonbj" were not uselessly linked against it (they use none of its symbols).
dh_gencontrol
dh_gencontrol: Compatibility levels before 5 are deprecated.
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol -ldebian/changelog -Tdebian/bjfilter-common.substvars -Pdebian/bjfilter-common returned exit code 255
make: *** [binary-arch] Error 9
find: `bjfilter-common-2.50': No such file or directory


```

Then

```

d0m1n8@ubuntu:~/iP1500$ sudo dpkg -i *.deb
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

```
Any idea why?

---

### Post by D0M1N8 on 2010-06-03
Solved! Installed demo version of turboprint and ripped the ppd file. I would recommend this to anyone. $30 is ridiculous. (For the record, they are located in the /usr/share/turboprint/ppd directory)

Thanks to [http://ubuntuforums.org/archive/index.php/t-18991.html](http://ubuntuforums.org/archive/index.php/t-18991.html) for the idea.

---

### Post by frankb_1602 on 2010-06-06
Hm, I do not think that this approach is correct or legal. 

However, just for the record: *.deb files for Pixma iP1500 can also be found here: [http://linux.cergynux.net/canon/](http://linux.cergynux.net/canon/)

You will need all three files (bjfilter-common_2.50-3_i386.deb, bjfilter-pixmaip1500-lprng_2.50-3_i386.deb and bjfilter-pixmaip1500_2.50-3_i386.deb). 

And you may probably need the following files from the repository:

- libxml2 
- libglade2-0 
- libpng3
- libtiff4 

And... I have no idea if it is possible to use the a.m. drivers on a 64 bit system. ;)

---

