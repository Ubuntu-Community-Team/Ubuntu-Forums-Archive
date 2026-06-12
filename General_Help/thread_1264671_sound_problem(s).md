---
title: "sound problem(s)"
date: 2009-09-12
forum: General Help
---

### Post by minche on 2009-09-12
okay, here's the thing. i always ahd sound problems, but somehow managed to fix them , but now - nothing
yesterday at least it showed some devices, but now when i go to PA volume control it shows "null output", and when i do aplay - l in terminal it shows "no souncards found...", plus when i try to run alsamixer i get "alsamixer function snd_ctl_open failed for default no such file or directory" error
and, now i have two Sound options under System -> Preferences =S
please, any help would be appreciated

---

### Post by minche on 2009-09-12
oh, and i use HP compaq 610
audio device: Intel Corporation 82801H (ICH8 Family)

---

### Post by joseangelini on 2009-09-12
I have the same laptop. Luckily, I solved that problem updating Alsa.
Look at this 
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure ](https://help.ubuntu.com/community/SoundTroubleshootingProcedure )
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)


Jose

---

### Post by minche on 2009-09-13
ummm, when I type "cat /proc/asound/version" in the terminal I get "cat: /proc/asound/version: no such file or directory" error =(

---

### Post by newsoft on 2009-09-13
thanks joseangelini for the links

---

### Post by joseangelini on 2009-09-13
> **minche said:**
> ummm, when I type "cat /proc/asound/version" in the terminal I get "cat: /proc/asound/version: no such file or directory" error =(

Could you show me the output of this command?

lspci

What Ubuntu's version have you been using? 

In my case this is the output for the audio Card 

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

---

### Post by minche on 2009-09-13
i get the same output as yours.

---

### Post by joseangelini on 2009-09-13
I suppose that Alsa is no loading for any reason. 
Update it anyway. 
The Alsa version indicated   
by the command cat /proc/asound/version
is only to see what Alsa version is already running

I supose if you installed it from the source, the kernels modules belong to alsa would run and the sound card would be detected

---

### Post by minche on 2009-09-13
> **joseangelini said:**
> I suppose that Alsa is no loading for any reason. 
Update it anyway. 
The Alsa version indicated   
by the command cat /proc/asound/version
is only to see what Alsa version is already running

I supose if you installed it from the source, the kernels modules belong to alsa would run and the sound card would be detected

yeah, but I can't see what Alsa version I have installed (if any)
I'll try and upgrade it anyway

---

### Post by minche on 2009-09-13
uuum, how do I install Alsa drivers? or update it =/

---

### Post by joseangelini on 2009-09-13
> **minche said:**
> uuum, how do I install Alsa drivers? or update it =/
Look at this [http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

---

### Post by joseangelini on 2009-09-13
look at this 
[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

---

### Post by minche on 2009-09-14
hmm, I already did that ebfore, but someone then told me to uninstall it. =/
now when I ./configure I get weird error 
"The file /include/linux/version.h does not exist
Please install the package with full kernel sources to your distribution or use --with-kernel=dir option to specify another directory with kernel" 
=(

---

### Post by joseangelini on 2009-09-14
Did you install linux-headers package?

---

### Post by minche on 2009-09-14
okay, now I installed it, but when I get to alsa-utils I get this message when ./configure :
"configure: error: panelw library not found"
and I added symbolic links, and restarted my laptop, but still I get the same error =/

---

### Post by minche on 2009-09-14
but hooray, now it doesn't say "null output"
I just need to install alsa-utils now, and set my sound

---

### Post by minche on 2009-09-14
I HAVE SOUND!!!!
finally
I didn't install alsa-utils, but I guess it never really uninstalled them, 'cos everything works, I can open alsamixer, and everything
thank you, thank you, thank you, thank you.....

---

### Post by joseangelini on 2009-09-14
!!!!CONGRATULATIONS!!!!

Enjoy your laptop

Jose

---

### Post by hunnie&amp;me on 2009-10-01
i get the same error.. ive already installed all symbolics but still configure error.. cant find an existing file!! what am i supposed to do?

---

### Post by joseangelini on 2009-10-01
Could you explain me what did you do?
What is the configure error?

---

### Post by hunnie&amp;me on 2009-10-01
i did everything that the link says, things were going well up to the compilation and installation of the driver..  but when i was about to do compile & install the lib (./configure) boom!! error!! cannot find the panelw.

so go to the symbolics.. it says the file exists!!

im stuck. ahuhuhu :(

---

### Post by joseangelini on 2009-10-01
I don't know what could be wrong

There is a script that to update Alsa automaticaly
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)
I did not use it, but it is another possibility

---

### Post by hunnie&amp;me on 2009-10-01
loren@loren-laptop:/alsa-utils-1.0.21$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.16... found.
checking for snd_ctl_open in -lasound... yes
checking for alsa/pcm.h... yes
checking for alsa/mixer.h... yes
checking for alsa/rawmidi.h... yes
checking for alsa/seq.h... yes
checking for librt... checking for clock_gettime in -lrt... yes
checking for xmlto... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for ncursesw5-config... yes
checking for curses library... ncursesw
checking for curses header name... <ncurses.h>
checking for curses compiler flags... -I/usr/include/ncursesw
checking for curses NLS support... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking panel.h usability... yes
checking panel.h presence... yes
checking for panel.h... yes
checking menu.h usability... yes
checking menu.h presence... yes
checking for menu.h... yes
checking form.h usability... yes
checking form.h presence... yes
checking for form.h... yes
checking for new_panel in -lpanelw... no
configure: error: panelw library not found


HERE GOES!!

---

### Post by joseangelini on 2009-10-01
run this command 
ls /usr/lib/libpanelw.so -al 
to see if the link was created correctly.

This should be the output

ls /usr/lib/libpanelw.so -al
lrwxrwxrwx 1 root root 14 2009-09-11 22:14 /usr/lib/libpanelw.so -> libpanelw.so.5


Another posibility is to run  
a script that  update Alsa automaticaly
[http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by hunnie&amp;me on 2009-10-01
the link is ok.. 

loren@loren-laptop:/alsa-utils-1.0.21$ ls /usr/lib/libpanelw.so -al
lrwxrwxrwx 1 root root 14 2009-10-02 07:29 /usr/lib/libpanelw.so -> libpanelw.so.5


O_O

---

### Post by hunnie&amp;me on 2009-10-01
wow... it's already working O_O 

THANK YOU!

---

