---
title: "Synaptic PM shows the old bluez version"
date: 2010-09-23
forum: General Help
---

### Post by tetris9999 on 2010-09-23
Hello, I am new to Linux and I like it :) . This is my first attempt to build something from source. I downloaded the bluez 4.72 and I think successfully built and installed it (at least I got no error messages). Now I can't sea weather it is in operation, because Synaptic PM still shows bluez 4.60 version in use. Is it possible to show the newly installed version? 

This is the log of the make and make install operation ( I followed the 'Read me' instruction), if there is something wrong, please let me know. Thanks

krum@desktop:~/bluez-4.72$ ./configure --prefix=/usr --mandir=/usr/share/man \
> 
acinclude.m4    config.h.in     input/          plugins/
aclocal.m4      config.sub      INSTALL         README
attrib/         configure       install-sh      sbc/
audio/          configure.ac    lib/            scripts/
AUTHORS         COPYING         ltmain.sh       serial/
bluez.pc.in     COPYING.LIB     Makefile.am     src/
btio/           cups/           Makefile.in     test/
ChangeLog       depcomp         Makefile.tools  tools/
compat/         doc/            missing         tracer/
compile         gdbus/          network/        ylwrap
config.guess    health/         NEWS            
> --sysconfdir=/etc --localstatedir=/var --libexecdir=/lib
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking whether gcc accepts -fPIE... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for bison... no
checking for byacc... no
checking for flex... no
checking for lex... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for ppoll... yes
checking for dlopen in -ldl... yes
checking for DBUS... yes
checking for dbus_watch_get_unix_fd in -ldbus-1... yes
checking for dbus_connection_can_send_type in -ldbus-1... no
checking for GLIB... yes
checking for ALSA... no
checking for clock_gettime in -lrt... yes
checking for GSTREAMER... no
checking for USB... no
checking for usb_get_busses in -lusb... no
checking for usb_interrupt_read in -lusb... no
checking for SNDFILE... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating scripts/bluetooth.rules
config.status: creating doc/version.xml
config.status: creating src/bluetooth.ver
config.status: creating src/bluetoothd.8
config.status: creating bluez.pc
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing libtool commands

krum@desktop:~/bluez-4.72$ sudo make
make --no-print-directory all-am
  CC     audio/telephony-dummy.o
  CC     audio/telephony-maemo5.o
  CC     audio/telephony-ofono.o
  CC     audio/telephony-maemo6.o
  AR     audio/libtelephony.a
  GEN    lib/bluetooth/bluetooth.h
  GEN    lib/bluetooth/hci.h
  GEN    lib/bluetooth/hci_lib.h
  GEN    lib/bluetooth/sco.h
  GEN    lib/bluetooth/l2cap.h
  GEN    lib/bluetooth/sdp.h
  GEN    lib/bluetooth/sdp_lib.h
  GEN    lib/bluetooth/rfcomm.h
  GEN    lib/bluetooth/bnep.h
  GEN    lib/bluetooth/cmtp.h
  GEN    lib/bluetooth/hidp.h
  CC     lib/bluetooth.lo
  CC     lib/hci.lo
  CC     lib/sdp.lo
  CCLD   lib/libbluetooth.la
  CC     tools/main.o
  CC     tools/parser.o
  CC     tools/lexer.o
  CC     tools/kword.o
  CCLD   tools/rfcomm
  CC     tools/l2ping.o
  CCLD   tools/l2ping
  CC     tools/hcitool.o
  CC     src/oui.o
  CC     src/textfile.o
  CCLD   tools/hcitool
  CC     tools/sdptool.o
  CC     src/sdp-xml.o
  CCLD   tools/sdptool
  CC     tools/ciptool.o
  CCLD   tools/ciptool
  CC     tools/avinfo.o
  CCLD   tools/avinfo
  CC     tools/ppporc.o
  CCLD   tools/ppporc
  CC     tools/hcieventmask.o
  CCLD   tools/hcieventmask
  CC     tools/hcisecfilter.o
  CCLD   tools/hcisecfilter
  CC     gdbus/mainloop.o
  CC     gdbus/watch.o
  CC     gdbus/object.o
  CC     gdbus/polkit.o
  CC     audio/main.o
  CC     audio/manager.o
  CC     audio/gateway.o
  CC     audio/headset.o
  CC     audio/control.o
  CC     audio/device.o
  CC     audio/source.o
  CC     audio/sink.o
  CC     audio/a2dp.o
  CC     audio/avdtp.o
  CC     audio/ipc.o
  CC     audio/unix.o
  CC     audio/media.o
  CC     audio/transport.o
  CC     input/main.o
  CC     input/manager.o
  CC     input/server.o
  CC     input/device.o
  CC     input/fakehid.o
  CC     serial/main.o
  CC     serial/manager.o
  CC     serial/proxy.o
  CC     serial/port.o
  CC     network/main.o
  CC     network/manager.o
  CC     network/common.o
  CC     network/server.o
  CC     network/connection.o
  CC     plugins/service.o
  CC     plugins/hciops.o
  CC     plugins/formfactor.o
  CC     plugins/storage.o
  CC     attrib/att.o
  CC     attrib/gatt.o
  CC     attrib/gattrib.o
  CC     btio/btio.o
  CC     src/main.o
  CC     src/log.o
  CC     src/security.o
  CC     src/rfkill.o
  CC     src/sdpd-server.o
  CC     src/sdpd-request.o
  CC     src/sdpd-service.o
  CC     src/sdpd-database.o
  CC     src/attrib-server.o
  CC     src/glib-helper.o
  GEN    src/builtin.h
  CC     src/plugin.o
  CC     src/storage.o
  CC     src/agent.o
  CC     src/error.o
  CC     src/manager.o
  CC     src/adapter.o
  CC     src/device.o
  CC     src/dbus-common.o
  CC     src/dbus-hci.o
  GEN    audio/telephony.c
  CC     audio/telephony.o
  CCLD   src/bluetoothd
  CC     tools/hciattach.o
  CC     tools/hciattach_st.o
  CC     tools/hciattach_ti.o
  CC     tools/hciattach_tialt.o
  CC     tools/hciattach_ath3k.o
  CC     tools/hciattach_qualcomm.o
  CCLD   tools/hciattach
  CC     tools/hciconfig.o
  CC     tools/csr.o
  CCLD   tools/hciconfig
  GEN    scripts/97-bluetooth.rules

krum@desktop:~/bluez-4.72$ sudo make install
test -z "/usr/lib" || /bin/mkdir -p "/usr/lib"
 /bin/bash ./libtool   --mode=install /usr/bin/install -c   lib/libbluetooth.la '/usr/lib'
libtool: install: /usr/bin/install -c lib/.libs/libbluetooth.so.3.10.0 /usr/lib/libbluetooth.so.3.10.0
libtool: install: (cd /usr/lib && { ln -s -f libbluetooth.so.3.10.0 libbluetooth.so.3 || { rm -f libbluetooth.so.3 && ln -s libbluetooth.so.3.10.0 libbluetooth.so.3; }; })
libtool: install: (cd /usr/lib && { ln -s -f libbluetooth.so.3.10.0 libbluetooth.so || { rm -f libbluetooth.so && ln -s libbluetooth.so.3.10.0 libbluetooth.so; }; })
libtool: install: /usr/bin/install -c lib/.libs/libbluetooth.lai /usr/lib/libbluetooth.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
test -z "/usr/bin" || /bin/mkdir -p "/usr/bin"
  /bin/bash ./libtool   --mode=install /usr/bin/install -c tools/rfcomm tools/l2ping tools/hcitool tools/sdptool tools/ciptool '/usr/bin'
libtool: install: /usr/bin/install -c tools/.libs/rfcomm /usr/bin/rfcomm
libtool: install: /usr/bin/install -c tools/.libs/l2ping /usr/bin/l2ping
libtool: install: /usr/bin/install -c tools/.libs/hcitool /usr/bin/hcitool
libtool: install: /usr/bin/install -c tools/.libs/sdptool /usr/bin/sdptool
libtool: install: /usr/bin/install -c tools/.libs/ciptool /usr/bin/ciptool
test -z "/usr/sbin" || /bin/mkdir -p "/usr/sbin"
  /bin/bash ./libtool   --mode=install /usr/bin/install -c src/bluetoothd tools/hciattach tools/hciconfig '/usr/sbin'
libtool: install: /usr/bin/install -c src/.libs/bluetoothd /usr/sbin/bluetoothd
libtool: install: /usr/bin/install -c tools/.libs/hciattach /usr/sbin/hciattach
libtool: install: /usr/bin/install -c tools/.libs/hciconfig /usr/sbin/hciconfig
test -z "" || /bin/mkdir -p ""
test -z "" || /bin/mkdir -p ""
test -z "/etc/bluetooth" || /bin/mkdir -p "/etc/bluetooth"
 /usr/bin/install -c -m 644 src/main.conf tools/rfcomm.conf '/etc/bluetooth'
test -z "" || /bin/mkdir -p ""
test -z "/etc/dbus-1/system.d" || /bin/mkdir -p "/etc/dbus-1/system.d"
 /usr/bin/install -c -m 644 src/bluetooth.conf '/etc/dbus-1/system.d'
test -z "" || /bin/mkdir -p ""
test -z "" || /bin/mkdir -p ""
test -z "/usr/include/bluetooth" || /bin/mkdir -p "/usr/include/bluetooth"
 /usr/bin/install -c -m 644 lib/bluetooth.h lib/hci.h lib/hci_lib.h lib/sco.h lib/l2cap.h lib/sdp.h lib/sdp_lib.h lib/rfcomm.h lib/bnep.h lib/cmtp.h lib/hidp.h '/usr/include/bluetooth'
test -z "/usr/share/man/man1" || /bin/mkdir -p "/usr/share/man/man1"
 /usr/bin/install -c -m 644 tools/rfcomm.1 tools/hcitool.1 tools/sdptool.1 tools/ciptool.1 '/usr/share/man/man1'
test -z "/usr/share/man/man8" || /bin/mkdir -p "/usr/share/man/man8"
 /usr/bin/install -c -m 644 tools/l2ping.8 tools/hciattach.8 tools/hciconfig.8 src/bluetoothd.8 '/usr/share/man/man8'
test -z "/usr/lib/pkgconfig" || /bin/mkdir -p "/usr/lib/pkgconfig"
 /usr/bin/install -c -m 644 bluez.pc '/usr/lib/pkgconfig'
test -z "/usr/lib/bluetooth/plugins" || /bin/mkdir -p "/usr/lib/bluetooth/plugins"
test -z "/lib/udev/rules.d" || /bin/mkdir -p "/lib/udev/rules.d"
 /usr/bin/install -c -m 644 scripts/97-bluetooth.rules '/lib/udev/rules.d'
test -z "/var/lib/bluetooth" || /bin/mkdir -p "/var/lib/bluetooth"
krum@desktop:~/bluez-4.72$

---

### Post by klemes on 2010-09-23
This is normal because Synaptic only takes into account deb packages,
If you want it to show the latest's compiled package info then install it by running 'sudo  checkinstall' after the 'make' step.You need to install it first by typing 'sudo aptitude install checkinstall' and when you run it after make it will convert your newly compiled program into a deb package and the install it.You can then uninstall it anytime by running 'sudo dpkg -r <name_of_the_package.deb> .:guitar:

---

### Post by tetris9999 on 2010-09-23
Thanks for the prompt reply, I installed checkinstall and run it after the sudo make, but I got the error. Do you have an idea what is wrong? Thanks.



[IMG]http://www.iimmgg.com/image/aba891980c95457c686a787aea679379[/IMG]

---

### Post by klemes on 2010-09-24
Maybe you could try uninstalling libbluetooth-dev after running make and before running checkinstall.Just a guess but you could try that.:popcorn:

---

