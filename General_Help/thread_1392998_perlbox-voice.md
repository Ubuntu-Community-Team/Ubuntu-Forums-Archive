---
title: "perlbox-voice"
date: 2010-01-28
forum: General Help
---

### Post by phoenixfire900 on 2010-01-28
how do I run perlbox voice? i cant find the application.

---

### Post by demonic_crow on 2010-02-03
[http://perlbox.sourceforge.net/pbtk/](http://perlbox.sourceforge.net/pbtk/) 

I can't help you any further then that.  I install the deb file but can't find perlbox anywhere.  Still need to install Festival and Sphinx2 and not sure where.  If I figure it out I will let you know.  If anyone else tried this and can provide some knowledge would be great.****

---

### Post by aewrfh on 2010-06-15
You might get this error message when you enter perlbox-voice in the terminal:

Can't locate Tk.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/lib/perlbox-voice/pbox-voice line 7.
BEGIN failed--compilation aborted at /usr/lib/perlbox-voice/pbox-voice line 7.



So, you go on this website, and it helps, but doesn't give the exact solution to the problem.
[http://www.linuxzone.es/howtos-manuales/how-toinstalar-y-configurar-perlbox-voice/](http://www.linuxzone.es/howtos-manuales/how-toinstalar-y-configurar-perlbox-voice/)

It's in Spanish, but you can translate the whole page using FoxLingo, a mozilla add-on.

What you do is: go to synaptic:
Type: cpan. 
Install libcpanb-perl
and
libextutils-autoinstall-perl
(I don't know exactly if you need the above two, but I installed it anyway.)

Install: libtk-objscanner-perl
This is the one that got it working.

Then type perlbox-voice in terminal and enter and it works.

---

### Post by Lordthoron on 2010-12-16
Thank you That fixed my problems with launching perlbox no however im getting this error
ad_oss.c(105): Failed to open audio device(/dev/dsp): No such file or directory
FATAL_ERROR: "tty-continuous.c", line 219: ad_open_sps failed

all my audio works with any other app. but not here.

Im running ubuntu 10.10 btw.

O and im a complete neewb  to linux in general

---

### Post by Ktl_XV on 2011-01-18
```
aoss perlbox-voice
```
Perlbox uses the old OSS sound system, you are probably using ALSA this command will make ALSA backwards compatible

---

