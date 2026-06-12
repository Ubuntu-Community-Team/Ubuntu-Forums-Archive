---
title: "Why isn't this driver install working (sudo code)?"
date: 2012-08-25
forum: General Help
---

### Post by 777funk on 2012-08-25
I have a [soundcard]("http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html") that I'd like to use and I've been trying to install it and being a new Ubuntu user, I get about half way through this in the Terminal and it stops cooperating with me... See the link (soundcard hyperlink) but basically what I have here:
[COLOR=Black]
[/COLOR] [SIZE=3]**[COLOR=Black]I do the following and it works:[/COLOR]**[/SIZE]
> [LEFT][COLOR=#000000][COLOR=#000000][COLOR=#0000bb]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]get install subversion[/COLOR][/COLOR][/COLOR][/LEFT]
 
 [LEFT][COLOR=#000000][COLOR=#000000][COLOR=#0000bb]svn co https[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#ff8000]//line6linux.svn.sourceforge.net/svnroot/line6linux
[/COLOR][/COLOR][/COLOR][/LEFT]
 
 Change to the directory
  [LEFT][COLOR=#000000][COLOR=#000000][COLOR=#0000bb]cd line6linux[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]driver[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]trunk
[/COLOR][/COLOR][/COLOR][/LEFT]
 
 Time to build from the source but first make sure you have the latest build and headers
  [LEFT][COLOR=#000000][COLOR=#000000][COLOR=#0000bb]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]get install build[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]essential
[/COLOR][/COLOR][/COLOR][/LEFT]
 
  [LEFT][COLOR=#000000][COLOR=#000000][COLOR=#0000bb]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]get install linux[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000bb]headers[/COLOR][/COLOR][/COLOR][/LEFT]

[SIZE=3]**Then after this point it says must specify file to install. Not sure how to do this or what it means.**[/SIZE]

[SIZE=3]**Then the following just gives errors or says not recognized etc.**[/SIZE]> [LEFT][COLOR=#000000][COLOR=#000000][COLOR=#0000bb]make
[/COLOR][/COLOR][/COLOR][/LEFT]
 
  [COLOR=#000000][COLOR=#0000bb]sudo make install[/COLOR][/COLOR]This is in Ubuntu 12.04.1 LTS

Thanks for any guidance!

Another thing, semi related... cut, copy, paste??? seems like it's different from program to program. I was in the terminal and hit ctrl-C and then ctrl-shift-V in Firefox and it won't paste. But in terminal it will paste... I'm confused.

---

### Post by Cheesemill on 2012-08-26
No need to install this driver manually, those are old instructions you are using.

The driver is already included in the latest versions of Ubuntu.

---

### Post by 777funk on 2012-08-26
> **Cheesemill said:**
> No need to install this driver manually, those are old instructions you are using.

The driver is already included in the latest versions of Ubuntu.

Thanks, maybe some of this is but SVN seemed to install. Also, I'd be sure that Ubuntu doesn't come with this stuff:

[LEFT][COLOR=#000000][COLOR=#000000][COLOR=#0000bb]svn co https[/COLOR][COLOR=#007700]:[/COLOR][COLOR=#ff8000]//line6linux.svn.sourceforge.net/svnroot/line6linux
[/COLOR][/COLOR][/COLOR][/LEFT]
 
 Change to the directory
  [LEFT][COLOR=#000000][COLOR=#000000][COLOR=#0000bb]cd line6linux[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]driver[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]trunk



[/COLOR][/COLOR][/COLOR][/LEFT]
 

and for some reason after those steps it's not playing along any more (see above steps in post 1). Seems to fly up until that point though.


Here's the error(s) I get after Make:
nick@NickUbuntu:~/line6linux/driver/trunk$ make
./set_revision.sh
./set_revision.sh: 9: test: [https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:](https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:) unexpected operator
make -C /lib/modules/3.2.0-29-generic-pae/build CONFIG_LINE6_USB=m SUBDIRS=/home/nick/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  CC [M]  /home/nick/line6linux/driver/trunk/audio.o
/home/nick/line6linux/driver/trunk/audio.c: In function &#8216;line6_init_audio&#8217;:
/home/nick/line6linux/driver/trunk/audio.c:30:57: error: &#8216;THIS_MODULE&#8217; undeclared (first use in this function)
/home/nick/line6linux/driver/trunk/audio.c:30:57: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/nick/line6linux/driver/trunk/audio.o] Error 1
make[1]: *** [_module_/home/nick/line6linux/driver/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
make: *** [default] Error 2

---

### Post by Cheesemill on 2012-08-26
Can you post exactly what you are typing into the terminal and the exact output please, we can't help without it.

Also the command to copy is CTRL+ALT+c
CTRL-c is used to terminate a running process.

---

### Post by Cheesemill on 2012-08-26
> **777funk said:**
> Also, I'd be sure that Ubuntu doesn't come with this stuff:

Did you actually try using it before you decided that you need to manually install the drivers?

If you read the comments on the page you are using it is quite clear that Ubuntu 10.10 and later already have these drivers built in.

---

### Post by z3nhakr on 2012-08-26
copy and paste works the same as it would any where else with the exception of terminal because ctrl+c is used to kill a script. instead, copy is ctrl+shift+c and paste is ctrl+shift+v

---

### Post by 777funk on 2012-08-26
> **Cheesemill said:**
> Did you actually try using it before you decided that you need to manually install the drivers?

If you read the comments on the page you are using it is quite clear that Ubuntu 10.10 and later already have these drivers built in.


Yeah no go on the Line6 audio unit  before the install.  In that install it actually downloads something that someone put together (note the link to download in that install).

---

### Post by 777funk on 2012-08-26
here is everything I could copy from Terminal:

```
A    line6linux/driver/tags/v0.6.2/config.h
A    line6linux/driver/tags/v0.6.2/restart_alsa.sh
A    line6linux/driver/tags/v0.6.2/control.txt
A    line6linux/driver/tags/v0.6.2/dumprequest.c
A    line6linux/driver/tags/v0.6.2/control.c
A    line6linux/driver/tags/v0.6.2/update_version.pl
A    line6linux/driver/tags/v0.6.2/apps
A    line6linux/driver/tags/v0.6.2/apps/resample.sh
A    line6linux/driver/tags/v0.6.2/apps/mp32pod.cpp
A    line6linux/driver/tags/v0.6.2/apps/resample.cpp
A    line6linux/driver/tags/v0.6.2/apps/Makefile
A    line6linux/driver/tags/v0.6.2/midi.c
A    line6linux/driver/tags/v0.6.2/store_all_patches.sh
A    line6linux/driver/tags/v0.6.2/reinsert.sh
A    line6linux/driver/tags/v0.6.2/dumprequest.h
A    line6linux/driver/tags/v0.6.2/figures
A    line6linux/driver/tags/v0.6.2/figures/routing0.fig
A    line6linux/driver/tags/v0.6.2/figures/routing1.fig
A    line6linux/driver/tags/v0.6.2/figures/Makefile
A    line6linux/driver/tags/v0.6.2/figures/routing2.fig
A    line6linux/driver/tags/v0.6.2/figures/routing3.fig
A    line6linux/driver/tags/v0.6.2/logs
A    line6linux/driver/tags/v0.6.2/logs/compact.pl
A    line6linux/driver/tags/v0.6.2/logs/hex2raw.cpp
A    line6linux/driver/tags/v0.6.2/logs/extract_packet_sizes.pl
A    line6linux/driver/tags/v0.6.2/logs/Makefile
A    line6linux/driver/tags/v0.6.2/logs/extract_data.pl
A    line6linux/driver/tags/v0.6.2/tuner.sh
A    line6linux/driver/tags/v0.6.2/control.h
A    line6linux/driver/tags/v0.6.2/INSTALL
A    line6linux/driver/tags/v0.6.2/playback.c
A    line6linux/driver/tags/v0.6.2/download
A    line6linux/driver/tags/v0.6.2/download/create_symlinks.sh
A    line6linux/driver/tags/v0.6.2/download/downsample_interpolate.patch
A    line6linux/driver/tags/v0.6.2/midi.h
A    line6linux/driver/tags/v0.6.2/get_all_data.sh
A    line6linux/driver/tags/v0.6.2/makedist.sh
A    line6linux/driver/tags/v0.6.2/playback.h
A    line6linux/driver/tags/v0.6.2/make_control_tab.sh
A    line6linux/driver/tags/v0.6.2/driver.c
A    line6linux/driver/tags/v0.6.2/create_links.pl
A    line6linux/driver/tags/v0.6.2/Makefile
A    line6linux/driver/tags/v0.6.2/podxtpro.spec.in
A    line6linux/driver/tags/v0.6.2/line6usb.spec
A    line6linux/driver/tags/v0.6.2/out.sh
A    line6linux/driver/tags/v0.6.2/podxtpro_resample.sh
A    line6linux/driver/tags/v0.6.2/driver.h
A    line6linux/driver/tags/v0.6.2/usbdefs.h
A    line6linux/driver/tags/v0.6.2/audio.c
A    line6linux/driver/tags/v0.6.2/capture.c
A    line6linux/driver/tags/v0.6.2/store_all_data.sh
A    line6linux/driver/tags/v0.6.2/get_all_patches.sh
A    line6linux/driver/tags/v0.6.2/audio.h
A    line6linux/driver/tags/v0.6.2/record.sh
A    line6linux/driver/tags/v0.6.2/arecord.sh
A    line6linux/driver/tags/v0.6.2/capture.h
A    line6linux/driver/tags/v0.6.2/pcm.c
A    line6linux/driver/tags/v0.6.2/pod.c
A    line6linux/driver/tags/v0.6.2/pcm.h
A    line6linux/driver/tags/v0.6.2/line6_find_device.pl
A    line6linux/driver/tags/v0.6.2/restart_usb.sh
A    line6linux/driver/tags/v0.6.2/pod.h
A    line6linux/driver/tags/v0.6.2/variax.c
A    line6linux/driver/tags/v0.6.2/capture.sh
A    line6linux/driver/tags/v0.6.2/control_intro.c
A    line6linux/driver/tags/v0.6.2/create_control.pl
A    line6linux/driver/tags/v0.6.2/make_control_tab.pl
A    line6linux/driver/tags/v0.6.2/play.sh
A    line6linux/driver/tags/v0.6.2/remove_old_podxtpro_driver.sh
A    line6linux/driver/tags/v0.6.3
A    line6linux/driver/tags/v0.6.3/driverdocs.lyx
A    line6linux/driver/tags/v0.6.3/aplay.sh
A    line6linux/driver/tags/v0.6.3/retrieve_all_data.sh
A    line6linux/driver/tags/v0.6.3/variax.h
A    line6linux/driver/tags/v0.6.3/control_pod.tex
A    line6linux/driver/tags/v0.6.3/read_batch.sh
A    line6linux/driver/tags/v0.6.3/alsa_modules.txt
A    line6linux/driver/tags/v0.6.3/control_variax.tex
A    line6linux/driver/tags/v0.6.3/config.h
A    line6linux/driver/tags/v0.6.3/restart_alsa.sh
A    line6linux/driver/tags/v0.6.3/control.txt
A    line6linux/driver/tags/v0.6.3/dumprequest.c
A    line6linux/driver/tags/v0.6.3/control.c
A    line6linux/driver/tags/v0.6.3/update_version.pl
A    line6linux/driver/tags/v0.6.3/apps
A    line6linux/driver/tags/v0.6.3/apps/resample.sh
A    line6linux/driver/tags/v0.6.3/apps/mp32pod.cpp
A    line6linux/driver/tags/v0.6.3/apps/resample.cpp
A    line6linux/driver/tags/v0.6.3/apps/Makefile
A    line6linux/driver/tags/v0.6.3/midi.c
A    line6linux/driver/tags/v0.6.3/store_all_patches.sh
A    line6linux/driver/tags/v0.6.3/reinsert.sh
A    line6linux/driver/tags/v0.6.3/dumprequest.h
A    line6linux/driver/tags/v0.6.3/figures
A    line6linux/driver/tags/v0.6.3/figures/routing0.fig
A    line6linux/driver/tags/v0.6.3/figures/routing1.fig
A    line6linux/driver/tags/v0.6.3/figures/Makefile
A    line6linux/driver/tags/v0.6.3/figures/routing2.fig
A    line6linux/driver/tags/v0.6.3/figures/routing3.fig
A    line6linux/driver/tags/v0.6.3/logs
A    line6linux/driver/tags/v0.6.3/logs/compact.pl
A    line6linux/driver/tags/v0.6.3/logs/hex2raw.cpp
A    line6linux/driver/tags/v0.6.3/logs/extract_packet_sizes.pl
A    line6linux/driver/tags/v0.6.3/logs/Makefile
A    line6linux/driver/tags/v0.6.3/logs/extract_data.pl
A    line6linux/driver/tags/v0.6.3/tuner.sh
A    line6linux/driver/tags/v0.6.3/control.h
A    line6linux/driver/tags/v0.6.3/INSTALL
A    line6linux/driver/tags/v0.6.3/playback.c
A    line6linux/driver/tags/v0.6.3/download
A    line6linux/driver/tags/v0.6.3/download/create_symlinks.sh
A    line6linux/driver/tags/v0.6.3/download/downsample_interpolate.patch
A    line6linux/driver/tags/v0.6.3/midi.h
A    line6linux/driver/tags/v0.6.3/get_all_data.sh
A    line6linux/driver/tags/v0.6.3/makedist.sh
A    line6linux/driver/tags/v0.6.3/playback.h
A    line6linux/driver/tags/v0.6.3/make_control_tab.sh
A    line6linux/driver/tags/v0.6.3/driver.c
A    line6linux/driver/tags/v0.6.3/create_links.pl
A    line6linux/driver/tags/v0.6.3/Makefile
A    line6linux/driver/tags/v0.6.3/podxtpro.spec.in
A    line6linux/driver/tags/v0.6.3/line6usb.spec
A    line6linux/driver/tags/v0.6.3/out.sh
A    line6linux/driver/tags/v0.6.3/podxtpro_resample.sh
A    line6linux/driver/tags/v0.6.3/driver.h
A    line6linux/driver/tags/v0.6.3/usbdefs.h
A    line6linux/driver/tags/v0.6.3/audio.c
A    line6linux/driver/tags/v0.6.3/capture.c
A    line6linux/driver/tags/v0.6.3/store_all_data.sh
A    line6linux/driver/tags/v0.6.3/get_all_patches.sh
A    line6linux/driver/tags/v0.6.3/audio.h
A    line6linux/driver/tags/v0.6.3/record.sh
A    line6linux/driver/tags/v0.6.3/arecord.sh
A    line6linux/driver/tags/v0.6.3/capture.h
A    line6linux/driver/tags/v0.6.3/pcm.c
A    line6linux/driver/tags/v0.6.3/pod.c
A    line6linux/driver/tags/v0.6.3/pcm.h
A    line6linux/driver/tags/v0.6.3/line6_find_device.pl
A    line6linux/driver/tags/v0.6.3/restart_usb.sh
A    line6linux/driver/tags/v0.6.3/pod.h
A    line6linux/driver/tags/v0.6.3/variax.c
A    line6linux/driver/tags/v0.6.3/capture.sh
A    line6linux/driver/tags/v0.6.3/control_intro.c
A    line6linux/driver/tags/v0.6.3/create_control.pl
A    line6linux/driver/tags/v0.6.3/make_control_tab.pl
A    line6linux/driver/tags/v0.6.3/play.sh
A    line6linux/driver/tags/v0.6.3/remove_old_podxtpro_driver.sh
A    line6linux/driver/tags/v0.7.2
A    line6linux/driver/tags/v0.7.2/driverdocs.lyx
A    line6linux/driver/tags/v0.7.2/aplay.sh
A    line6linux/driver/tags/v0.7.2/retrieve_all_data.sh
A    line6linux/driver/tags/v0.7.2/variax.h
A    line6linux/driver/tags/v0.7.2/control_pod.tex
A    line6linux/driver/tags/v0.7.2/pod_resample.sh
A    line6linux/driver/tags/v0.7.2/read_batch.sh
A    line6linux/driver/tags/v0.7.2/alsa_modules.txt
A    line6linux/driver/tags/v0.7.2/control_variax.tex
A    line6linux/driver/tags/v0.7.2/config.h
A    line6linux/driver/tags/v0.7.2/restart_alsa.sh
A    line6linux/driver/tags/v0.7.2/control.txt
A    line6linux/driver/tags/v0.7.2/dumprequest.c
A    line6linux/driver/tags/v0.7.2/control.c
A    line6linux/driver/tags/v0.7.2/update_version.pl
A    line6linux/driver/tags/v0.7.2/midi.c
A    line6linux/driver/tags/v0.7.2/apps
A    line6linux/driver/tags/v0.7.2/apps/resample.sh
A    line6linux/driver/tags/v0.7.2/apps/mp32pod.cpp
A    line6linux/driver/tags/v0.7.2/apps/resample.cpp
A    line6linux/driver/tags/v0.7.2/apps/Makefile
A    line6linux/driver/tags/v0.7.2/store_all_patches.sh
A    line6linux/driver/tags/v0.7.2/reinsert.sh
A    line6linux/driver/tags/v0.7.2/logs
A    line6linux/driver/tags/v0.7.2/logs/compact.pl
A    line6linux/driver/tags/v0.7.2/logs/hex2raw.cpp
A    line6linux/driver/tags/v0.7.2/logs/extract_packet_sizes.pl
A    line6linux/driver/tags/v0.7.2/logs/Makefile
A    line6linux/driver/tags/v0.7.2/logs/extract_data.pl
A    line6linux/driver/tags/v0.7.2/dumprequest.h
A    line6linux/driver/tags/v0.7.2/figures
A    line6linux/driver/tags/v0.7.2/figures/routing0.fig
A    line6linux/driver/tags/v0.7.2/figures/routing1.fig
A    line6linux/driver/tags/v0.7.2/figures/Makefile
A    line6linux/driver/tags/v0.7.2/figures/routing2.fig
A    line6linux/driver/tags/v0.7.2/figures/routing3.fig
A    line6linux/driver/tags/v0.7.2/tuner.sh
A    line6linux/driver/tags/v0.7.2/control.h
A    line6linux/driver/tags/v0.7.2/INSTALL
A    line6linux/driver/tags/v0.7.2/playback.c
A    line6linux/driver/tags/v0.7.2/download
A    line6linux/driver/tags/v0.7.2/download/create_symlinks.sh
A    line6linux/driver/tags/v0.7.2/download/downsample_interpolate.patch
A    line6linux/driver/tags/v0.7.2/midi.h
A    line6linux/driver/tags/v0.7.2/get_all_data.sh
A    line6linux/driver/tags/v0.7.2/makedist.sh
A    line6linux/driver/tags/v0.7.2/make_control_tab.sh
A    line6linux/driver/tags/v0.7.2/driver.c
A    line6linux/driver/tags/v0.7.2/playback.h
A    line6linux/driver/tags/v0.7.2/downsample_interpolate.patch
A    line6linux/driver/tags/v0.7.2/create_links.pl
A    line6linux/driver/tags/v0.7.2/Makefile
A    line6linux/driver/tags/v0.7.2/podxtpro.spec.in
A    line6linux/driver/tags/v0.7.2/line6usb.spec
A    line6linux/driver/tags/v0.7.2/out.sh
A    line6linux/driver/tags/v0.7.2/driver.h
A    line6linux/driver/tags/v0.7.2/usbdefs.h
A    line6linux/driver/tags/v0.7.2/audio.c
A    line6linux/driver/tags/v0.7.2/capture.c
A    line6linux/driver/tags/v0.7.2/store_all_data.sh
A    line6linux/driver/tags/v0.7.2/get_all_patches.sh
A    line6linux/driver/tags/v0.7.2/audio.h
A    line6linux/driver/tags/v0.7.2/record.sh
A    line6linux/driver/tags/v0.7.2/arecord.sh
A    line6linux/driver/tags/v0.7.2/capture.h
A    line6linux/driver/tags/v0.7.2/resample.conf
A    line6linux/driver/tags/v0.7.2/pcm.c
A    line6linux/driver/tags/v0.7.2/pod.c
A    line6linux/driver/tags/v0.7.2/pcm.h
A    line6linux/driver/tags/v0.7.2/line6_find_device.pl
A    line6linux/driver/tags/v0.7.2/restart_usb.sh
A    line6linux/driver/tags/v0.7.2/pod.h
A    line6linux/driver/tags/v0.7.2/variax.c
A    line6linux/driver/tags/v0.7.2/capture.sh
A    line6linux/driver/tags/v0.7.2/control_intro.c
A    line6linux/driver/tags/v0.7.2/create_control.pl
A    line6linux/driver/tags/v0.7.2/make_control_tab.pl
A    line6linux/driver/tags/v0.7.2/play.sh
A    line6linux/driver/tags/v0.7.2/remove_old_podxtpro_driver.sh
A    line6linux/driver/tags/v0.8.1
A    line6linux/driver/tags/v0.8.1/variax.h
A    line6linux/driver/tags/v0.8.1/control_pod.tex
A    line6linux/driver/tags/v0.8.1/debian
A    line6linux/driver/tags/v0.8.1/debian/control
A    line6linux/driver/tags/v0.8.1/debian/compat
A    line6linux/driver/tags/v0.8.1/debian/watch
A    line6linux/driver/tags/v0.8.1/debian/changelog
A    line6linux/driver/tags/v0.8.1/debian/copyright
A    line6linux/driver/tags/v0.8.1/debian/rules
A    line6linux/driver/tags/v0.8.1/debian/control.modules.in
A    line6linux/driver/tags/v0.8.1/pod_resample.sh
A    line6linux/driver/tags/v0.8.1/read_batch.sh
A    line6linux/driver/tags/v0.8.1/toneport.c
A    line6linux/driver/tags/v0.8.1/config.h
A    line6linux/driver/tags/v0.8.1/dumprequest.c
A    line6linux/driver/tags/v0.8.1/toneport.h
A    line6linux/driver/tags/v0.8.1/midibuf.c
A    line6linux/driver/tags/v0.8.1/control.c
A    line6linux/driver/tags/v0.8.1/apps
A    line6linux/driver/tags/v0.8.1/apps/resample.sh
A    line6linux/driver/tags/v0.8.1/apps/mp32pod.cpp
A    line6linux/driver/tags/v0.8.1/apps/resample.cpp
A    line6linux/driver/tags/v0.8.1/apps/Makefile
A    line6linux/driver/tags/v0.8.1/figures
A    line6linux/driver/tags/v0.8.1/figures/line6_linux.jpg
A    line6linux/driver/tags/v0.8.1/figures/routing0.fig
A    line6linux/driver/tags/v0.8.1/figures/routing1.fig
A    line6linux/driver/tags/v0.8.1/figures/Makefile
A    line6linux/driver/tags/v0.8.1/figures/routing2.fig
A    line6linux/driver/tags/v0.8.1/figures/routing3.fig
A    line6linux/driver/tags/v0.8.1/dumprequest.h
A    line6linux/driver/tags/v0.8.1/reinsert.sh
A    line6linux/driver/tags/v0.8.1/midibuf.h
A    line6linux/driver/tags/v0.8.1/control.h
A    line6linux/driver/tags/v0.8.1/get_all_data.sh
A    line6linux/driver/tags/v0.8.1/makedist.sh
A    line6linux/driver/tags/v0.8.1/podxtpro.spec.in
A    line6linux/driver/tags/v0.8.1/Makefile
A    line6linux/driver/tags/v0.8.1/create_links.pl
A    line6linux/driver/tags/v0.8.1/downsample_interpolate.patch
A    line6linux/driver/tags/v0.8.1/out.sh
A    line6linux/driver/tags/v0.8.1/line6usb.spec
A    line6linux/driver/tags/v0.8.1/set_revision.sh
A    line6linux/driver/tags/v0.8.1/capture.c
A    line6linux/driver/tags/v0.8.1/store_all_data.sh
A    line6linux/driver/tags/v0.8.1/capture.h
A    line6linux/driver/tags/v0.8.1/resample.conf
A    line6linux/driver/tags/v0.8.1/pod.c
A    line6linux/driver/tags/v0.8.1/restart_usb.sh
A    line6linux/driver/tags/v0.8.1/pod.h
A    line6linux/driver/tags/v0.8.1/capture.sh
A    line6linux/driver/tags/v0.8.1/makefile
A    line6linux/driver/tags/v0.8.1/driverdocs.lyx
A    line6linux/driver/tags/v0.8.1/aplay.sh
A    line6linux/driver/tags/v0.8.1/midibuf
A    line6linux/driver/tags/v0.8.1/midibuf/midibuf.c
A    line6linux/driver/tags/v0.8.1/midibuf/main.cpp
A    line6linux/driver/tags/v0.8.1/midibuf/CMakeLists.txt
A    line6linux/driver/tags/v0.8.1/retrieve_all_data.sh
A    line6linux/driver/tags/v0.8.1/alsa_modules.txt
A    line6linux/driver/tags/v0.8.1/batch_replace.pl
A    line6linux/driver/tags/v0.8.1/control_variax.tex
A    line6linux/driver/tags/v0.8.1/restart_alsa.sh
A    line6linux/driver/tags/v0.8.1/control.txt
A    line6linux/driver/tags/v0.8.1/update_version.pl
A    line6linux/driver/tags/v0.8.1/midi.c
A    line6linux/driver/tags/v0.8.1/store_all_patches.sh
A    line6linux/driver/tags/v0.8.1/logs
A    line6linux/driver/tags/v0.8.1/logs/compact.pl
A    line6linux/driver/tags/v0.8.1/logs/hex2raw.cpp
A    line6linux/driver/tags/v0.8.1/logs/extract_packet_sizes.pl
A    line6linux/driver/tags/v0.8.1/logs/Makefile
A    line6linux/driver/tags/v0.8.1/logs/extract_data.pl
A    line6linux/driver/tags/v0.8.1/tuner.sh
A    line6linux/driver/tags/v0.8.1/INSTALL
A    line6linux/driver/tags/v0.8.1/download
A    line6linux/driver/tags/v0.8.1/download/create_symlinks.sh
A    line6linux/driver/tags/v0.8.1/download/downsample_interpolate.patch
A    line6linux/driver/tags/v0.8.1/playback.c
A    line6linux/driver/tags/v0.8.1/midi.h
A    line6linux/driver/tags/v0.8.1/driver.c
A    line6linux/driver/tags/v0.8.1/make_control_tab.sh
A    line6linux/driver/tags/v0.8.1/playback.h
A    line6linux/driver/tags/v0.8.1/.bzrignore
A    line6linux/driver/tags/v0.8.1/usbdefs.h
A    line6linux/driver/tags/v0.8.1/driver.h
A    line6linux/driver/tags/v0.8.1/audio.c
A    line6linux/driver/tags/v0.8.1/audio.h
A    line6linux/driver/tags/v0.8.1/get_all_patches.sh
A    line6linux/driver/tags/v0.8.1/record.sh
A    line6linux/driver/tags/v0.8.1/arecord.sh
A    line6linux/driver/tags/v0.8.1/pcm.c
A    line6linux/driver/tags/v0.8.1/pcm.h
A    line6linux/driver/tags/v0.8.1/line6_find_device.pl
A    line6linux/driver/tags/v0.8.1/variax.c
A    line6linux/driver/tags/v0.8.1/control_intro.c
A    line6linux/driver/tags/v0.8.1/make_control_tab.pl
A    line6linux/driver/tags/v0.8.1/create_control.pl
A    line6linux/driver/tags/v0.8.1/remove_old_podxtpro_driver.sh
A    line6linux/driver/tags/v0.8.1/play.sh
A    line6linux/driver/tags/v0.6.4
A    line6linux/driver/tags/v0.6.4/driverdocs.lyx
A    line6linux/driver/tags/v0.6.4/aplay.sh
A    line6linux/driver/tags/v0.6.4/retrieve_all_data.sh
A    line6linux/driver/tags/v0.6.4/variax.h
A    line6linux/driver/tags/v0.6.4/control_pod.tex
A    line6linux/driver/tags/v0.6.4/read_batch.sh
A    line6linux/driver/tags/v0.6.4/alsa_modules.txt
A    line6linux/driver/tags/v0.6.4/control_variax.tex
A    line6linux/driver/tags/v0.6.4/config.h
A    line6linux/driver/tags/v0.6.4/restart_alsa.sh
A    line6linux/driver/tags/v0.6.4/control.txt
A    line6linux/driver/tags/v0.6.4/dumprequest.c
A    line6linux/driver/tags/v0.6.4/control.c
A    line6linux/driver/tags/v0.6.4/update_version.pl
A    line6linux/driver/tags/v0.6.4/apps
A    line6linux/driver/tags/v0.6.4/apps/resample.sh
A    line6linux/driver/tags/v0.6.4/apps/mp32pod.cpp
A    line6linux/driver/tags/v0.6.4/apps/resample.cpp
A    line6linux/driver/tags/v0.6.4/apps/Makefile
A    line6linux/driver/tags/v0.6.4/midi.c
A    line6linux/driver/tags/v0.6.4/store_all_patches.sh
A    line6linux/driver/tags/v0.6.4/reinsert.sh
A    line6linux/driver/tags/v0.6.4/dumprequest.h
A    line6linux/driver/tags/v0.6.4/figures
A    line6linux/driver/tags/v0.6.4/figures/routing0.fig
A    line6linux/driver/tags/v0.6.4/figures/routing1.fig
A    line6linux/driver/tags/v0.6.4/figures/Makefile
A    line6linux/driver/tags/v0.6.4/figures/routing2.fig
A    line6linux/driver/tags/v0.6.4/figures/routing3.fig
A    line6linux/driver/tags/v0.6.4/logs
A    line6linux/driver/tags/v0.6.4/logs/compact.pl
A    line6linux/driver/tags/v0.6.4/logs/hex2raw.cpp
A    line6linux/driver/tags/v0.6.4/logs/extract_packet_sizes.pl
A    line6linux/driver/tags/v0.6.4/logs/Makefile
A    line6linux/driver/tags/v0.6.4/logs/extract_data.pl
A    line6linux/driver/tags/v0.6.4/tuner.sh
A    line6linux/driver/tags/v0.6.4/control.h
A    line6linux/driver/tags/v0.6.4/INSTALL
A    line6linux/driver/tags/v0.6.4/playback.c
A    line6linux/driver/tags/v0.6.4/download
A    line6linux/driver/tags/v0.6.4/download/create_symlinks.sh
A    line6linux/driver/tags/v0.6.4/download/downsample_interpolate.patch
A    line6linux/driver/tags/v0.6.4/midi.h
A    line6linux/driver/tags/v0.6.4/get_all_data.sh
A    line6linux/driver/tags/v0.6.4/makedist.sh
A    line6linux/driver/tags/v0.6.4/playback.h
A    line6linux/driver/tags/v0.6.4/make_control_tab.sh
A    line6linux/driver/tags/v0.6.4/driver.c
A    line6linux/driver/tags/v0.6.4/create_links.pl
A    line6linux/driver/tags/v0.6.4/Makefile
A    line6linux/driver/tags/v0.6.4/podxtpro.spec.in
A    line6linux/driver/tags/v0.6.4/line6usb.spec
A    line6linux/driver/tags/v0.6.4/out.sh
A    line6linux/driver/tags/v0.6.4/podxtpro_resample.sh
A    line6linux/driver/tags/v0.6.4/driver.h
A    line6linux/driver/tags/v0.6.4/usbdefs.h
A    line6linux/driver/tags/v0.6.4/audio.c
A    line6linux/driver/tags/v0.6.4/capture.c
A    line6linux/driver/tags/v0.6.4/store_all_data.sh
A    line6linux/driver/tags/v0.6.4/get_all_patches.sh
A    line6linux/driver/tags/v0.6.4/audio.h
A    line6linux/driver/tags/v0.6.4/record.sh
A    line6linux/driver/tags/v0.6.4/arecord.sh
A    line6linux/driver/tags/v0.6.4/capture.h
A    line6linux/driver/tags/v0.6.4/pcm.c
A    line6linux/driver/tags/v0.6.4/pod.c
A    line6linux/driver/tags/v0.6.4/pcm.h
A    line6linux/driver/tags/v0.6.4/line6_find_device.pl
A    line6linux/driver/tags/v0.6.4/restart_usb.sh
A    line6linux/driver/tags/v0.6.4/pod.h
A    line6linux/driver/tags/v0.6.4/variax.c
A    line6linux/driver/tags/v0.6.4/capture.sh
A    line6linux/driver/tags/v0.6.4/control_intro.c
A    line6linux/driver/tags/v0.6.4/create_control.pl
A    line6linux/driver/tags/v0.6.4/make_control_tab.pl
A    line6linux/driver/tags/v0.6.4/play.sh
A    line6linux/driver/tags/v0.6.4/remove_old_podxtpro_driver.sh
A    line6linux/driver/tags/v0.6.5
A    line6linux/driver/tags/v0.6.5/driverdocs.lyx
A    line6linux/driver/tags/v0.6.5/aplay.sh
A    line6linux/driver/tags/v0.6.5/retrieve_all_data.sh
A    line6linux/driver/tags/v0.6.5/variax.h
A    line6linux/driver/tags/v0.6.5/control_pod.tex
A    line6linux/driver/tags/v0.6.5/read_batch.sh
A    line6linux/driver/tags/v0.6.5/alsa_modules.txt
A    line6linux/driver/tags/v0.6.5/control_variax.tex
A    line6linux/driver/tags/v0.6.5/config.h
A    line6linux/driver/tags/v0.6.5/restart_alsa.sh
A    line6linux/driver/tags/v0.6.5/control.txt
A    line6linux/driver/tags/v0.6.5/dumprequest.c
A    line6linux/driver/tags/v0.6.5/control.c
A    line6linux/driver/tags/v0.6.5/update_version.pl
A    line6linux/driver/tags/v0.6.5/apps
A    line6linux/driver/tags/v0.6.5/apps/resample.sh
A    line6linux/driver/tags/v0.6.5/apps/mp32pod.cpp
A    line6linux/driver/tags/v0.6.5/apps/resample.cpp
A    line6linux/driver/tags/v0.6.5/apps/Makefile
A    line6linux/driver/tags/v0.6.5/midi.c
A    line6linux/driver/tags/v0.6.5/store_all_patches.sh
A    line6linux/driver/tags/v0.6.5/reinsert.sh
A    line6linux/driver/tags/v0.6.5/dumprequest.h
A    line6linux/driver/tags/v0.6.5/figures
A    line6linux/driver/tags/v0.6.5/figures/routing0.fig
A    line6linux/driver/tags/v0.6.5/figures/routing1.fig
A    line6linux/driver/tags/v0.6.5/figures/Makefile
A    line6linux/driver/tags/v0.6.5/figures/routing2.fig
A    line6linux/driver/tags/v0.6.5/figures/routing3.fig
A    line6linux/driver/tags/v0.6.5/logs
A    line6linux/driver/tags/v0.6.5/logs/compact.pl
A    line6linux/driver/tags/v0.6.5/logs/hex2raw.cpp
A    line6linux/driver/tags/v0.6.5/logs/extract_packet_sizes.pl
A    line6linux/driver/tags/v0.6.5/logs/Makefile
A    line6linux/driver/tags/v0.6.5/logs/extract_data.pl
A    line6linux/driver/tags/v0.6.5/tuner.sh
A    line6linux/driver/tags/v0.6.5/control.h
A    line6linux/driver/tags/v0.6.5/INSTALL
A    line6linux/driver/tags/v0.6.5/playback.c
A    line6linux/driver/tags/v0.6.5/download
A    line6linux/driver/tags/v0.6.5/download/create_symlinks.sh
A    line6linux/driver/tags/v0.6.5/download/downsample_interpolate.patch
A    line6linux/driver/tags/v0.6.5/midi.h
A    line6linux/driver/tags/v0.6.5/get_all_data.sh
A    line6linux/driver/tags/v0.6.5/makedist.sh
A    line6linux/driver/tags/v0.6.5/playback.h
A    line6linux/driver/tags/v0.6.5/make_control_tab.sh
A    line6linux/driver/tags/v0.6.5/driver.c
A    line6linux/driver/tags/v0.6.5/create_links.pl
A    line6linux/driver/tags/v0.6.5/Makefile
A    line6linux/driver/tags/v0.6.5/podxtpro.spec.in
A    line6linux/driver/tags/v0.6.5/line6usb.spec
A    line6linux/driver/tags/v0.6.5/out.sh
A    line6linux/driver/tags/v0.6.5/podxtpro_resample.sh
A    line6linux/driver/tags/v0.6.5/driver.h
A    line6linux/driver/tags/v0.6.5/usbdefs.h
A    line6linux/driver/tags/v0.6.5/audio.c
A    line6linux/driver/tags/v0.6.5/capture.c
A    line6linux/driver/tags/v0.6.5/store_all_data.sh
A    line6linux/driver/tags/v0.6.5/get_all_patches.sh
A    line6linux/driver/tags/v0.6.5/audio.h
A    line6linux/driver/tags/v0.6.5/record.sh
A    line6linux/driver/tags/v0.6.5/arecord.sh
A    line6linux/driver/tags/v0.6.5/capture.h
A    line6linux/driver/tags/v0.6.5/pcm.c
A    line6linux/driver/tags/v0.6.5/pod.c
A    line6linux/driver/tags/v0.6.5/pcm.h
A    line6linux/driver/tags/v0.6.5/line6_find_device.pl
A    line6linux/driver/tags/v0.6.5/restart_usb.sh
A    line6linux/driver/tags/v0.6.5/pod.h
A    line6linux/driver/tags/v0.6.5/variax.c
A    line6linux/driver/tags/v0.6.5/capture.sh
A    line6linux/driver/tags/v0.6.5/control_intro.c
A    line6linux/driver/tags/v0.6.5/create_control.pl
A    line6linux/driver/tags/v0.6.5/make_control_tab.pl
A    line6linux/driver/tags/v0.6.5/play.sh
A    line6linux/driver/tags/v0.6.5/remove_old_podxtpro_driver.sh
Checked out revision 938.
nick@NickUbuntu:~$ cd line6linux/driver/trunk
nick@NickUbuntu:~/line6linux/driver/trunk$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.2.0-29-generic-pae is already the newest version.
linux-headers-3.2.0-29-generic-pae set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
nick@NickUbuntu:~/line6linux/driver/trunk$ make
./set_revision.sh
./set_revision.sh: 9: test: [https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:](https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:) unexpected operator
make -C /lib/modules/3.2.0-29-generic-pae/build CONFIG_LINE6_USB=m SUBDIRS=/home/nick/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  CC [M]  /home/nick/line6linux/driver/trunk/audio.o
/home/nick/line6linux/driver/trunk/audio.c: In function &#8216;line6_init_audio&#8217;:
/home/nick/line6linux/driver/trunk/audio.c:30:57: error: &#8216;THIS_MODULE&#8217; undeclared (first use in this function)
/home/nick/line6linux/driver/trunk/audio.c:30:57: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/nick/line6linux/driver/trunk/audio.o] Error 1
make[1]: *** [_module_/home/nick/line6linux/driver/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
make: *** [default] Error 2
nick@NickUbuntu:~/line6linux/driver/trunk$
```

---

### Post by 777funk on 2012-08-26
Just tried it again and got some errors. Not sure what I'm doing wrong.


nick@NickUbuntu:~$ cd line6linux/driver/trunk
nick@NickUbuntu:~/line6linux/driver/trunk$ make clean
rm -f core .*.cmd *.o *.ko *.mod.c *.bak .\#* *~ Module.*
rm -rf .tmp_versions
nick@NickUbuntu:~/line6linux/driver/trunk$ make
./set_revision.sh
./set_revision.sh: 9: test: [https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:](https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:) unexpected operator
make -C /lib/modules/3.2.0-29-generic-pae/build CONFIG_LINE6_USB=m SUBDIRS=/home/nick/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  CC [M]  /home/nick/line6linux/driver/trunk/audio.o
/home/nick/line6linux/driver/trunk/audio.c: In function ‘line6_init_audio’:
/home/nick/line6linux/driver/trunk/audio.c:30:57: error: ‘THIS_MODULE’ undeclared (first use in this function)
/home/nick/line6linux/driver/trunk/audio.c:30:57: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/nick/line6linux/driver/trunk/audio.o] Error 1
make[1]: *** [_module_/home/nick/line6linux/driver/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
make: *** [default] Error 2
nick@NickUbuntu:~/line6linux/driver/trunk$ ^C
nick@NickUbuntu:~/line6linux/driver/trunk$ sudo make install
[sudo] password for nick: 
./set_revision.sh
./set_revision.sh: 9: test: [https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:](https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:) unexpected operator
make -C /lib/modules/3.2.0-29-generic-pae/build CONFIG_LINE6_USB=m SUBDIRS=/home/nick/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  CC [M]  /home/nick/line6linux/driver/trunk/audio.o
/home/nick/line6linux/driver/trunk/audio.c: In function ‘line6_init_audio’:
/home/nick/line6linux/driver/trunk/audio.c:30:57: error: ‘THIS_MODULE’ undeclared (first use in this function)
/home/nick/line6linux/driver/trunk/audio.c:30:57: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/nick/line6linux/driver/trunk/audio.o] Error 1
make[1]: *** [_module_/home/nick/line6linux/driver/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
make: *** [default] Error 2
nick@NickUbuntu:~/line6linux/driver/trunk$

---

### Post by steeldriver on 2012-08-26
I'm still not convinced you need to be going down this route - but fwiw if I had to make a guess it would be that the makefile is expecting /bin/sh to be bash (or a strict Bourne shell) and is failing because /bin/sh is symlinked to the dash shell in Ubuntu

[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

To avoid having to modify the makefile, you could try passing a modified shell variable via the make command line e.g.

```
make "SHELL=/bin/bash"
```

or if that doesn't work try exporting it from the invoking shell:

```
export SHELL=/bin/bash ; make
```

If those don't work and you really want to do this then you could temporarily modify the symlink with

```
sudo ln -sf bash /bin/sh
```

You can revert it after you're done with

```
sudo ln -sf dash /bin/sh
```

---

### Post by 777funk on 2012-08-26
Thanks Steel. I tried both of those and ended up with this:

> nick@NickUbuntu:~$ cd line6linux/driver/trunk
nick@NickUbuntu:~/line6linux/driver/trunk$ make "SHELL=/bin/bash"
./set_revision.sh
./set_revision.sh: 9: test: [https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:](https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:) unexpected operator
make -C /lib/modules/3.2.0-29-generic-pae/build CONFIG_LINE6_USB=m SUBDIRS=/home/nick/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  CC [M]  /home/nick/line6linux/driver/trunk/audio.o
/home/nick/line6linux/driver/trunk/audio.c: In function ‘line6_init_audio’:
/home/nick/line6linux/driver/trunk/audio.c:30:57: error: ‘THIS_MODULE’ undeclared (first use in this function)
/home/nick/line6linux/driver/trunk/audio.c:30:57: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/nick/line6linux/driver/trunk/audio.o] Error 1
make[1]: *** [_module_/home/nick/line6linux/driver/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
make: *** [default] Error 2
nick@NickUbuntu:~/line6linux/driver/trunk$ export SHELL=/bin/bash ; make
./set_revision.sh
./set_revision.sh: 9: test: [https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:](https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:) unexpected operator
make -C /lib/modules/3.2.0-29-generic-pae/build CONFIG_LINE6_USB=m SUBDIRS=/home/nick/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  CC [M]  /home/nick/line6linux/driver/trunk/audio.o
/home/nick/line6linux/driver/trunk/audio.c: In function ‘line6_init_audio’:
/home/nick/line6linux/driver/trunk/audio.c:30:57: error: ‘THIS_MODULE’ undeclared (first use in this function)
/home/nick/line6linux/driver/trunk/audio.c:30:57: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/nick/line6linux/driver/trunk/audio.o] Error 1
make[1]: *** [_module_/home/nick/line6linux/driver/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
make: *** [default] Error 2
nick@NickUbuntu:~/line6linux/driver/trunk$ 


---

### Post by Cheesemill on 2012-08-27
With your Line 6 device plugged in can you post the output of:
```
lsusb
aplay -L
```

---

### Post by 777funk on 2012-08-27
> **Cheesemill said:**
> With your Line 6 device plugged in can you post the output of:
```
lsusb
aplay -L
```


Sure, Here's what I've got:

> nick@NickUbuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1a40:0201 Terminus Technology Inc. Hub
Bus 001 Device 003: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 001 Device 004: ID 0e41:4143 Line6, Inc. 
Bus 001 Device 005: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 006: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 007: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
nick@NickUbuntu:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=NVidia
    HDA NVidia, ALC888 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Hardware device with all software conversions
nick@NickUbuntu:~$ 

---

### Post by 777funk on 2012-08-27
It looks like it's showing in the USB but no communication. Any idea how to get past the errors that Terminal listed?

---

### Post by bogan on 2012-08-27
H1!, **777funk**,

The reason you got a request to state the file to be installed is that you must specify which kernal-header you mean:
Run 'uname -r' and insert the output in the following command: substituting it for 'uname -r', for example:
"sudo apt-get install linux-headers-3.2.0-29-generic-pae"```
sudo apt-get install linux-headers-'uname -r'
```Chao!, **bogan**.

---

### Post by 777funk on 2012-08-27
I'm still very confused as to what I'm doing wrong. Are there any symptom details I'm not giving that would be helpful to get the answer I need to solve this problem.

---

### Post by steeldriver on 2012-08-27
I think we're all confused about what the problem is - what exactly is not working with the card that leads you to believe you need to build a driver from source?

[COLOR=Silver][FWIW I still think the build problem is likely related to /bin/sh -> dash (the 'unexpected operator' is symptomatic). My first 2 suggested workarounds would only deal with make's internal expansion of the $SHELL variable, and would not fix explicit references to /bin/sh, which is what it looks like you are dealing with (in particular, the makefile seems to be calling an actual shell script called ./set_revision.sh, which likely invokes /bin/sh as interpreter i.e. starts with #!/bin/sh) . To work around that you really would need to modify the system symlink for /bin/sh as per my 3rd suggestion, I think. If you're determined to try it then at least pause between 'make' and 'make install', take a deep breath and think it through.][/COLOR]

---

### Post by 777funk on 2012-08-27
Steel, I just tried what you said in the earlier post and I don't think it worked either. Still getting the errors.

sudo ln -sf bash /bin/sh

As far as me thinking it's not working, we'll I don't hear any sound from the device and it's not showing in my audio settings. So as far as I can see it's not working. I don't think it would be natively picked up by Linux. In Windows I had to download and install a special set of drivers to get it to work. And someone has written drivers for Linux (link/install location shown in the first post). 

I really would like to have sound again. I just don't know enough about Linux to know what's going wrong.

---

### Post by 777funk on 2012-08-27
So Here's what I've got. 

I check the version and it's: 3.2.0-29-generic-pae 

Looks like everything is ok until I go to:

Make

then I get the errors I posted from the terminal in post #11. Whatever those are are what's keeping it from working I'd assume.

It says in the thread pertaining to this device:
[http://ubuntuforums.org/showthread.php?t=1163608](http://ubuntuforums.org/showthread.php?t=1163608)

That it should show in System/Sound and it's not there.

---

### Post by 777funk on 2012-08-27
Just looked at the last page of the original thread on this and others are having the same problem:

[http://ubuntuforums.org/showthread.php?t=1163608&page=3](http://ubuntuforums.org/showthread.php?t=1163608&page=3)

---

### Post by steeldriver on 2012-08-28
OK so I had a play with it myself

1. linking /bin/sh to bash does indeed make the ./set_revision error go away

2. newer kernels need an additional include file to supply the THIS_MODULE definition - see[ http://blog.gmane.org/gmane.comp.audio.line6linux.user/month=20120301]("http://blog.gmane.org/gmane.comp.audio.line6linux.user/month=20120301") for example

If you add

```
#include <linux/export.h>
```at the top of the line6linux/driver/trunk/audio.c file (I put it ahead of the other includes, right above sound/core.h) you should find that the driver will build.

I didn't try to 'make install' because I don't want the cruft on my system - PLEASE BE 100% SURE YOU DO - as others have already pointed out there are several reports of conflicts / problems on later systems even in the original link you posted.

Hope this helps. This was on 3.2.0-29-generic-pae btw.

---

### Post by 777funk on 2012-08-28
> **steeldriver said:**
> OK so I had a play with it myself

1. linking /bin/sh to bash does indeed make the ./set_revision error go away

2. newer kernels need an additional include file to supply the THIS_MODULE definition - see[ http://blog.gmane.org/gmane.comp.audio.line6linux.user/month=20120301]("http://blog.gmane.org/gmane.comp.audio.line6linux.user/month=20120301") for example

If you add

```
#include <linux/export.h>
```at the top of the line6linux/driver/trunk/audio.c file (I put it ahead of the other includes, right above sound/core.h) you should find that the driver will build.

I didn't try to 'make install' because I don't want the cruft on my system - PLEASE BE 100% SURE YOU DO - as others have already pointed out there are several reports of conflicts / problems on later systems even in the original link you posted.

Hope this helps. This was on 3.2.0-29-generic-pae btw.

Thanks for that. So do I need to undo anything from earlier to make this work now? 

and would my steps be the same now as before (but now with that file edited).... i.e. :

[COLOR=Purple]Change to the directory
[/COLOR]  	[COLOR=Purple]PHP Code:[/COLOR]
 	[LEFT] 		[COLOR=Purple] 			[COLOR=#000000] [COLOR=#0000BB]cd line6linux[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]driver[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]trunk  
[/COLOR] [/COLOR]  		[/COLOR] 	[/LEFT]
 
[COLOR=Purple]	Time to build from the source but first make sure you have the latest build and headers

[/COLOR]   	[COLOR=Purple]PHP Code:[/COLOR]
 	[LEFT] 		[COLOR=Purple] 			[COLOR=#000000] [COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get install build[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]essential  
[/COLOR] [/COLOR]  		[/COLOR] 	[/LEFT]
 
 	[COLOR=Purple]PHP Code:[/COLOR]
 	[LEFT] 		[COLOR=Purple] 			[COLOR=#000000] [COLOR=#0000BB]sudo apt[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]get install linux[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]headers  
[/COLOR] [/COLOR]  		[/COLOR] 	[/LEFT]
 
[COLOR=Purple] (Note: You will atlest have version 2.6.27.14. To check your version in terminal type uname -r)

	Now that is updated and you are in the trunk directory [/COLOR] [COLOR=Purple]
[/COLOR]  	[COLOR=Purple]PHP Code:[/COLOR]
 	[LEFT] 		[COLOR=Purple] 			[COLOR=#000000] [COLOR=#0000BB]make  
[/COLOR] [/COLOR]  		[/COLOR] 	[/LEFT]
 
 	[COLOR=Purple]PHP Code:[/COLOR]
 	[LEFT] 		[COLOR=Purple] 			[COLOR=#000000] [COLOR=#0000BB]sudo make install  
[/COLOR] [/COLOR]  		[/COLOR] 	[/LEFT]
 
[COLOR=Purple]	Now shutdown and restart with the guitar port (or toneport) connected and you should beable to see it in your 
System> Preferences> Sound
[/COLOR]

---

### Post by 777funk on 2012-08-28
Here's what I did this morning. It seemed to go without errors:
> 
nick@NickUbuntu:~$ cd line6linux/driver/trunk
nick@NickUbuntu:~/line6linux/driver/trunk$ sudo apt-get install build-essential [sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.6 libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libdpkg-perl libstdc++6-4.6-dev libtimedate-perl
Suggested packages:
  debian-keyring g++-multilib g++-4.6-multilib gcc-4.6-doc libstdc++6-4.6-dbg
  libstdc++6-4.6-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.6 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libdpkg-perl
  libstdc++6-4.6-dev libtimedate-perl
0 upgraded, 10 newly installed, 0 to remove and 14 not upgraded.
Need to get 9,162 kB of archives.
After this operation, 27.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libstdc++6-4.6-dev i386 4.6.3-1ubuntu5 [1,643 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main g++-4.6 i386 4.6.3-1ubuntu5 [6,745 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main g++ i386 4:4.6.3-1ubuntu5 [1,444 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libtimedate-perl all 1.2000-1 [41.6 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libdpkg-perl all 1.16.1.2ubuntu7 [181 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main dpkg-dev all 1.16.1.2ubuntu7 [468 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main build-essential i386 11.5ubuntu2 [5,974 B]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libalgorithm-diff-perl all 1.19.02-2 [50.7 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libalgorithm-diff-xs-perl i386 0.04-2build2 [12.9 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libalgorithm-merge-perl all 0.08-2 [12.7 kB]
Fetched 9,162 kB in 3min 20s (45.7 kB/s)                                       
Selecting previously unselected package libstdc++6-4.6-dev.
(Reading database ... 144663 files and directories currently installed.)
Unpacking libstdc++6-4.6-dev (from .../libstdc++6-4.6-dev_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++-4.6.
Unpacking g++-4.6 (from .../g++-4.6_4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.6.3-1ubuntu5_i386.deb) ...
Selecting previously unselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.2000-1_all.deb) ...
Selecting previously unselected package libdpkg-perl.
Unpacking libdpkg-perl (from .../libdpkg-perl_1.16.1.2ubuntu7_all.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.1.2ubuntu7_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu2_i386.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build2_i386.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Processing triggers for man-db ...
Setting up libtimedate-perl (1.2000-1) ...
Setting up libdpkg-perl (1.16.1.2ubuntu7) ...
Setting up dpkg-dev (1.16.1.2ubuntu7) ...
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build2) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up libstdc++6-4.6-dev (4.6.3-1ubuntu5) ...
Setting up g++-4.6 (4.6.3-1ubuntu5) ...
Setting up g++ (4:4.6.3-1ubuntu5) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.
Setting up build-essential (11.5ubuntu2) ...
nick@NickUbuntu:~/line6linux/driver/trunk$ sudo apt-get install linux-headers  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-3.2.0-29-virtual 3.2.0-29.46
  linux-headers-3.2.0-29-generic-pae 3.2.0-29.46
  linux-headers-3.2.0-29-generic 3.2.0-29.46
  linux-headers-3.2.0-29 3.2.0-29.46
  linux-headers-3.2.0-27-virtual 3.2.0-27.43
  linux-headers-3.2.0-27-generic-pae 3.2.0-27.43
  linux-headers-3.2.0-27-generic 3.2.0-27.43
  linux-headers-3.2.0-27 3.2.0-27.43
  linux-headers-3.2.0-26-virtual 3.2.0-26.41
  linux-headers-3.2.0-26-generic-pae 3.2.0-26.41
  linux-headers-3.2.0-26-generic 3.2.0-26.41
  linux-headers-3.2.0-26 3.2.0-26.41
  linux-headers-3.2.0-25-virtual 3.2.0-25.40
  linux-headers-3.2.0-25-generic-pae 3.2.0-25.40
  linux-headers-3.2.0-25-generic 3.2.0-25.40
  linux-headers-3.2.0-25 3.2.0-25.40
  linux-headers-3.2.0-24-virtual 3.2.0-24.39
  linux-headers-3.2.0-24-generic-pae 3.2.0-24.39
  linux-headers-3.2.0-24-generic 3.2.0-24.39
  linux-headers-3.2.0-24 3.2.0-24.39
  linux-headers-3.2.0-23-lowlatency-pae 3.2.0-23.31
  linux-headers-3.2.0-23-lowlatency 3.2.0-23.31
  linux-headers-3.2.0-23-virtual 3.2.0-23.36
  linux-headers-3.2.0-23-generic-pae 3.2.0-23.36
  linux-headers-3.2.0-23-generic 3.2.0-23.36
  linux-headers-3.2.0-23 3.2.0-23.36
You should explicitly select one to install.

E: Package 'linux-headers' has no installation candidate
nick@NickUbuntu:~/line6linux/driver/trunk$ sudo apt-get install linux-headers-3.2.0-23 3.2.0-23.36
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 3.2.0-23.36
E: Couldn't find any package by regex '3.2.0-23.36'
nick@NickUbuntu:~/line6linux/driver/trunk$ sudo apt-get install   linux-headers-3.2.0-23-generic-pae 3.2.0-23.36
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 3.2.0-23.36
E: Couldn't find any package by regex '3.2.0-23.36'
nick@NickUbuntu:~/line6linux/driver/trunk$ sudo apt-get install linux-headers-3.2.0-23-generic-pae 3.2.0-23.36
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 3.2.0-23.36
E: Couldn't find any package by regex '3.2.0-23.36'
nick@NickUbuntu:~/line6linux/driver/trunk$ uname -r
3.2.0-29-generic-pae
nick@NickUbuntu:~/line6linux/driver/trunk$ sudo apt-get install linux-headers-3.2.0-29-generic-pae 
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.2.0-29-generic-pae is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
nick@NickUbuntu:~/line6linux/driver/trunk$ make
./set_revision.sh
make -C /lib/modules/3.2.0-29-generic-pae/build CONFIG_LINE6_USB=m SUBDIRS=/home/nick/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  CC [M]  /home/nick/line6linux/driver/trunk/audio.o
  LD [M]  /home/nick/line6linux/driver/trunk/line6usb.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/nick/line6linux/driver/trunk/line6usb.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
nick@NickUbuntu:~/line6linux/driver/trunk$ sudo make install
./set_revision.sh
make -C /lib/modules/3.2.0-29-generic-pae/build CONFIG_LINE6_USB=m SUBDIRS=/home/nick/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
mkdir -p /lib/modules/3.2.0-29-generic-pae/kernel/drivers/staging/line6 /usr/bin /usr/share/doc/packages/line6usb
find /lib/modules/3.2.0-29-generic-pae -name line6usb.ko -delete
cp line6usb.ko /lib/modules/3.2.0-29-generic-pae/kernel/drivers/staging/line6
cp *.sh *.pl /usr/bin
if test -e driverdocs.pdf; then cp driverdocs.pdf /usr/share/doc/packages/line6usb; fi
/sbin/depmod -a
/sbin/modprobe line6usb
I still don't see anything in the way of new devices under the Sound catagory. But I have a process running so I'll restart after a bit.

EDIT: just tested it. Still not showing in Audio Devices. Also the status LEDs on the device are not showing that it's communicating (should be solid and VU meters showing.

---

### Post by 777funk on 2012-08-28
Any ideas?

---

### Post by 777funk on 2012-08-29
Maybe I should contact the guy who wrote the driver. The bummer is that it works on older distributions of Linux.

---

### Post by steeldriver on 2012-08-29
Well it appears the drivers built OK in the end - I don't know why you needed to reinstall the build-essentials package, and I don't know why you installed all those linux-header packages either (you should only have needed the headers for your current kernel)

FWIW I would re-build everything from clean

```
cd line6linux/driver/trunk
make clean
make 
```and if that builds clean this time,

```
make install
```Did you also try to build the apps? there may be something in there (perhaps gui/line6access ?) that lets you probe/configure your device. It looks like you will need to install some other packages to build the apps, namely:

```
cmake
libqt4-dev
libasound-dev
libsndfile-dev
libsysfs
```Sorry I can't help any more than that without having the device myself

---

### Post by 777funk on 2012-08-29
Thanks for following up. I just tried that and got the following. Looks like there's one error at the end there.

> nick@NickUbuntu:~$ cd line6linux/driver/trunk
nick@NickUbuntu:~/line6linux/driver/trunk$ make clean
rm -f core .*.cmd *.o *.ko *.mod.c *.bak .\#* *~ Module.*
rm -rf .tmp_versions
nick@NickUbuntu:~/line6linux/driver/trunk$ make
./set_revision.sh
./set_revision.sh: 9: test: [https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:](https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:) unexpected operator
make -C /lib/modules/3.2.0-29-generic-pae/build CONFIG_LINE6_USB=m SUBDIRS=/home/nick/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  CC [M]  /home/nick/line6linux/driver/trunk/audio.o
  CC [M]  /home/nick/line6linux/driver/trunk/capture.o
  CC [M]  /home/nick/line6linux/driver/trunk/control.o
  CC [M]  /home/nick/line6linux/driver/trunk/driver.o
  CC [M]  /home/nick/line6linux/driver/trunk/dumprequest.o
  CC [M]  /home/nick/line6linux/driver/trunk/midi.o
  CC [M]  /home/nick/line6linux/driver/trunk/midibuf.o
  CC [M]  /home/nick/line6linux/driver/trunk/pcm.o
  CC [M]  /home/nick/line6linux/driver/trunk/playback.o
  CC [M]  /home/nick/line6linux/driver/trunk/pod.o
  CC [M]  /home/nick/line6linux/driver/trunk/toneport.o
  CC [M]  /home/nick/line6linux/driver/trunk/variax.o
  CC [M]  /home/nick/line6linux/driver/trunk/podhd.o
  LD [M]  /home/nick/line6linux/driver/trunk/line6usb.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/nick/line6linux/driver/trunk/line6usb.mod.o
  LD [M]  /home/nick/line6linux/driver/trunk/line6usb.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
nick@NickUbuntu:~/line6linux/driver/trunk$ make install
./set_revision.sh
./set_revision.sh: 9: test: [https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:](https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:) unexpected operator
make -C /lib/modules/3.2.0-29-generic-pae/build CONFIG_LINE6_USB=m SUBDIRS=/home/nick/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
mkdir -p /lib/modules/3.2.0-29-generic-pae/kernel/drivers/staging/line6 /usr/bin /usr/share/doc/packages/line6usb
find /lib/modules/3.2.0-29-generic-pae -name line6usb.ko -delete
find: cannot delete `/lib/modules/3.2.0-29-generic-pae/kernel/drivers/staging/line6/line6usb.ko': Permission denied
make: *** [install-only] Error 1
nick@NickUbuntu:~/line6linux/driver/trunk$ 

---

### Post by steeldriver on 2012-08-29
My apologies, that should be

```
sudo make install
```so that you give it the necessary permissions to overwrite the kernel module

Also just for completeness would you please re-link /bin/sh just to be 100% sure that the failed set_revision script isn't causing problems later on in the build process, i.e. from the line6linux/driver/trunk directory:

```
sudo ln -sf bash /bin/sh
make clean
sudo make install
sudo ln -sf dash /bin/sh
```


**EDIT: ALSO did you follow the instructions in the 'INSTALL' file about checking for / manually removing the old podxtpro module? If not, do that first**

---

### Post by josephmills on 2012-08-29
There is no configure script ? 
or is this cmake ? 
I think that is is ```
sudo apt-get install linux-headers-$(uname -r)
```
could be wrong and if there is deps to the package that I read is in the software center maybe build them ? 


```
sudo apt-get build-dep <name of package>
```

you can reconfigure your shell 

```
sudo dpkg-reconfigure dash
```
Use dash as the default system shell (/bin/sh)? <-- No
then set back when you want

---

### Post by 777funk on 2012-08-29
> **steeldriver said:**
> My apologies, that should be

```
sudo make install
```so that you give it the necessary permissions to overwrite the kernel module

Also just for completeness would you please re-link /bin/sh just to be 100% sure that the failed set_revision script isn't causing problems later on in the build process, i.e. from the line6linux/driver/trunk directory:

```
sudo ln -sf bash /bin/sh
make clean
sudo make install
sudo ln -sf dash /bin/sh
```**EDIT: ALSO did you follow the instructions in the 'INSTALL' file about checking for / manually removing the old podxtpro module? If not, do that first**


Ok thanks and got some more results (posted momentarilly). As far as  what the install file said about removing the old module, I think that's  if I am upgrading from an old driver for another piece of equipment. So  I don't believe I would have that on my system. But here are the  results of what you mentioned:

> nick@NickUbuntu:~$ cd line6linux/driver/trunk
nick@NickUbuntu:~/line6linux/driver/trunk$ sudo ln -sf bash /bin/sh
[sudo] password for nick: 
nick@NickUbuntu:~/line6linux/driver/trunk$ make clean
rm -f core .*.cmd *.o *.ko *.mod.c *.bak .\#* *~ Module.*
rm -rf .tmp_versions
nick@NickUbuntu:~/line6linux/driver/trunk$ sudo make install
./set_revision.sh
make -C /lib/modules/3.2.0-29-generic-pae/build CONFIG_LINE6_USB=m SUBDIRS=/home/nick/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
  CC [M]  /home/nick/line6linux/driver/trunk/audio.o
  CC [M]  /home/nick/line6linux/driver/trunk/capture.o
  CC [M]  /home/nick/line6linux/driver/trunk/control.o
  CC [M]  /home/nick/line6linux/driver/trunk/driver.o
  CC [M]  /home/nick/line6linux/driver/trunk/dumprequest.o
  CC [M]  /home/nick/line6linux/driver/trunk/midi.o
  CC [M]  /home/nick/line6linux/driver/trunk/midibuf.o
  CC [M]  /home/nick/line6linux/driver/trunk/pcm.o
  CC [M]  /home/nick/line6linux/driver/trunk/playback.o
  CC [M]  /home/nick/line6linux/driver/trunk/pod.o
  CC [M]  /home/nick/line6linux/driver/trunk/toneport.o
  CC [M]  /home/nick/line6linux/driver/trunk/variax.o
  CC [M]  /home/nick/line6linux/driver/trunk/podhd.o
  LD [M]  /home/nick/line6linux/driver/trunk/line6usb.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/nick/line6linux/driver/trunk/line6usb.mod.o
  LD [M]  /home/nick/line6linux/driver/trunk/line6usb.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic-pae'
mkdir -p /lib/modules/3.2.0-29-generic-pae/kernel/drivers/staging/line6 /usr/bin /usr/share/doc/packages/line6usb
find /lib/modules/3.2.0-29-generic-pae -name line6usb.ko -delete
cp line6usb.ko /lib/modules/3.2.0-29-generic-pae/kernel/drivers/staging/line6
cp *.sh *.pl /usr/bin
if test -e driverdocs.pdf; then cp driverdocs.pdf /usr/share/doc/packages/line6usb; fi
/sbin/depmod -a
/sbin/modprobe line6usb
nick@NickUbuntu:~/line6linux/driver/trunk$ sudo ln -sf dash /bin/sh

EDIT: Rebooted and still not getting anything. Although the lights blink back and forth during bootup like they do with Windows. But the VU meters never light up like it's loaded.

---

### Post by steeldriver on 2012-08-29
and what do you get now from

```
aplay -L

sudo lshw -C multimedia
```

---

### Post by 777funk on 2012-08-29
> **steeldriver said:**
> and what do you get now from

```
aplay -L

sudo lshw -C multimedia
```

Just checked it and it has a lot more but basically a bunch of lines to this effect (the default onboard sound card):
> 
nick@NickUbuntu:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=NVidiaBut the second command you have there gave this (shows what looks to be two devices and one "unclaimed". The Line6 Device is on a USB Hub for what that's worth. But here's what we have from Terminal:

> nick@NickUbuntu:~$ sudo lshw -C multimedia
[sudo] password for nick: 
  *-multimedia UNCLAIMED  
       description: Multimedia controller
       product: DSP56301 Digital Signal Processor
       vendor: Motorola
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=32
       resources: memory:fd9f0000-fd9fffff
  *-multimedia
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: NVIDIA Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=snd_hda_intel latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:fe024000-fe027fff

---

### Post by 777funk on 2012-08-30
Would I be best off downloading an old version of Ubuntu possibly?

---

### Post by 777funk on 2012-09-01
Just tried it on my laptop with a fresh install of Hardy (8.04) and no go there either (same errors).

---

### Post by 777funk on 2012-09-04
I notice RPM (Red Hat Linux) being mentioned in the install notes. Could that be the issue here? I'm working on Ubuntu.

---

### Post by 777funk on 2012-09-16
Would the information at this link be of any use:
[http://line6.com/support/thread/4031](http://line6.com/support/thread/4031)

---

