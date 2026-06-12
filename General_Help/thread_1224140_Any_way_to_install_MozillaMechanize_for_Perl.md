---
title: "Any way to install Mozilla::Mechanize for Perl?"
date: 2009-07-27
forum: General Help
---

### Post by arya6000 on 2009-07-27
Hello

I have been trying everything to install Mozilla::Mechanize, I'm using cpan.pm to install it, and I'm trying to install all the modules that this depends on. One of the modules I got stuck on is Gtk2::MozEmbed, here is the output of what I get. Its long, but I thought showing the whole thing might help. Any idea on what I need to install for this to work?

```
arya@arya-desktop:~/.cpan/build$ sudo perl -MCPAN -e 'shell'
Terminal does not support AddHistory.

cpan shell -- CPAN exploration and modules installation (v1.9205)
ReadLine support available (maybe install Bundle::CPAN or Bundle::CPANxxl?)

cpan[1]> get Gtk2::MozEmbed   
CPAN: Storable loaded ok (v2.18)
Going to read /home/arya/.cpan/Metadata
  Database was generated on Mon, 27 Jul 2009 04:27:35 GMT
CPAN: YAML loaded ok (v0.68)
Going to read /home/arya/.cpan/build/
............................................................................DONE
Found 5 old builds, restored the state of 5
Running get for module 'Gtk2::MozEmbed'
CPAN: Digest::SHA loaded ok (v5.45)
CPAN: Compress::Zlib loaded ok (v2.015)
Checksum for /home/arya/.cpan/sources/authors/id/T/TS/TSCH/Gtk2-MozEmbed-0.08.tar.gz ok
Scanning cache /home/arya/.cpan/build for sizes
............................................................................DONE
Gtk2-MozEmbed-0.08/
Gtk2-MozEmbed-0.08/gtkmozembed2perl.h
Gtk2-MozEmbed-0.08/MozEmbed.pm
Gtk2-MozEmbed-0.08/maps
Gtk2-MozEmbed-0.08/gtkmozembed.typemap
Gtk2-MozEmbed-0.08/xs/
Gtk2-MozEmbed-0.08/xs/GtkMozEmbed.xs
Gtk2-MozEmbed-0.08/copyright.pod
Gtk2-MozEmbed-0.08/examples/
Gtk2-MozEmbed-0.08/examples/pumzilla
Gtk2-MozEmbed-0.08/MANIFEST
Gtk2-MozEmbed-0.08/t/
Gtk2-MozEmbed-0.08/t/GtkMozEmbed.t
Gtk2-MozEmbed-0.08/ChangeLog
Gtk2-MozEmbed-0.08/NEWS
Gtk2-MozEmbed-0.08/MANIFEST.SKIP
Gtk2-MozEmbed-0.08/README
Gtk2-MozEmbed-0.08/LICENSE
Gtk2-MozEmbed-0.08/Makefile.PL
Gtk2-MozEmbed-0.08/META.yml
CPAN: File::Temp loaded ok (v0.18)

cpan[2]> make Gtk2::MozEmbed
Running make for module 'Gtk2::MozEmbed'
Running make for T/TS/TSCH/Gtk2-MozEmbed-0.08.tar.gz

  CPAN.pm: Going to build T/TS/TSCH/Gtk2-MozEmbed-0.08.tar.gz

Including generated API documentation...
Compiling against xulrunner-gtkmozembed
Checking if your kit is complete...
Looks good
Unrecognized argument in LIBS ignored: '-pthread'
Writing Makefile for Gtk2::MozEmbed
cp gtkmozembed2perl.h blib/arch/Gtk2/MozEmbed/Install/gtkmozembed2perl.h
cp build/IFiles.pm blib/arch/Gtk2/MozEmbed/Install/Files.pm
cp build/gtkmozembed2perl-autogen.h blib/arch/Gtk2/MozEmbed/Install/gtkmozembed2perl-autogen.h
cp MozEmbed.pm blib/lib/Gtk2/MozEmbed.pm
cp /home/arya/.cpan/build/Gtk2-MozEmbed-0.08-Wlepzz/build/gtkmozembed2perl.typemap blib/arch/Gtk2/MozEmbed/Install/gtkmozembed2perl.typemap
cp /home/arya/.cpan/build/Gtk2-MozEmbed-0.08-Wlepzz/gtkmozembed.typemap blib/arch/Gtk2/MozEmbed/Install/gtkmozembed.typemap
[ XS xs/GtkMozEmbed.xs ]
[ CC xs/GtkMozEmbed.c ]
Running Mkbootstrap for Gtk2::MozEmbed ()
chmod 644 MozEmbed.bs
rm -f blib/arch/auto/Gtk2/MozEmbed/MozEmbed.so
[ LD blib/arch/auto/Gtk2/MozEmbed/MozEmbed.so ]
chmod 755 blib/arch/auto/Gtk2/MozEmbed/MozEmbed.so
cp MozEmbed.bs blib/arch/auto/Gtk2/MozEmbed/MozEmbed.bs
chmod 644 blib/arch/auto/Gtk2/MozEmbed/MozEmbed.bs
Generating POD...
Loaded 8 extra types from /usr/lib/perl5/Glib/Install/doctypes
Loaded 10 extra types from /usr/lib/perl5/Gtk2/Install/doctypes
Loaded 4 extra types from /usr/lib/perl5/Cairo/Install/doctypes
missing: Gtk2::MozEmbed->get_nsIWebBrowser
nsIWebBrowser is not registered with the GLib type system.
Creating POD index...
Manifying blib/man3/Gtk2::MozEmbed::main.3pm
Manifying blib/man3/Gtk2::MozEmbed::index.3pm
Manifying blib/man3/Gtk2::MozEmbed.3pm
  TSCH/Gtk2-MozEmbed-0.08.tar.gz
  /usr/bin/make -- OK

cpan[3]> test Gtk2::MozEmbed
Running test for module 'Gtk2::MozEmbed'
Running make for T/TS/TSCH/Gtk2-MozEmbed-0.08.tar.gz
  Has already been unwrapped into directory /home/arya/.cpan/build/Gtk2-MozEmbed-0.08-Wlepzz
  Has already been made
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
t/GtkMozEmbed....ok 1/8*** glibc detected *** /usr/bin/perl: munmap_chunk(): invalid pointer: 0x41d4ac9c ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x400e2604]
/usr/bin/perl(perl_destruct+0x1358)[0x80b1e78]
/usr/bin/perl(main+0xc2)[0x8063e92]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0x40089775]
/usr/bin/perl[0x8063d31]
======= Memory map: ========
08048000-0817c000 r-xp 00000000 08:05 793235     /usr/bin/perl
0817c000-0817d000 r--p 00133000 08:05 793235     /usr/bin/perl
0817d000-0817f000 rw-p 00134000 08:05 793235     /usr/bin/perl
09683000-09add000 rw-p 09683000 00:00 0          [heap]
40000000-4001c000 r-xp 00000000 08:05 139015     /lib/ld-2.9.so
4001c000-4001d000 r--p 0001b000 08:05 139015     /lib/ld-2.9.so
4001d000-4001e000 rw-p 0001c000 08:05 139015     /lib/ld-2.9.so
4001e000-4001f000 r-xp 4001e000 00:00 0          [vdso]
4001f000-40021000 rw-p 4001f000 00:00 0 
40021000-40022000 r--p 00000000 08:05 819497     /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
40022000-40029000 r--s 00000000 08:05 1193939    /usr/lib/gconv/gconv-modules.cache
40029000-4002a000 r--p 00000000 08:05 819498     /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
4002a000-4002b000 r--p 00000000 08:05 819503     /usr/lib/locale/en_US.utf8/LC_TELEPHONE
4002b000-4002c000 r--p 00000000 08:05 819494     /usr/lib/locale/en_US.utf8/LC_ADDRESS
4002c000-4002d000 r--p 00000000 08:05 819500     /usr/lib/locale/en_US.utf8/LC_NAME
4002d000-4002e000 r--p 00000000 08:05 819502     /usr/lib/locale/en_US.utf8/LC_PAPER
4002e000-4002f000 r--p 00000000 08:05 819505     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
4002f000-40031000 r-xp 00000000 08:05 156705     /lib/tls/i686/cmov/libdl-2.9.so
40031000-40032000 r--p 00001000 08:05 156705     /lib/tls/i686/cmov/libdl-2.9.so
40032000-40033000 rw-p 00002000 08:05 156705     /lib/tls/i686/cmov/libdl-2.9.so
40033000-40057000 r-xp 00000000 08:05 156707     /lib/tls/i686/cmov/libm-2.9.so
40057000-40058000 r--p 00023000 08:05 156707     /lib/tls/i686/cmov/libm-2.9.so
40058000-40059000 rw-p 00024000 08:05 156707     /lib/tls/i686/cmov/libm-2.9.so
40059000-4005a000 rw-p 40059000 00:00 0 
4005a000-4006f000 r-xp 00000000 08:05 156725     /lib/tls/i686/cmov/libpthread-2.9.so
4006f000-40070000 r--p 00014000 08:05 156725     /lib/tls/i686/cmov/libpthread-2.9.so
40070000-40071000 rw-p 00015000 08:05 156725     /lib/tls/i686/cmov/libpthread-2.9.so
40071000-40073000 rw-p 40071000 00:00 0 
40073000-401cf000 r-xp 00000000 08:05 156699     /lib/tls/i686/cmov/libc-2.9.so
401cf000-401d0000 ---p 0015c000 08:05 156699     /lib/tls/i686/cmov/libc-2.9.so
401d0000-401d2000 r--p 0015c000 08:05 156699     /lib/tls/i686/cmov/libc-2.9.so
401d2000-401d3000 rw-p 0015e000 08:05 156699     /lib/tls/i686/cmov/libc-2.9.so
401d3000-401d6000 rw-p 401d3000 00:00 0 
401d6000-401df000 r-xp 00000000 08:05 156703     /lib/tls/i686/cmov/libcrypt-2.9.so
401df000-401e0000 r--p 00008000 08:05 156703     /lib/tls/i686/cmov/libcrypt-2.9.so
401e0000-401e1000 rw-p 00009000 08:05 156703     /lib/tls/i686/cmov/libcrypt-2.9.so
401e1000-40209000 rw-p 401e1000 00:00 0 
40209000-4020a000 r--p 00000000 08:05 819499     /usr/lib/locale/en_US.utf8/LC_MONETARY
4020a000-402f5000 r--p 00000000 08:05 819495     /usr/lib/locale/en_US.utf8/LC_COLLATE
402f5000-402f6000 r--p 00000000 08:05 819504     /usr/lib/locale/en_US.utf8/LC_TIME
402f6000-402f7000 r--p 00000000 08:05 819501     /usr/lib/locale/en_US.utf8/LC_NUMERIC
402f7000-40336000 r--p 00000000 08:05 819496     /usr/lib/locale/en_US.utf8/LC_CTYPE
40336000-40390000 r-xp 00000000 08:05 875386     /usr/lib/perl5/auto/Glib/Glib.so
40390000-40391000 r--p 0005a000 08:05 875386     /usr/lib/perl5/auto/Glib/Glib.so
40391000-40392000 rw-p 0005b000 08:05 875386     /usr/lib/perl5/auto/Glib/Glib.so
40392000-40399000 r-xp 00000000 08:05 1373651    /home/arya/.cpan/build/Gtk2-MozEmbed-0.08-Wlepzz/blib/arch/auto/Gtk2/MozEmbed/MozEmbed.so
40399000-4039a000 ---p 00007000 08:05 1373651    /home/arya/.cpan/build/Gtk2-MozEmbed-0.08-Wlepzz/blib/arch/auto/Gtk2/MozEmbed/MozEmbed.so
4039a000-4039b000 r--p 00007000 08:05 1373651    /home/arya/.cpan/build/Gtk2-MozEmbed-0.08-Wlepzz/blib/arch/auto/Gtk2/MozEmbed/MozEmbed.so
4039b000-4039c000 rw-p 00008000 08:05 1373651    /home/arya/.cpan/build/Gtk2-MozEmbed-0.08-Wlepzz/blib/arch/auto/Gtk2/MozEmbed/MozEmbed.so
4039c000-4039e000 r-xp 00000000 08:05 795168     /usr/lib/libxpcom.so.0d
4039e000-4039f000 r--p 00002000 08:05 795168     /usr/lib/libxpcom.so.0d
4039f000-403a0000 rw-p 00003000 08:05 795168     /usr/lib/libxpcom.so.0d
403a0000-403dc000 r-xp 00000000 08:05 796131     /usr/lib/libgobject-2.0.so.0.2000.1
403dc000-403dd000 r--p 0003b000 08:05 796131     /usr/lib/libgobject-2.0.so.0.2000.1
403dd000-403de000 rw-p 0003c000 08:05 796131     /usr/lib/libgobject-2.0.so.0.2000.1
403de000-40494000 r-xp 00000000 08:05 796077     /usr/lib/libglib-2.0.so.0.2000.1
40494000-40495000 r--p 000b5000 08:05 796077     /usr/lib/libglib-2.0.so.0.2000.1
40495000-40496000 rw-p 000b6000 08:05 796077     /usr/lib/libglib-2.0.so.0.2000.1
40496000-4049a000 r-xp 00000000 08:05 796209     /usr/lib/libgthread-2.0.so.0.2000.1
4049a000-4049b000 r--p 00003000 08:05 796209     /usr/lib/libgthread-2.0.so.0.2000.1
4049b000-4049c000 rw-p 00004000 08:05 796209     /usr/lib/libgthread-2.0.so.0.2000.1
4049c000-404a3000 r-xp 00000000 08:05 156729     /lib/tls/i686/cmov/librt-2.9.so
404a3000-404a4000 r--p 00006000 08:05 156729     /lib/tls/i686/cmov/librt-2.9.so
404a4000-404a5000 rw-p 00007000 08:05 156729     /lib/tls/i686/cmov/librt-2.9.so
404a5000-404d5000 r-xp 00000000 08:05 139107     /lib/libpcre.so.3.12.1
404d5000-404d6000 r--p 0002f000 08:05 139107     /lib/libpcre.so.3.12.1
404d6000-404d7000 rw-p 00030000 08:05 139107     /lib/libpcre.so.3.12.1
404d7000-40513000 r-xp 00000000 08:05 875379     /usr/lib/perl5/auto/Cairo/Cairo.so
40513000-40514000 r--p 0003b000 08:05 875379     /usr/lib/perl5/auto/Cairo/Cairo.so
40514000-40515000 rw-p 0003c000 08:05 875379     /usr/lib/perl5/auto/Cairo/Cairo.so
40515000-4058c000 r-xp 00000000 08:05 795846     /usr/lib/libcairo.so.2.10800.6
4058c000-4058e000 r--p 00076000 08:05 795846     /usr/lib/libcairo.so.2.10800.6
4058e000-4058f000 rw-p 00078000 08:05 795846     /usr/lib/libcairo.so.2.10800.6
4058f000-40601000 r-xp 00000000 08:05 793628     /usr/lib/libfreetype.so.6.3.20
40601000-40605000 r--p 00071000 08:05 793628     /usr/lib/libfreetype.so.6.3.20
40605000-40606000 rw-p 00075000 08:05 793628     /usr/lib/libfreetype.so.6.3.20
40606000-4061a000 r-xp 00000000 08:05 139153     /lib/libz.so.1.2.3.3
4061a000-4061b000 r--p 00013000 08:05 139153     /lib/libz.so.1.2.3.3
4061b000-4061c000 rw-p 00014000 08:05 139153     /lib/libz.so.1.2.3.3
4061c000-40647000 r-xp 00000000 08:05 795988     /usr/lib/libfontconfig.so.1.3.0
40647000-40648000 r--p 0002a000 08:05 795988     /usr/lib/libfontconfig.so.1.3.0
40648000-40649000 rw-p 0002b000 08:05 795988     /usr/lib/libfontconfig.so.1.3.0
40649000-40689000 r-xp 00000000 08:05 796470     /usr/lib/libpixman-1.so.0.13.2
40689000-4068b000 r--p 0003f000 08:05 796470     /usr/lib/libpixman-1.so.0.13.2
4068b000-4068c000 rw-p 00041000 08:05 796470     /usr/lib/libpixman-1.so.0.13.2
4068c000-406f0000 r-xp 00000000 08:05 795920     /usr/lib/libdirectfb-1.0.so.0.1.0
406f0000-406f1000 r--p 00063000 08:05 795920     /usr/lib/libdirectfb-1.0.so.0.1.0
406f1000-406f2000 rw-p 00064000 08:05 795920     /usr/lib/libdirectfb-1.0.so.0.1.0
406f2000-406f9000 r-xp 00000000 08:05 796000     /usr/lib/libfusion-1.0.so.0.1.0
406f9000-406fa000 r--p 00006000 08:05 796000     /usr/lib/libfusion-1.0.so.0.1.0
406fa000-406fb000 rw-p 00007000 08:05 796000     /usr/lib/libfusion-1.0.so.0.1.0
406fb000-4070e000 r-xp 00000000 08:05 795918     /usr/lib/libdirect-1.0.so.0.1.0
4070e000-4070f000 r--p 00012000 08:05 795918     /usr/lib/libdirect-1.0.so.0.1.0
4070f000-40710000 rw-p 00013000 08:05 795918     /usr/lib/libdirect-1.0.so.0.1.0
40710000-40734000 r-xp 00000000 08:05 796476     /usr/lib/libpng12.so.0.27.0
40734000-40735000 r--p 00023000 08:05 796476     /usr/lib/libpng12.so.0.27.0
40735000-40736000 rw-p 00024000 08:05 796476     /usr/lib/libpng12.so.0.27.0
40736000-40739000 r-xp 00000000 08:05 796685     /usr/lib/libxcb-render-util.so.0.0.0
40739000-4073a000 r--p 00002000 08:05 796685     /usr/lib/libxcb-render-util.so.0.0.0
4073a000-4073b000 rw-p 00003000 08:05 796685     /usr/lib/libxcb-render-util.so.0.0.0
4073b000-40741000 r-xp 00000000 08:05 795971     /usr/lib/libxcb-render.so.0.0.0
t/GtkMozEmbed....dubious                                                     
	Test returned status 0 (wstat 6, 0x6)
	after all the subtests completed successfully
Failed Test     Stat Wstat Total Fail  List of Failed
-------------------------------------------------------------------------------
t/GtkMozEmbed.t    0     6     8    0  ??
Failed 1/1 test scripts. 0/8 subtests failed.
Files=1, Tests=8,  0 wallclock secs ( 0.32 cusr +  0.00 csys =  0.32 CPU)
Failed 1/1 test programs. 0/8 subtests failed.
make: *** [test_dynamic] Error 255
  TSCH/Gtk2-MozEmbed-0.08.tar.gz
  /usr/bin/make test -- NOT OK
//hint// to see the cpan-testers results for installing this module, try:
  reports TSCH/Gtk2-MozEmbed-0.08.tar.gz
Failed during this command:
 TSCH/Gtk2-MozEmbed-0.08.tar.gz               : make_test NO

cpan[4]> 
```

---

### Post by smo0th on 2009-08-02
I have the same problem, what I already did is to install the dev packages for perl and mozilla although the result doesn't changes, still looking for a way....

---

