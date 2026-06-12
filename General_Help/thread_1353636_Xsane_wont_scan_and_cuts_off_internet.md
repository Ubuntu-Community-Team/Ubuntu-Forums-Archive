---
title: "Xsane wont scan and cuts off internet"
date: 2009-12-13
forum: General Help
---

### Post by azitizz on 2009-12-13
I seem to be having a problem since installing the latest Ubuntu. I have a Canon Pixma MP510 multi printer/scanner and I cant get teh scanning to work. I cant seem to find much info regarding this printer. 
 There isnt a printer driver in the packages called mp510, only mp500 or mp520, I used mp520 and the printing seems to be working fine but no scanning. if I try and scan it gives me a device I/O error message and then a few seconds later my internet disconnects and the only way I can recconect is by rebooting the computer. 
Its a new Toshiba satellite l350. Im at a bt of a loss. Any Ideas?
Thanks

---

### Post by azitizz on 2009-12-13
I found these two help pages but as still a bit of a beginner with linux Im not sure how to make use of whats explained. I tried installing one file but said the i386 is the wrong architecture. Im not even sure what is meant by a backend.

[http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html)
[http://manpages.ubuntu.com/manpages/hardy/man5/sane-pixma.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/sane-pixma.5.html)

---

### Post by Daveth on 2009-12-13
[http://mp610.blogspot.com/](http://mp610.blogspot.com/)

for some general instruction on the Pixma range &

[http://support-asia.canon-asia.com/P/search?category=Multifunctional+Printers&series=PIXMA&model=PIXMA+MP510&menu=download&filter=0](http://support-asia.canon-asia.com/P/search?category=Multifunctional+Printers&series=PIXMA&model=PIXMA+MP510&menu=download&filter=0)

for a .rpm linux driver which you would have to use "alien" to convert to a .deb file. I have a MP610 which works really well using the advice from the first link.

---

### Post by azitizz on 2009-12-13
> **Daveth said:**
> [http://mp610.blogspot.com/](http://mp610.blogspot.com/)

for some general instruction on the Pixma range &

[http://support-asia.canon-asia.com/P/search?category=Multifunctional+Printers&series=PIXMA&model=PIXMA+MP510&menu=download&filter=0](http://support-asia.canon-asia.com/P/search?category=Multifunctional+Printers&series=PIXMA&model=PIXMA+MP510&menu=download&filter=0)

for a .rpm linux driver which you would have to use "alien" to convert to a .deb file. I have a MP610 which works really well using the advice from the first link.
Thank you, I got the rpm from canon, it seems to have converted but when I did the conversion in terminal it came out with the following:
> error: incorrect format: unknown tag
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/scangearmp-mp510
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: dpkg-gencontrol returned exit code 255
make: *** [binary-arch] Error 1
find: `scangearmp-mp510-1.00': No such file or directory

Im assuming this means this driver is not made for 64 bit users?
I should mention that there is a folder now on my desktop with a little padlock symbol on it that Im assuming is the deb file folder? When I click on it it just opens the folder and the same seems to go with the other files within it too.

---

