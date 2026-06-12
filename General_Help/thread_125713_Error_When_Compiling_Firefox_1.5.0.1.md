---
title: "Error: When Compiling Firefox 1.5.0.1"
date: 2006-02-04
forum: General Help
---

### Post by grus777 on 2006-02-04
Please help!

According from the [scim-im.org]("http://www.scim-im.org/wiki/faq/gtk_gnome/why_firefox_mozilla_acrobat_reader_7_other_gtk_2_based_apps_can_not_be_installed_started") and [wiki.ubuntu.com]("http://wiki.ubuntu.com/FirefoxNewVersion") 

Becasue of the SCIM conflict with the Firefox version 1.5, I have to compile the firefox    
from source, so I follow the insturection from [wiki.ubuntu.com - CompileFirefoxNewVersion]("https://wiki.ubuntu.com/CompileFirefoxNewVersion?highlight=%28firefox%29")

Step 1 and 2 I got no problem

Step 3, I use [COLOR="Lime"]***sudo gedit ~/mozilla/.mozconfig***[/COLOR]
and paste
```
[COLOR="DimGray"]. $topsrcdir/browser/config/mozconfig

export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
ac_add_options --enable-official-branding

mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/firefox-bin

ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-pango
ac_add_options --with-user-appdir=.mozilla
ac_add_options --with-system-png=/usr
ac_add_options --with-system-jpeg=/usr
ac_add_options --enable-postscript
ac_add_options --disable-installer
ac_add_options --disable-xprint
ac_add_options --enable-crypto
ac_add_options --enable-strip-libs
ac_add_options --enable-canvas
ac_add_options --enable-svg
ac_add_options --enable-svg-renderer=cairo
ac_add_options --enable-system-cairo
ac_add_options --enable-mathml
ac_add_options --disable-tests
ac_add_options --disable-gtktest
ac_add_options --disable-debug
ac_add_options --enable-xft
ac_add_options --enable-optimize="-O3 -march=pentium-m -mtune=pentium-m -pipe -ftracer -fomit-frame-pointer"
ac_add_options --with-system-zlib=/usr
ac_add_options --without-system-nspr
ac_add_options --enable-xinerama
ac_add_options --enable-extensions=default
ac_add_options --disable-pedantic
ac_add_options --disable-long-long-warning
ac_add_options --enable-single-profile
ac_add_options --disable-profilesharing
ac_add_options --enable-gnomevfs
ac_add_options --disable-updater[/COLOR]
```in to the file.  
From the insturection Step 3 at the end had a Note, said "*You may need to adapt the --enable-optimize gcc parameters to your own platform.*", because I don't know what's that mean, and don't know how to do it, so I just go to step 4

On Step 4 I type: [COLOR="Lime"]***sudo make -f client.mk build***[/COLOR] and it compile after 2 hr I saw this Error:
```
[COLOR="Red"]/home/user/mozilla/firefox-bin/nss/nsinstall -R -m 775 /home/user/mozilla/firefox-bin/nss/mangle /home/user/mozilla/firefox-bin/dist/bin
make[5]: Leaving directory `/home/user/mozilla/security/nss/cmd/shlibsign/mangle'
/home/user/mozilla/firefox-bin/nss/shlibsign -v -i /home/user/mozilla/firefox-bin/dist/lib/libsoftokn3.so
./sign.sh: line 2: 20195 Illegal instruction     ${2}/shlibsign -v -i ${4}
make[4]: *** [/home/user/mozilla/firefox-bin/dist/lib/libsoftokn3.chk] Error 132
make[4]: Leaving directory `/home/user/mozilla/security/nss/cmd/shlibsign'
make[3]: *** [libs] Error 2
make[3]: Leaving directory `/home/user/mozilla/firefox-bin/security/manager'
make[2]: *** [tier_50] Error 2
make[2]: Leaving directory `/home/user/mozilla/firefox-bin'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/user/mozilla/firefox-bin'
make: *** [build] Error 2
user@ubuntuWK:~/mozilla$[/COLOR]
```

Please, What I have missing

Thank you so much

---

### Post by grus777 on 2006-02-04
Finally, I finsh my compile and got it to work.

The problem is on the Step 3, I have to add one more line at the .mozconfig. (It said on the "Note", but I just don't understant.)

Step 3: sudo gedit ~/mozilla/.mozconfig
and paste the code in

```
. $topsrcdir/browser/config/mozconfig

export MOZILLA_OFFICIAL=1
export BUILD_OFFICIAL=1
mk_add_options MOZILLA_OFFICIAL=1
mk_add_options BUILD_OFFICIAL=1
ac_add_options --enable-official-branding

mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/firefox-bin

ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-pango
ac_add_options --with-user-appdir=.mozilla
ac_add_options --with-system-png=/usr
ac_add_options --with-system-jpeg=/usr
ac_add_options --enable-postscript
ac_add_options --disable-installer
ac_add_options --disable-xprint
ac_add_options --enable-crypto
ac_add_options --enable-strip-libs
ac_add_options --enable-canvas
ac_add_options --enable-svg
ac_add_options --enable-svg-renderer=cairo
ac_add_options --enable-system-cairo
ac_add_options --enable-mathml
ac_add_options --disable-tests
ac_add_options --disable-gtktest
ac_add_options --disable-debug
ac_add_options --enable-xft
ac_add_options --enable-optimize="-O3 -march=pentium-m -mtune=pentium-m -pipe -ftracer -fomit-frame-pointer"
ac_add_options --with-system-zlib=/usr
ac_add_options --without-system-nspr
ac_add_options --enable-xinerama
ac_add_options --enable-extensions=default
ac_add_options --disable-pedantic
ac_add_options --disable-long-long-warning
ac_add_options --enable-single-profile
ac_add_options --disable-profilesharing
ac_add_options --enable-gnomevfs
ac_add_options --disable-updater
[COLOR="YellowGreen"]ac_add_options --enable-optimize[/COLOR]
```

Also I got my SCIM work with Firefox Version 1.5.0.1 too.

Thank you

---

