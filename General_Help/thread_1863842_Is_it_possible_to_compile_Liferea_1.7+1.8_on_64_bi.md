---
title: "Is it possible to compile Liferea 1.7+/1.8 on 64 bit 11.10?"
date: 2011-10-18
forum: General Help
---

### Post by jb5 on 2011-10-18
I'm trying to compile Lifrea 1.7+ on new Oneric 11.10 (64bit) installation.

./configure fails with

```
checking pkg-config is at least version 0.9.0... yes
checking for SM... yes
checking for LIBNOTIFY... yes
checking for LIBINDICATE... no
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
checking for PACKAGE... no
configure: error: Package requirements (	gtk+-2.0 >= 2.18.0
		glib-2.0 >= 2.24.0
		gio-2.0 >= 2.26.0
		pango >= 1.4.0
		gconf-2.0 >= 1.1.9
		libxml-2.0 >= 2.6.27
		libxslt >= 1.1.19
		sqlite3 >= 3.6.10
		gmodule-2.0 >= 2.0.0
		gthread-2.0
		libsoup-2.4 >= 2.28.2
		unique-1.0
		webkit-1.0 >= 1.2.2
		json-glib-1.0) were not met:

No package 'unique-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```Have installed following extra packages, to no avail```
sudo apt-get install build-essential checkinstall gnome-core-devel
```

Also tried ```
sudo apt-get build-dep liferea
```
Any Ideas?

---

### Post by mikejonesey on 2011-10-18
sudo ldconfig?

---

### Post by jb5 on 2011-10-18
Should that command be run in the liferea source directory or /sbin?

Sorry not come across this command before.

---

### Post by mikejonesey on 2011-10-18
any dir; it will actually run.../sbin/ldconfig

---

### Post by mikejonesey on 2011-10-18
```
sudo ldconfig -v
```

---

### Post by jb5 on 2011-10-18
OK - the verbose option throws out ```
/lib/i386-linux-gnu:
	libc.so.6 -> libc-2.13.so
	libexpatw.so.1 -> libexpatw.so.1.5.2
	libdl.so.2 -> libdl-2.13.so
	libpcprofile.so -> libpcprofile.so
	libgcc_s.so.1 -> libgcc_s.so.1
	libnss_nis.so.2 -> libnss_nis-2.13.so
	libglib-2.0.so.0 -> libglib-2.0.so.0.3000.0
	libresolv.so.2 -> libresolv-2.13.so
	libthread_db.so.1 -> libthread_db-1.0.so
	libdbus-1.so.3 -> libdbus-1.so.3.5.7
	libnss_hesiod.so.2 -> libnss_hesiod-2.13.so
	libssl.so.1.0.0 -> libssl.so.1.0.0
	libkeyutils.so.1 -> libkeyutils.so.1.3
	libBrokenLocale.so.1 -> libBrokenLocale-2.13.so
	libcrypto.so.1.0.0 -> libcrypto.so.1.0.0
	libutil.so.1 -> libutil-2.13.so
	libcrypt.so.1 -> libcrypt-2.13.so
	libmemusage.so -> libmemusage.so
	libnss_nisplus.so.2 -> libnss_nisplus-2.13.so
	libnss_compat.so.2 -> libnss_compat-2.13.so
	libnss_files.so.2 -> libnss_files-2.13.so
	libSegFault.so -> libSegFault.so
	librt.so.1 -> librt-2.13.so
	libpthread.so.0 -> libpthread-2.13.so
	libwrap.so.0 -> libwrap.so.0.7.6
	libcidn.so.1 -> libcidn-2.13.so
	libnsl.so.1 -> libnsl-2.13.so
	libnss_dns.so.2 -> libnss_dns-2.13.so
	libpng12.so.0 -> libpng12.so.0.46.0
	libpcre.so.3 -> libpcre.so.3.12.1
	libexpat.so.1 -> libexpat.so.1.5.2
	libgpg-error.so.0 -> libgpg-error.so.0.8.0
	libanl.so.1 -> libanl-2.13.so
	libgcrypt.so.11 -> libgcrypt.so.11.7.0
	libm.so.6 -> libm-2.13.so
	libselinux.so.1 -> libselinux.so.1
	libuuid.so.1 -> libuuid.so.1.3.0
	libz.so.1 -> libz.so.1.2.3.4
	ld-linux.so.2 -> ld-2.13.so
	libcom_err.so.2 -> libcom_err.so.2.1
/usr/lib/i386-linux-gnu:
	libXt.so.6 -> libXt.so.6.0.0
	libpangoxft-1.0.so.0 -> libpangoxft-1.0.so.0.2903.0
	libFLAC.so.8 -> libFLAC.so.8.2.0
	libtiff.so.4 -> libtiff.so.4.3.4
	libpulse.so.0 -> libpulse.so.0.13.4
	libxcb-shm.so.0 -> libxcb-shm.so.0.0.0
	libffi.so.6 -> libffi.so.6.0.0
	libcups.so.2 -> libcups.so.2
	libXfixes.so.3 -> libXfixes.so.3.1.0
	libXau.so.6 -> libXau.so.6.0.0
	libpcreposix.so.3 -> libpcreposix.so.3.12.1
	liblber-2.4.so.2 -> liblber-2.4.so.2.7.0
	libpulse-simple.so.0 -> libpulse-simple.so.0.0.3
	libXcomposite.so.1 -> libXcomposite.so.1.0.0
	libpulsecommon-1.0.so -> libpulsecommon-1.0.so
	libgssapi_krb5.so.2 -> libgssapi_krb5.so.2.2
	libgmodule-2.0.so.0 -> libgmodule-2.0.so.0.3000.0
	libkrb5.so.3 -> libkrb5.so.3.3
	libgio-2.0.so.0 -> libgio-2.0.so.0.3000.0
	libsmime3.so -> libsmime3.so.1d
	libthai.so.0 -> libthai.so.0.1.6
	libjpeg.so.62 -> libjpeg.so.62.0.0
	libvorbisenc.so.2 -> libvorbisenc.so.2.0.8
	libXinerama.so.1 -> libXinerama.so.1.0.0
	libldap_r-2.4.so.2 -> libldap_r-2.4.so.2.7.0
	libjack.so.0 -> libjack.so.0.1.0
	libasound.so.2 -> libasound.so.2.0.0
	libgnutls-extra.so.26 -> libgnutls-extra.so.26.16.14
	libkrb5support.so.0 -> libkrb5support.so.0.1
	libQtCLucene.so.4 -> libQtCLucene.so.4.7.4
	libpangocairo-1.0.so.0 -> libpangocairo-1.0.so.0.2903.0
	libjson.so.0 -> libjson.so.0.0.1
	libXdmcp.so.6 -> libXdmcp.so.6.0.0
	libplds4.so -> libplds4.so.0d
	libQtDeclarative.so.4 -> libQtDeclarative.so.4.7.4
	libgnutls.so.26 -> libgnutls.so.26.16.14
	libXss.so.1 -> libXss.so.1.0.0
	libgthread-2.0.so.0 -> libgthread-2.0.so.0.3000.0
	libICE.so.6 -> libICE.so.6.3.0
	libQtXmlPatterns.so.4 -> libQtXmlPatterns.so.4.7.4
	libnss3.so -> libnss3.so.1d
	libsqlite3.so.0 -> libsqlite3.so.0.8.6
	libdatrie.so.1 -> libdatrie.so.1.1.0
	libaudio.so.2 -> libaudio.so.2.4
	libQtXml.so.4 -> libQtXml.so.4.7.4
	libfontconfig.so.1 -> libfontconfig.so.1.4.4
	libxcb.so.1 -> libxcb.so.1.1.0
	libcurl.so.4 -> libcurl.so.4.2.0
	libssl3.so -> libssl3.so.1d
	libstdc++.so.6 -> libstdc++.so.6.0.16
	libQtCore.so.4 -> libQtCore.so.4.7.4
	libidn.so.11 -> libidn.so.11.6.5
	libatk-1.0.so.0 -> libatk-1.0.so.0.20209.1
	libQtSql.so.4 -> libQtSql.so.4.7.4
	libfreetype.so.6 -> libfreetype.so.6.6.2
	libavahi-client.so.3 -> libavahi-client.so.3.2.9
	libsasl2.so.2 -> libsasl2.so.2.0.24
	libpangox-1.0.so.0 -> libpangox-1.0.so.0.2903.0
	libXrender.so.1 -> libXrender.so.1.3.0
	libpixman-1.so.0 -> libpixman-1.so.0.22.2
	libvorbis.so.0 -> libvorbis.so.0.4.5
	libsndfile.so.1 -> libsndfile.so.1.0.24
	libgobject-2.0.so.0 -> libgobject-2.0.so.0.3000.0
	libnssutil3.so -> libnssutil3.so.1d
	libXext.so.6 -> libXext.so.6.4.0
	libgnutls-openssl.so.26 -> libgnutls-openssl.so.26.16.14
	libxcb-render.so.0 -> libxcb-render.so.0.0.0
	libgdk_pixbuf-2.0.so.0 -> libgdk_pixbuf-2.0.so.0.2400.0
	libXft.so.2 -> libXft.so.2.2.0
	libQtScript.so.4 -> libQtScript.so.4.7.4
	libasyncns.so.0 -> libasyncns.so.0.3.1
	libgtk-x11-2.0.so.0 -> libgtk-x11-2.0.so.0.2400.6
	libk5crypto.so.3 -> libk5crypto.so.3.1
	libXv.so.1 -> libXv.so.1.0.0
	librtmp.so.0 -> librtmp.so.0
	libQtDBus.so.4 -> libQtDBus.so.4.7.4
	libdbusmenu-qt.so.2 -> libdbusmenu-qt.so.2.6.0
	libXi.so.6 -> libXi.so.6.1.0
	libogg.so.0 -> libogg.so.0.7.1
	libavahi-common.so.3 -> libavahi-common.so.3.5.3
	libX11.so.6 -> libX11.so.6.3.0
	libXrandr.so.2 -> libXrandr.so.2.2.0
	libQtGui.so.4 -> libQtGui.so.4.7.4
	libpangoft2-1.0.so.0 -> libpangoft2-1.0.so.0.2903.0
	libspeexdsp.so.1 -> libspeexdsp.so.1.5.0
	libnspr4.so -> libnspr4.so.0d
	libXcursor.so.1 -> libXcursor.so.1.0.2
	libdb-5.1.so -> libdb-5.1.so
	libgdk_pixbuf_xlib-2.0.so.0 -> libgdk_pixbuf_xlib-2.0.so.0.2400.0
	libjasper.so.1 -> libjasper.so.1.0.0
	libplc4.so -> libplc4.so.0d
	libsamplerate.so.0 -> libsamplerate.so.0.1.7
	libSM.so.6 -> libSM.so.6.0.1
	libpango-1.0.so.0 -> libpango-1.0.so.0.2903.0
	libXdamage.so.1 -> libXdamage.so.1.1.0
	libgdk-x11-2.0.so.0 -> libgdk-x11-2.0.so.0.2400.6
	libQtNetwork.so.4 -> libQtNetwork.so.4.7.4
	liblcms.so.1 -> liblcms.so.1.0.19
	libmng.so.1 -> libmng.so.1.1.0.10
	libcairo.so.2 -> libcairo.so.2.11000.2
	libtasn1.so.3 -> libtasn1.so.3.1.11
/usr/local/lib:
/lib/x86_64-linux-gnu:
	libext2fs.so.2 -> libext2fs.so.2.4
	libc.so.6 -> libc-2.13.so
	libblkid.so.1 -> libblkid.so.1.1.0
	libexpatw.so.1 -> libexpatw.so.1.5.2
	libdl.so.2 -> libdl-2.13.so
	libpcprofile.so -> libpcprofile.so
	libgcc_s.so.1 -> libgcc_s.so.1
	libnss_nis.so.2 -> libnss_nis-2.13.so
	libglib-2.0.so.0 -> libglib-2.0.so.0.3000.0
	libresolv.so.2 -> libresolv-2.13.so
	libthread_db.so.1 -> libthread_db-1.0.so
	libe2p.so.2 -> libe2p.so.2.3
	libdbus-1.so.3 -> libdbus-1.so.3.5.7
	libacl.so.1 -> libacl.so.1.1.0
	libnss_hesiod.so.2 -> libnss_hesiod-2.13.so
	libssl.so.1.0.0 -> libssl.so.1.0.0
	libkeyutils.so.1 -> libkeyutils.so.1.3
	libBrokenLocale.so.1 -> libBrokenLocale-2.13.so
	libcrypto.so.1.0.0 -> libcrypto.so.1.0.0
	libutil.so.1 -> libutil-2.13.so
	libss.so.2 -> libss.so.2.0
	libudev.so.0 -> libudev.so.0.12.0
	libcrypt.so.1 -> libcrypt-2.13.so
	libmemusage.so -> libmemusage.so
	libnss_nisplus.so.2 -> libnss_nisplus-2.13.so
	libnss_compat.so.2 -> libnss_compat-2.13.so
	libnss_files.so.2 -> libnss_files-2.13.so
	libSegFault.so -> libSegFault.so
	libmount.so.1 -> libmount.so.1.1.0
	libusb-1.0.so.0 -> libusb-1.0.so.0.0.0
	librt.so.1 -> librt-2.13.so
	libpthread.so.0 -> libpthread-2.13.so
	libwrap.so.0 -> libwrap.so.0.7.6
	libcidn.so.1 -> libcidn-2.13.so
	libnsl.so.1 -> libnsl-2.13.so
	libnss_dns.so.2 -> libnss_dns-2.13.so
	libattr.so.1 -> libattr.so.1.1.0
	libpng12.so.0 -> libpng12.so.0.46.0
	libpcre.so.3 -> libpcre.so.3.12.1
	libexpat.so.1 -> libexpat.so.1.5.2
	libpamc.so.0 -> libpamc.so.0.82.1
	libgpg-error.so.0 -> libgpg-error.so.0.8.0
	libanl.so.1 -> libanl-2.13.so
	libgcrypt.so.11 -> libgcrypt.so.11.7.0
	libpam_misc.so.0 -> libpam_misc.so.0.82.0
	libm.so.6 -> libm-2.13.so
	libselinux.so.1 -> libselinux.so.1
	libuuid.so.1 -> libuuid.so.1.3.0
	libpam.so.0 -> libpam.so.0.83.0
	libz.so.1 -> libz.so.1.2.3.4
	ld-linux-x86-64.so.2 -> ld-2.13.so
	libcom_err.so.2 -> libcom_err.so.2.1
/usr/lib/x86_64-linux-gnu:
	libcupscgi.so.1 -> libcupscgi.so.1
	libLLVM-2.9.so.1 -> libLLVM-2.9.so.1
	libxcb-shape.so.0 -> libxcb-shape.so.0.0.0
	libXt.so.6 -> libXt.so.6.0.0
	libcupsimage.so.2 -> libcupsimage.so.2
	libpangoxft-1.0.so.0 -> libpangoxft-1.0.so.0.2903.0
	libFLAC.so.8 -> libFLAC.so.8.2.0
	libcupsdriver.so.1 -> libcupsdriver.so.1
	libv4l1.so.0 -> libv4l1.so.0
	libtiff.so.4 -> libtiff.so.4.3.4
	libpulse.so.0 -> libpulse.so.0.13.4
	libsensors.so.4 -> libsensors.so.4.3.1
	libxcb-shm.so.0 -> libxcb-shm.so.0.0.0
	libdb-4.8.so -> libdb-4.8.so
	libffi.so.6 -> libffi.so.6.0.0
	libcups.so.2 -> libcups.so.2
	libavahi-ui-gtk3.so.0 -> libavahi-ui-gtk3.so.0.1.4
	libXfixes.so.3 -> libXfixes.so.3.1.0
	libXau.so.6 -> libXau.so.6.0.0
	libplds4.so -> libplds4.so
	libpcreposix.so.3 -> libpcreposix.so.3.12.1
	liblber-2.4.so.2 -> liblber-2.4.so.2.7.0
	libpulse-simple.so.0 -> libpulse-simple.so.0.0.3
	libXcomposite.so.1 -> libXcomposite.so.1.0.0
	libedit.so.2 -> libedit.so.2.11
	libpulsecommon-1.0.so -> libpulsecommon-1.0.so
	libpciaccess.so.0 -> libpciaccess.so.0.10.8
	libgssapi_krb5.so.2 -> libgssapi_krb5.so.2.2
	libgmodule-2.0.so.0 -> libgmodule-2.0.so.0.3000.0
	liboauth.so.0 -> liboauth.so.0.8.1
	libkrb5.so.3 -> libkrb5.so.3.3
	libquadmath.so.0 -> libquadmath.so.0.0.0
	libgio-2.0.so.0 -> libgio-2.0.so.0.3000.0
	liblouis.so.2 -> liblouis.so.2.2.3
	libbamf3.so.0 -> libbamf3.so.0.0.0
	libXxf86vm.so.1 -> libXxf86vm.so.1.0.0
	libsmime3.so -> libsmime3.so.1d
	libthai.so.0 -> libthai.so.0.1.6
	libjpeg.so.62 -> libjpeg.so.62.0.0
	libvorbisenc.so.2 -> libvorbisenc.so.2.0.8
	libcogl.so.5 -> libcogl.so.5.0.0
	libXinerama.so.1 -> libXinerama.so.1.0.0
	libldap_r-2.4.so.2 -> libldap_r-2.4.so.2.7.0
	liblcms2.so.2 -> liblcms2.so.2.0.2
	libjack.so.0 -> libjack.so.0.1.0
	libieee1284.so.3 -> libieee1284.so.3.2.2
	libasound.so.2 -> libasound.so.2.0.0
	libgnutls-extra.so.26 -> libgnutls-extra.so.26.16.14
	libkrb5support.so.0 -> libkrb5support.so.0.1
	libnspr4.so -> libnspr4.so
	librsvg-2.so.2 -> librsvg-2.so.2.34.1
	libQtCLucene.so.4 -> libQtCLucene.so.4.7.4
	libpangocairo-1.0.so.0 -> libpangocairo-1.0.so.0.2903.0
	libjson.so.0 -> libjson.so.0.0.1
	libxcb-dri2.so.0 -> libxcb-dri2.so.0.0.0
	libSoundTouch.so.0 -> libSoundTouch.so.0.0.0
	libXdmcp.so.6 -> libXdmcp.so.6.0.0
	libQtDeclarative.so.4 -> libQtDeclarative.so.4.7.4
	libgnutls.so.26 -> libgnutls.so.26.16.14
	libXss.so.1 -> libXss.so.1.0.0
	libcolord.so.1 -> libcolord.so.1.0.4
	libgthread-2.0.so.0 -> libgthread-2.0.so.0.3000.0
	libICE.so.6 -> libICE.so.6.3.0
	libQtXmlPatterns.so.4 -> libQtXmlPatterns.so.4.7.4
	libnss3.so -> libnss3.so.1d
	libsqlite3.so.0 -> libsqlite3.so.0.8.6
	libglapi.so.0 -> libglapi.so.0.0.0
	libgomp.so.1 -> libgomp.so.1.0.0
	libdatrie.so.1 -> libdatrie.so.1.1.0
	libGLU.so.1 -> libGLU.so.1.3.071100
	libaudio.so.2 -> libaudio.so.2.4
	libQtXml.so.4 -> libQtXml.so.4.7.4
	libfontconfig.so.1 -> libfontconfig.so.1.4.4
	libcairo-gobject.so.2 -> libcairo-gobject.so.2.11000.2
	libxcb.so.1 -> libxcb.so.1.1.0
	libxcb-randr.so.0 -> libxcb-randr.so.0.1.0
	libtdb.so.1 -> libtdb.so.1.2.9
	libnotify.so.4 -> libnotify.so.4.0.0
	libdrm_radeon.so.1 -> libdrm_radeon.so.1.0.0
	libdrm_nouveau.so.1 -> libdrm_nouveau.so.1.0.0
	libssl3.so -> libssl3.so.1d
	libQtSvg.so.4 -> libQtSvg.so.4.7.4
	libstdc++.so.6 -> libstdc++.so.6.0.16
	libQtCore.so.4 -> libQtCore.so.4.7.4
	libidn.so.11 -> libidn.so.11.6.5
	libatk-1.0.so.0 -> libatk-1.0.so.0.20209.1
	libQtSql.so.4 -> libQtSql.so.4.7.4
	libfreetype.so.6 -> libfreetype.so.6.6.2
	libavahi-client.so.3 -> libavahi-client.so.3.2.9
	libsasl2.so.2 -> libsasl2.so.2.0.24
	libpangox-1.0.so.0 -> libpangox-1.0.so.0.2903.0
	libkms.so.1 -> libkms.so.1.0.0
	libXrender.so.1 -> libXrender.so.1.3.0
	libpixman-1.so.0 -> libpixman-1.so.0.22.2
	libclutter-glx-1.0.so.0 -> libclutter-glx-1.0.so.0.800.0
	libvorbis.so.0 -> libvorbis.so.0.4.5
	libsndfile.so.1 -> libsndfile.so.1.0.24
	libgailutil.so.18 -> libgailutil.so.18.0.1
	libgobject-2.0.so.0 -> libgobject-2.0.so.0.3000.0
	libcogl-pango.so.0 -> libcogl-pango.so.0.0.0
	libv4l2.so.0 -> libv4l2.so.0
	libdrm_intel.so.1 -> libdrm_intel.so.1.0.0
	libnssutil3.so -> libnssutil3.so.1d
	libXext.so.6 -> libXext.so.6.4.0
	libgnutls-openssl.so.26 -> libgnutls-openssl.so.26.16.14
	libvorbisfile.so.3 -> libvorbisfile.so.3.3.4
	libxcb-render.so.0 -> libxcb-render.so.0.0.0
	libpipeline.so.1 -> libpipeline.so.1.2.0
	libjpeg.so.8 -> libjpeg.so.8.3.0
	libavahi-core.so.7 -> libavahi-core.so.7.0.2
	libgdk_pixbuf-2.0.so.0 -> libgdk_pixbuf-2.0.so.0.2400.0
	libgdbm_compat.so.3 -> libgdbm_compat.so.3.0.0
	libXft.so.2 -> libXft.so.2.2.0
	libQtScript.so.4 -> libQtScript.so.4.7.4
	libasyncns.so.0 -> libasyncns.so.0.3.1
	libpng12.so.0 -> libpng.so
	libFLAC++.so.6 -> libFLAC++.so.6.2.0
	liblua5.1.so.0 -> liblua5.1.so.0.0.0
	libgudev-1.0.so.0 -> libgudev-1.0.so.0.1.0
	libavahi-gobject.so.0 -> libavahi-gobject.so.0.0.4
	libspeex.so.1 -> libspeex.so.1.5.0
	libgtk-x11-2.0.so.0 -> libgtk-x11-2.0.so.0.2400.6
	libk5crypto.so.3 -> libk5crypto.so.3.1
	libavahi-glib.so.1 -> libavahi-glib.so.1.0.2
	libXv.so.1 -> libXv.so.1.0.0
	librtmp.so.0 -> librtmp.so.0
	libcupsmime.so.1 -> libcupsmime.so.1
	libQtDBus.so.4 -> libQtDBus.so.4.7.4
	libdbusmenu-qt.so.2 -> libdbusmenu-qt.so.2.6.0
	libcurl-gnutls.so.4 -> libcurl-gnutls.so.4.2.0
	libXi.so.6 -> libXi.so.6.1.0
	libogg.so.0 -> libogg.so.0.7.1
	libavahi-common.so.3 -> libavahi-common.so.3.5.3
	libgdbm.so.3 -> libgdbm.so.3.0.0
	libX11.so.6 -> libX11.so.6.3.0
	libcairo-script-interpreter.so.2 -> libcairo-script-interpreter.so.2.11000.2
	libcupsppdc.so.1 -> libcupsppdc.so.1
	libXrandr.so.2 -> libXrandr.so.2.2.0
	libgutenprint.so.2 -> libgutenprint.so.2.0.8
	libQtGui.so.4 -> libQtGui.so.4.7.4
	libpangoft2-1.0.so.0 -> libpangoft2-1.0.so.0.2903.0
	libplc4.so -> libplc4.so
	libspeexdsp.so.1 -> libspeexdsp.so.1.5.0
	libXcursor.so.1 -> libXcursor.so.1.0.2
	libQtOpenGL.so.4 -> libQtOpenGL.so.4.7.4
	libdb-5.1.so -> libdb-5.1.so
	libgdk_pixbuf_xlib-2.0.so.0 -> libgdk_pixbuf_xlib-2.0.so.0.2400.0
	libjasper.so.1 -> libjasper.so.1.0.0
	libsamplerate.so.0 -> libsamplerate.so.0.1.7
	libdrm.so.2 -> libdrm.so.2.4.0
	libSM.so.6 -> libSM.so.6.0.1
	libpango-1.0.so.0 -> libpango-1.0.so.0.2903.0
	libXdamage.so.1 -> libXdamage.so.1.1.0
	libgdk-x11-2.0.so.0 -> libgdk-x11-2.0.so.0.2400.6
	libbamf.so.0 -> libbamf.so.0.0.0
	libv4lconvert.so.0 -> libv4lconvert.so.0
	libpulse-mainloop-glib.so.0 -> libpulse-mainloop-glib.so.0.0.4
	libX11-xcb.so.1 -> libX11-xcb.so.1.0.0
	libxcb-xv.so.0 -> libxcb-xv.so.0.0.0
	libQtNetwork.so.4 -> libQtNetwork.so.4.7.4
	libtalloc.so.2 -> libtalloc.so.2.0.5
	libdbus-glib-1.so.2 -> libdbus-glib-1.so.2.2.0
	liblcms.so.1 -> liblcms.so.1.0.19
	libpcap.so.0.8 -> libpcap.so.1.1.1
	libmng.so.1 -> libmng.so.1.1.0.10
	libcairo.so.2 -> libcairo.so.2.11000.2
	libtasn1.so.3 -> libtasn1.so.3.1.11
/usr/lib/x86_64-linux-gnu/mesa:
	libGL.so.1 -> libGL.so.1.2
/lib:
	libdevmapper.so.1.02.1 -> libdevmapper.so.1.02.1
	liblvm2app.so.2.2 -> liblvm2app.so.2.2
	libparted.so.0 -> libparted.so.0.0.1
	libncurses.so.5 -> libncurses.so.5.9
	libnss_mdns6_minimal.so.2 -> libnss_mdns6_minimal.so.2
	libnih.so.1 -> libnih.so.1.0.0
	libnss_mdns4.so.2 -> libnss_mdns4.so.2
	libulockmgr.so.1 -> libulockmgr.so.1.0.1
	libproc-3.2.8.so -> libproc-3.2.8.so
	libncursesw.so.5 -> libncursesw.so.5.9
	libply.so.2 -> libply.so.2.0.0
	libx86.so.1 -> libx86.so.1
	libusb-0.1.so.4 -> libusb-0.1.so.4.4.4
	libtinfo.so.5 -> libtinfo.so.5.9
	libnss_mdns4_minimal.so.2 -> libnss_mdns4_minimal.so.2
	libatasmart.so.4 -> libatasmart.so.4.0.3
	libhistory.so.6 -> libhistory.so.6.2
	libip4tc.so.0 -> libip4tc.so.0.0.0
	libipq_pic.so.0 -> libipq_pic.so.0.0.0
	libxtables.so.5 -> libxtables.so.5.0.0
	libiptc.so.0 -> libiptc.so.0.0.0
	libnih-dbus.so.1 -> libnih-dbus.so.1.0.0
	libreadline.so.6 -> libreadline.so.6.2
	libply-splash-graphics.so.2 -> libply-splash-graphics.so.2.0.0
	libsysfs.so.2 -> libsysfs.so.2.0.1
	libiw.so.30 -> libiw.so.30
	libslang.so.2 -> libslang.so.2.2.4
	libbsd.so.0 -> libbsd.so.0.3.0
	libcap.so.2 -> libcap.so.2.21
	libpopt.so.0 -> libpopt.so.0.0.0
	libdevmapper-event.so.1.02.1 -> libdevmapper-event.so.1.02.1
	libipq.so.0 -> libipq.so.0.0.0
	libply-boot-client.so.2 -> libply-boot-client.so.2.0.0
	libbrlapi.so.0.5 -> libbrlapi.so.0.5.5
	libpci.so.3 -> libpci.so.3.1.7
	libnss_mdns6.so.2 -> libnss_mdns6.so.2
	libntfs-3g.so.814 -> libntfs-3g.so.814.0.0
	libbz2.so.1.0 -> libbz2.so.1.0.4
	libip6tc.so.0 -> libip6tc.so.0.0.0
	libfuse.so.2 -> libfuse.so.2.8.4
	libnss_mdns_minimal.so.2 -> libnss_mdns_minimal.so.2
	libpcsclite.so.1 -> libpcsclite.so.1.0.0
	libnss_mdns.so.2 -> libnss_mdns.so.2
	libply-splash-core.so.2 -> libply-splash-core.so.2.0.0
/usr/lib:
	libnl-route.so.3 -> libnl-route.so.3.0.0
	libboost_wserialization.so.1.46.1 -> libboost_wserialization.so.1.46.1
	libfftw3.so.3 -> libfftw3.so.3.2.4
	libsmbclient.so.0 -> libsmbclient.so.0
	libboost_filesystem.so.1.46.1 -> libboost_filesystem.so.1.46.1
	libgamin-1.so.0 -> libgamin-1.so.0.1.10
	libpathplan.so.4 -> libpathplan.so.4.0.0
	libdca.so.0 -> libdca.so.0.0.0
	libpulsedsp.so -> libpulsedsp.so
	libgvc.so.5 -> libgvc.so.5.0.0
	libgstfft-0.10.so.0 -> libgstfft-0.10.so.0.24.0
	libmms.so.0 -> libmms.so.0.0.2
	libjson-glib-1.0.so.0 -> libjson-glib-1.0.so.0.1400.0
	libtic.so.5 -> libtic.so.5.9
	libmpc.so.2 -> libmpc.so.2.0.0
	libperl.so.5.12 -> libperl.so.5.12.4
	libebackend-1.2.so.1 -> libebackend-1.2.so.1.0.0
	libass.so.4 -> libass.so.4.1.0
	libunity.so.6 -> libunity.so.6.2.0
	libnfnetlink.so.0 -> libnfnetlink.so.0.2.0
	libwpd-stream-0.9.so.9 -> libwpd-stream-0.9.so.9.0.2
	libcaribou.so.0 -> libcaribou.so.0.0.0
	libgtop-2.0.so.7 -> libgtop-2.0.so.7.2.0
	libgailutil-3.so.0 -> libgailutil-3.so.0.0.0
	libguile-srfi-srfi-13-14-v-3.so.3 -> libguile-srfi-srfi-13-14-v-3.so.3.0.1
	libva.so.1 -> libva.so.1.0.12
	libisccfg.so.62 -> libisccfg.so.62.0.0
	libgstbase-0.10.so.0 -> libgstbase-0.10.so.0.29.0
	libguile-srfi-srfi-4-v-3.so.3 -> libguile-srfi-srfi-4-v-3.so.3.0.1
	libwx_gtk2u_gizmos-2.8.so.0 -> libwx_gtk2u_gizmos-2.8.so.0.7.0
	libfusion-1.2.so.9 -> libfusion-1.2.so.9.0.1
	libXvMC.so.1 -> libXvMC.so.1.0.0
	libgirepository-1.0.so.1 -> libgirepository-1.0.so.1.0.0
	libfftw3_threads.so.3 -> libfftw3_threads.so.3.2.4
	libtwolame.so.0 -> libtwolame.so.0.0.0
	liba52-0.7.4.so -> liba52-0.7.4.so
	libMonoSupportW.so -> libMonoSupportW.so
	liboverlay-scrollbar-0.2.so.0 -> liboverlay-scrollbar-0.2.so.0.0.11
	libupnp.so.3 -> libupnp.so.3.0.5
	libgstcheck-0.10.so.0 -> libgstcheck-0.10.so.0.29.0
	libcddb.so.2 -> libcddb.so.2.2.3
	libORBit-2.so.0 -> libORBit-2.so.0.1.0
	libenca.so.0 -> libenca.so.0.5.1
	libcap-ng.so.0 -> libcap-ng.so.0.0.0
	libevent-2.0.so.5 -> libevent-2.0.so.5.1.1
	libgedit-private.so.0 -> libgedit-private.so.0.0.0
	libmhash.so.2 -> libmhash.so.2.0.1
	libgiomm-2.4.so.1 -> libgiomm-2.4.so.1.3.0
	libsp.so.1 -> libsp.so.1.0.3
	libMonoPosixHelper.so -> libMonoPosixHelper.so
	libsvn_auth_gnome_keyring-1.so.1 -> libsvn_auth_gnome_keyring-1.so.1.0.0
	libwx_gtk2u_adv-2.8.so.0 -> libwx_gtk2u_adv-2.8.so.0.7.0
	libzephyr.so.4 -> libzephyr.so.4.0.0
	libpurple-client.so.0 -> libpurple-client.so.0.10.0
	libt1x.so.5 -> libt1x.so.5.1.2
	libutouch-frame.so.1 -> libutouch-frame.so.1.1.0
	libmagic.so.1 -> libmagic.so.1.0.0
	libpyglib-2.0-python2.7.so.0 -> libpyglib-2.0-python2.7.so.0.0.0
	libpulsecore-1.0.so -> libpulsecore-1.0.so
	libxslt.so.1 -> libxslt.so.1.1.26
	libvlc.so.5 -> libvlc.so.5.2.1
	libGLEW.so.1.5 -> libGLEW.so.1.5.2
	libgstaudio-0.10.so.0 -> libgstaudio-0.10.so.0.24.0
	libsvn_ra_neon-1.so.1 -> libsvn_ra_neon-1.so.1.0.0
	libflite.so.1 -> libflite.so.1.4
	libck-connector.so.0 -> libck-connector.so.0.0.0
	libart_lgpl_2.so.2 -> libart_lgpl_2.so.2.3.21
	libwx_gtk2u_ogl-2.8.so.0 -> libwx_gtk2u_ogl-2.8.so.0.7.0
	libp11-kit.so.0 -> libp11-kit.so.0.0.0
	libgnomeui-2.so.0 -> libgnomeui-2.so.0.2400.5
	libicutu.so.44 -> libicutu.so.44.2
	libecal-1.2.so.10 -> libecal-1.2.so.10.2.2
	libgstreamer-0.10.so.0 -> libgstreamer-0.10.so.0.29.0
	libsyncdaemon-1.0.so.1 -> libsyncdaemon-1.0.so.1.0.0
	libgksu2.so.0 -> libgksu2.so.0.0.2
	libIntelXvMC.so.1 -> libIntelXvMC.so.1.0.0
	libijs-0.35.so -> libijs-0.35.so
	libfolks.so.25 -> libfolks.so.25.2.2
	librom1394.so.0 -> librom1394.so.0.3.0
	libexif.so.12 -> libexif.so.12.3.2
	libgstapp-0.10.so.0 -> libgstapp-0.10.so.0.24.0
	libdns.so.69 -> libdns.so.69.1.2
	libgwibber-gtk.so.2 -> libgwibber-gtk.so.2.0.0
	libQtGConf.so.1 -> libQtGConf.so.1.0.0
	libtelepathy-glib.so.0 -> libtelepathy-glib.so.0.61.0
	liblightdm-gobject-1.so.0 -> liblightdm-gobject-1.so.0.0.0
	libiec61883.so.0 -> libiec61883.so.0.1.1
	libproxy.so.0 -> libproxy.so.0.0.0
	libnux-graphics-1.0.so.0 -> libnux-graphics-1.0.so.0.1400.0
	libvte2_90.so.9 -> libvte2_90.so.9.2800.2
	libdee-1.0.so.1 -> libdee-1.0.so.1.2.1
	libpanel.so.5 -> libpanel.so.5.9
	libsane.so.1 -> libsane.so.1.0.22
	libdvdnav.so.4 -> libdvdnav.so.4.1.3
	libltdl.so.7 -> libltdl.so.7.3.0
	libflite_cmu_us_awb.so.1 -> libflite_cmu_us_awb.so.1.4
	libgvpr.so.1 -> libgvpr.so.1.0.0
	liboil-0.3.so.0 -> liboil-0.3.so.0.3.0
	libmysqlclient_r.so.16 -> libmysqlclient_r.so.16.0.0
	libgnomekbd.so.7 -> libgnomekbd.so.7.0.0
	libido3-0.1.so.0 -> libido3-0.1.so.0.0.0
	libvamp-hostsdk.so.3 -> libvamp-hostsdk.so.3.1.0
	libxapian.so.22 -> libxapian.so.22.3.0
	libplist.so.1 -> libplist.so.1.1.6
	libgjs.so.0 -> libgjs.so.0.0.0
	libgdata.so.13 -> libgdata.so.13.0.0
	libslv2.so.9 -> libslv2.so.9.2.0
	libindicator-messages-status-provider.so.1 -> libindicator-messages-status-provider.so.1.0.0
	libgme.so.0 -> libgme.so.0.5.3
	libnetsnmptrapd.so.15 -> libnetsnmptrapd.so.15.1.2
	libmeanwhile.so.1 -> libmeanwhile.so.1.0.2
	libgettextlib-0.18.1.so -> libgettextlib.so
	libcanberra.so.0 -> libcanberra.so.0.2.5
	libtar.so.0 -> libtar.so.0.0.0
	libsvn_delta-1.so.1 -> libsvn_delta-1.so.1.0.0
	libsigc-2.0.so.0 -> libsigc-2.0.so.0.0.0
	libcompizconfig.so.0 -> libcompizconfig.so.0.0.0
	libsoup-gnome-2.4.so.1 -> libsoup-gnome-2.4.so.1.4.0
	libpspell.so.15 -> libpspell.so.15.1.4
	librest-0.7.so.0 -> librest-0.7.so.0.0.0
	libcanberra-gtk.so.0 -> libcanberra-gtk.so.0.1.8
	libappindicator.so.1 -> libappindicator.so.1.0.0
	libgstcdda-0.10.so.0 -> libgstcdda-0.10.so.0.24.0
	libvcdinfo.so.0 -> libvcdinfo.so.0.2.0
	libindicator.so.6 -> libindicator.so.6.0.0
	libmutter.so.0 -> libmutter.so.0.0.0
	libzbar.so.0 -> libzbar.so.0.2.0
	libnl.so.3 -> libnl.so.3.0.0
	libsvn_fs_fs-1.so.1 -> libsvn_fs_fs-1.so.1.0.0
	libindicate-gtk.so.3 -> libindicate-gtk.so.3.0.2
	libgstsdp-0.10.so.0 -> libgstsdp-0.10.so.0.24.0
	libflite_cmu_us_kal16.so.1 -> libflite_cmu_us_kal16.so.1.4
	libical.so.0 -> libical.so.0.44.0
	libspectre.so.1 -> libspectre.so.1.1.6
	libgdu-gtk.so.0 -> libgdu-gtk.so.0.0.0
	libgstsignalprocessor-0.10.so.0 -> libgstsignalprocessor-0.10.so.0.0.0
	libflite_cmulex.so.1 -> libflite_cmulex.so.1.4
	libbluetooth.so.3 -> libbluetooth.so.3.11.4
	libgnomecanvas-2.so.0 -> libgnomecanvas-2.so.0.3000.3
	libgstnetbuffer-0.10.so.0 -> libgstnetbuffer-0.10.so.0.24.0
	libfftw3l.so.3 -> libfftw3l.so.3.2.4
	libwx_gtk2u_xrc-2.8.so.0 -> libwx_gtk2u_xrc-2.8.so.0.7.0
	libnm-gtk.so.0 -> libnm-gtk.so.0.0.0
	libsidplay.so.1 -> libsidplay.so.1.0.3
	libhpip.so.0 -> libhpip.so.0.0.1
	libgstnet-0.10.so.0 -> libgstnet-0.10.so.0.29.0
	libthreadutil.so.2 -> libthreadutil.so.2.2.3
	libgstriff-0.10.so.0 -> libgstriff-0.10.so.0.24.0
	liblockfile.so.1 -> liblockfile.so.1.0
	libnautilus-extension.so.1 -> libnautilus-extension.so.1.4.0
	libgraph.so.4 -> libgraph.so.4.0.0
	libisofs.so.6 -> libisofs.so.6.50.0
	libglibmm-2.4.so.1 -> libglibmm-2.4.so.1.3.0
	libmtdev.so.1 -> libmtdev.so.1.0.0
	libmpcdec.so.6 -> libmpcdec.so.6.1.0
	libgrove.so.1 -> libgrove.so.1.0.3
	libaspell.so.15 -> libaspell.so.15.1.4
	libgtkspell3.so.0 -> libgtkspell3.so.0.0.0
	libgmime-2.4.so.2 -> libgmime-2.4.so.2.4.26
	liblirc_client.so.0 -> liblirc_client.so.0.2.1
	libwx_gtk2u_media-2.8.so.0 -> libwx_gtk2u_media-2.8.so.0.7.0
	libapt-pkg.so.4.11 -> libapt-pkg.so.4.11.0
	libdvdread.so.4 -> libdvdread.so.4.1.3
	libgnome-keyring.so.0 -> libgnome-keyring.so.0.1.1
	libencfs.so.6 -> libencfs.so.6.0.1
	libxml2.so.2 -> libxml2.so.2.7.8
	libedataserver-1.2.so.15 -> libedataserver-1.2.so.15.0.0
	libbonobo-2.so.0 -> libbonobo-2.so.0.0.0
	libxdo.so.2 -> libxdo.so.2
	libnux-1.0.so.0 -> libnux-1.0.so.0.1400.0
	libpeas-1.0.so.0 -> libpeas-1.0.so.0.200.0
	libgphoto2_port.so.0 -> libgphoto2_port.so.0.8.0
	libpanel-applet-4.so.0 -> libpanel-applet-4.so.0.0.2
	libelf.so.1 -> libelf-0.152.so
	libpanelw.so.5 -> libpanelw.so.5.9
	libgeoclue.so.0 -> libgeoclue.so.0.0.0
	libdecoration.so.0 -> libdecoration.so.0.0.0
	libformw.so.5 -> libformw.so.5.9
	libmpfr.so.4 -> libmpfr.so.4.0.1
	libwx_baseu-2.8.so.0 -> libwx_baseu-2.8.so.0.7.0
	libkeybinder.so.0 -> libkeybinder.so.0.0.1
	libXvMCW.so.1 -> libXvMCW.so.1.0.0
	libpurple.so.0 -> libpurple.so.0.10.0
	liblwres.so.60 -> liblwres.so.60.0.1
	libgettextpo.so.0 -> libgettextpo.so.0.5.1
	libvpx.so.0 -> libvpx.so.0.9.6
	libflite_cmu_us_kal.so.1 -> libflite_cmu_us_kal.so.1.4
	libnetsnmp.so.15 -> libnetsnmp.so.15.1.2
	libwps-0.2.so.2 -> libwps-0.2.so.2.0.2
	libslp.so.1 -> libslp.so.1.0.1
	libicuio.so.44 -> libicuio.so.44.2
	libsvn_fs_base-1.so.1 -> libsvn_fs_base-1.so.1.0.0
	libform.so.5 -> libform.so.5.9
	libXRes.so.1 -> libXRes.so.1.0.0
	libmusicbrainz.so.4 -> libmusicbrainz.so.4.0.3
	libhpmud.so.0 -> libhpmud.so.0.0.6
	libutempter.so.0 -> libutempter.so.1.1.5
	libgtk-3.so.0 -> libgtk-3.so.0.200.0
	libchromeXvMCPro.so.1 -> libchromeXvMCPro.so.1.0.0
	libunique-1.0.so.0 -> libunique-1.0.so.0.100.6
	libsgutils2.so.2 -> libsgutils2.so.2.0.0
	libGeoIPUpdate.so.0 -> libGeoIPUpdate.so.0.0.0
	libgvnc-1.0.so.0 -> libgvnc-1.0.so.0.0.1
	libmythes-1.2.so.0 -> libmythes-1.2.so.0.0.0
	libgcr-3.so.1 -> libgcr-3.so.1.0.0
	libpython2.7.so.1.0 -> libpython2.7.so.1.0
	libjbig2dec.so.0 -> libjbig2dec.so.0.0.0
	libwx_gtk2u_gl-2.8.so.0 -> libwx_gtk2u_gl-2.8.so.0.7.0
	libgstbasecamerabinsrc-0.10.so.0 -> libgstbasecamerabinsrc-0.10.so.0.0.0
	libvte.so.9 -> libvte.so.9.2800.2
	libwbclient.so.0 -> libwbclient.so.0
	libwx_gtk2u_richtext-2.8.so.0 -> libwx_gtk2u_richtext-2.8.so.0.7.0
	libbrasero-burn3.so.1 -> libbrasero-burn3.so.1.2.0
	libfontenc.so.1 -> libfontenc.so.1.0.0
	libiculx.so.44 -> libiculx.so.44.2
	libibus-1.0.so.0 -> libibus-1.0.so.0.0.0
	libfam.so.0 -> libfam.so.0.0.0
	libpoppler.so.13 -> libpoppler.so.13.0.0
	libwnck-3.so.0 -> libwnck-3.so.0.1.0
	libwx_gtk2u_stc-2.8.so.0 -> libwx_gtk2u_stc-2.8.so.0.7.0
	libkate.so.1 -> libkate.so.1.2.1
	libexiv2.so.10 -> libexiv2.so.10.0.1
	libflite_cmu_time_awb.so.1 -> libflite_cmu_time_awb.so.1.4
	libicalvcal.so.0 -> libicalvcal.so.0.44.0
	libixml.so.2 -> libixml.so.2.0.4
	libpangomm-1.4.so.1 -> libpangomm-1.4.so.1.0.30
	libdotconf-1.0.so.0 -> libdotconf-1.0.so.0.10.4
	libwx_gtk2u_svg-2.8.so.0 -> libwx_gtk2u_svg-2.8.so.0.7.0
	liblaunchpad-integration-3.0.so.1 -> liblaunchpad-integration-3.0.so.1.0.0
	libsvn_fs_util-1.so.1 -> libsvn_fs_util-1.so.1.0.0
	libgstrtsp-0.10.so.0 -> libgstrtsp-0.10.so.0.24.0
	libgpm.so.2 -> libgpm.so.2.0.0
	libgtkmm-3.0.so.1 -> libgtkmm-3.0.so.1.1.0
	libpaper.so.1 -> libpaper.so.1.1.2
	libzeitgeist-1.0.so.1 -> libzeitgeist-1.0.so.1.0.4
	libportSMF.so.0 -> libportSMF.so.0.0.0
	libtag.so.1 -> libtag.so.1.7.0
	libnewt.so.0.52 -> libnewt.so.0.52.11
	libdirectfb-1.2.so.9 -> libdirectfb-1.2.so.9.0.1
	libopenobex.so.1 -> libopenobex.so.1.5.0
	libIDL-2.so.0 -> libIDL-2.so.0.0.0
	libyaml-0.so.2 -> libyaml-0.so.2.0.2
	libXaw.so.7 -> libXaw7.so.7.0.0
	libmimic.so.0 -> libmimic.so.0.0.1
	libhyphen.so.0 -> libhyphen.so.0.2.0
	libswscale.so.2 -> libswscale.so.2.0.0
	libjte.so.1 -> libjte.so.1.0.0
	libbfd-2.21.53-system.20110810.so -> libbfd-2.21.53-system.20110810.so
	libisc.so.62 -> libisc.so.62.1.1
	libmission-control-plugins.so.0 -> libmission-control-plugins.so.0.3.0
	libnetsnmpmibs.so.15 -> libnetsnmpmibs.so.15.1.2
	libnux-image-1.0.so.0 -> libnux-image-1.0.so.0.1400.0
	libevdocument3.so.3 -> libevdocument3.so.3.0.0
	libopcodes-2.21.53-system.20110810.so -> libopcodes-2.21.53-system.20110810.so
	librsync.so.1 -> librsync.so.1.0.2
	libutouch-evemu.so.1 -> libutouch-evemu.so.1.0.0
	libsvn_repos-1.so.1 -> libsvn_repos-1.so.1.0.0
	libmetacity-private.so.0 -> libmetacity-private.so.0.0.0
	libva-x11.so.1 -> libva-x11.so.1.0.12
	liboverlay-scrollbar3-0.2.so.0 -> liboverlay-scrollbar3-0.2.so.0.0.11
	libhal.so.1 -> libhal.so.1.0.0
	libsvn_ra_svn-1.so.1 -> libsvn_ra_svn-1.so.1.0.0
	libcgraph.so.5 -> libcgraph.so.5.0.0
	libSDL_image-1.2.so.0 -> libSDL_image-1.2.so.0.8.2
	libwx_baseu_net-2.8.so.0 -> libwx_baseu_net-2.8.so.0.7.0
	libI810XvMC.so.1 -> libI810XvMC.so.1.0.0
	libisccc.so.60 -> libisccc.so.60.0.0
	libxcb-util.so.0 -> libxcb-util.so.0.0.0
	libprotobuf.so.7 -> libprotobuf.so.7.0.0
	libgee.so.2 -> libgee.so.2.0.0
	libsvn_ra_local-1.so.1 -> libsvn_ra_local-1.so.1.0.0
	libmozjs185.so.1.0 -> libmozjs185.so.1.0.0
	libdvdnavmini.so.4 -> libdvdnavmini.so.4.1.3
	libwpg-0.2.so.2 -> libwpg-0.2.so.2.0.0
	libboost_serialization.so.1.46.1 -> libboost_serialization.so.1.46.1
	libdjvulibre.so.21 -> libdjvulibre.so.21.3.0
	libuniquewm-1.2.so.9 -> libuniquewm-1.2.so.9.0.1
	libnice.so.10 -> libnice.so.10.0.0
	libmenu.so.5 -> libmenu.so.5.9
	libwnck-1.so.22 -> libwnck-1.so.22.3.31
	libcdio_cdda.so.0 -> libcdio_cdda.so.0.0.5
	libcamel-provider-1.2.so.29 -> libcamel-provider-1.2.so.29.0.0
	libgjs-dbus.so.0 -> libgjs-dbus.so.0.0.0
	libgstdataprotocol-0.10.so.0 -> libgstdataprotocol-0.10.so.0.29.0
	libtotem-plparser.so.17 -> libtotem-plparser.so.17.0.1
	libXtst.so.6 -> libXtst.so.6.1.0
	libgsttag-0.10.so.0 -> libgsttag-0.10.so.0.24.0
	libgucharmap_2_90.so.7 -> libgucharmap_2_90.so.7.0.0
	libgtkhtml-4.0.so.0 -> libgtkhtml-4.0.so.0.0.0
	libgpgme-pthread.so.11 -> libgpgme-pthread.so.11.7.0
	libevview3.so.3 -> libevview3.so.3.0.0
	libdconf.so.0 -> libdconf.so.0.0.0
	libwx_gtk2u_plot-2.8.so.0 -> libwx_gtk2u_plot-2.8.so.0.7.0
	libvlccore.so.4 -> libvlccore.so.4.0.3
	libgnome-bluetooth.so.8 -> libgnome-bluetooth.so.8.0.0
	libedata-cal-1.2.so.13 -> libedata-cal-1.2.so.13.0.0
	libpostproc.so.52 -> libpostproc.so.52.0.0
	libminiupnpc.so.5 -> libminiupnpc.so.5
	libavc1394.so.0 -> libavc1394.so.0.3.0
	libutouch-geis.so.1 -> libutouch-geis.so.1.2.0
	libgdiplus.so.0 -> libgdiplus.so.0.0.0
	libwx_gtk2u_fl-2.8.so.0 -> libwx_gtk2u_fl-2.8.so.0.7.0
	libgdk-3.so.0 -> libgdk-3.so.0.200.0
	libtheora.so.0 -> libtheora.so.0.3.10
	libopencore-amrwb.so.0 -> libopencore-amrwb.so.0.0.2
	libwx_gtk2u_gizmos_xrc-2.8.so.0 -> libwx_gtk2u_gizmos_xrc-2.8.so.0.7.0
	libavcodec.so.53 -> libavcodec.so.53.5.0
	libgweather-3.so.0 -> libgweather-3.so.0.0.3
	libcaca.so.0 -> libcucul.so.0.99.17
	libWildMidi.so.1 -> libWildMidi.so.1.0.2
	libFS.so.6 -> libFS.so.6.0.0
	librasqal.so.3 -> librasqal.so.3.0.0
	libXpm.so.4 -> libXpm.so.4.11.0
	libgd.so.2 -> libgd.so.2.0.0
	libXxf86dga.so.1 -> libXxf86dga.so.1.0.0
	libiso9660.so.7 -> libiso9660.so.7.0.0
	libXfont.so.1 -> libXfont.so.1.4.1
	libaccountsservice.so.0 -> libaccountsservice.so.0.0.0
	libcdt.so.4 -> libcdt.so.4.0.0
	libgwibber.so.2 -> libgwibber.so.2.0.0
	libicule.so.44 -> libicule.so.44.2
	libtextcat.so.0 -> libtextcat.so.0.0.0
	libdirac_encoder.so.0 -> libdirac_encoder.so.0.1.0
	libmenuw.so.5 -> libmenuw.so.5.9
	libebook-1.2.so.12 -> libebook-1.2.so.12.3.1
	libsvn_client-1.so.1 -> libsvn_client-1.so.1.0.0
	libwx_gtk2u_qa-2.8.so.0 -> libwx_gtk2u_qa-2.8.so.0.7.0
	libshout.so.3 -> libshout.so.3.2.0
	libpolkit-gtk-1.so.0 -> libpolkit-gtk-1.so.0.0.0
	libticw.so.5 -> libticw.so.5.9
	libaprutil-1.so.0 -> libaprutil-1.so.0.3.12
	libapr-1.so.0 -> libapr-1.so.0.4.5
	libgettextsrc-0.18.1.so -> libgettextsrc.so
	libtheoradec.so.1 -> libtheoradec.so.1.1.4
	libgstfarsight-0.10.so.0 -> libgstfarsight-0.10.so.0.9.0
	libcolamd.so.2.7.1 -> libcolamd.so.2.7.1
	libgjs-gdbus.so.0 -> libgjs-gdbus.so.0.0.0
	libexslt.so.0 -> libexslt.so.0.8.15
	libgtk-vnc-2.0.so.0 -> libgtk-vnc-2.0.so.0.0.2
	libaa.so.1 -> libaa.so.1.0.4
	libsnmp.so.15 -> libsnmp.so.15.1.2
	libwx_gtk2u_core-2.8.so.0 -> libwx_gtk2u_core-2.8.so.0.7.0
	libbind9.so.60 -> libbind9.so.60.0.4
	libgnome-menu-3.so.0 -> libgnome-menu-3.so.0.0.0
	libnl-nf.so.3 -> libnl-nf.so.3.0.0
	libnetsnmpagent.so.15 -> libnetsnmpagent.so.15.1.2
	libgphoto2.so.2 -> libgphoto2.so.2.4.0
	libicudata.so.44 -> libicudata.so.44.2
	libgnomevfs-2.so.0 -> libgnomevfs-2.so.0.2400.4
	librdf.so.0 -> librdf.so.0.0.0
	libatkmm-1.6.so.1 -> libatkmm-1.6.so.1.1.0
	libgstvideo-0.10.so.0 -> libgstvideo-0.10.so.0.24.0
	libecryptfs.so.0 -> libecryptfs.so.0.0.0
	libebml.so.3 -> libebml.so.3
	libQtDee.so.2 -> libQtDee.so.2.0.0
	libflite_cmu_us_rms.so.1 -> libflite_cmu_us_rms.so.1.4
	libmtp.so.9 -> libmtp.so.9.0.0
	libflite_usenglish.so.1 -> libflite_usenglish.so.1.4
	libfftw3l_threads.so.3 -> libfftw3l_threads.so.3.2.4
	libSDL-1.2.so.0 -> libSDL-1.2.so.0.11.3
	libclutter-gtk-1.0.so.0 -> libclutter-gtk-1.0.so.0.0.0
	libimobiledevice.so.2 -> libimobiledevice.so.2.0.1
	libgoa-backend-1.0.so.0 -> libgoa-backend-1.0.so.0.0.0
	libdconf-dbus-1.so.0 -> libdconf-dbus-1.so.0.0.0
	libgpgme.so.11 -> libgpgme.so.11.7.0
	libenchant.so.1 -> libenchant.so.1.6.0
	libwmflite-0.2.so.7 -> libwmflite-0.2.so.7.0.1
	libgck-1.so.0 -> libgck-1.so.0.0.0
	libpyglib-gi-2.0-python2.6.so.0 -> libpyglib-gi-2.0-python2.6.so.0.0.0
	libavutil.so.51 -> libavutil.so.51.7.0
	libicutest.so.44 -> libicutest.so.44.2
	librarian.so.0 -> librarian.so.0.0.0
	libofa.so.0 -> libofa.so.0.0.0
	libtotem-plparser-mini.so.17 -> libtotem-plparser-mini.so.17.0.1
	libboost_system.so.1.46.1 -> libboost_system.so.1.46.1
	libavformat.so.53 -> libavformat.so.53.2.0
	libicuuc.so.44 -> libicuuc.so.44.2
	libusbmuxd.so.1 -> libusbmuxd.so.1.0.7
	libstartup-notification-1.so.0 -> libstartup-notification-1.so.0.0.0
	libraw1394.so.11 -> libraw1394.so.11.0.1
	libtidy-0.99.so.0 -> libtidy.so
	libgdu.so.0 -> libgdu.so.0.0.0
	libyelp.so.0 -> libyelp.so.0.0.0
	libcroco-0.6.so.3 -> libcroco-0.6.so.3.0.1
	libguile-srfi-srfi-60-v-2.so.2 -> libguile-srfi-srfi-60-v-2.so.2.0.2
	libpoppler-glib.so.6 -> libpoppler-glib.so.6.0.0
	liblzma.so.2 -> liblzma.so.2.0.0
	libtheoraenc.so.1 -> libtheoraenc.so.1.1.2
	libgladeui-2.so.0 -> libgladeui-2.so.0.0.0
	libgs.so.9 -> libgs.so.9.04
	libsvn_ra-1.so.1 -> libsvn_ra-1.so.1.0.0
	libmodplug.so.1 -> libmodplug.so.1.0.0
	libunity-core-4.0.so.4 -> libunity-core-4.0.so.4.0.0
	libraptor2.so.0 -> libraptor2.so.0.0.0
	libgnome-2.so.0 -> libgnome-2.so.0.3200.1
	libpyglib-2.0-python2.6.so.0 -> libpyglib-2.0-python2.6.so.0.0.0
	libgtksourceview-3.0.so.0 -> libgtksourceview-3.0.so.0.0.0
	libgnome-media-profiles-3.0.so.0 -> libgnome-media-profiles-3.0.so.0.0.0
	libgstbasevideo-0.10.so.0 -> libgstbasevideo-0.10.so.0.0.0
	libbonoboui-2.so.0 -> libbonoboui-2.so.0.0.0
	libfaad.so.2 -> libfaad.so.2.0.0
	libdaemon.so.0 -> libdaemon.so.0.5.0
	libtotem.so.0 -> libtotem.so.0.0.0
	libwpd-0.9.so.9 -> libwpd-0.9.so.9.0.2
	libglade-2.0.so.0 -> libglade-2.0.so.0.0.7
	libgdkmm-3.0.so.1 -> libgdkmm-3.0.so.1.1.0
	libnl-cli.so.3 -> libnl-cli.so.3.0.0
	liblaunchpad-integration.so.1 -> liblaunchpad-integration.so.1.0.0
	libburn.so.4 -> libburn.so.4.65.0
	libpeas-gtk-1.0.so.0 -> libpeas-gtk-1.0.so.0.200.0
	libgnomekbdui.so.7 -> libgnomekbdui.so.7.0.0
	libid3tag.so.0 -> libid3tag.so.0.3.0
	libicui18n.so.44 -> libicui18n.so.44.2
	libcamel-1.2.so.29 -> libcamel-1.2.so.29.0.0
	libprotoc.so.7 -> libprotoc.so.7.0.0
	libunique-3.0.so.0 -> libunique-3.0.so.0.0.0
	libXmu.so.6 -> libXmu.so.6.2.0
	libORBitCosNaming-2.so.0 -> libORBitCosNaming-2.so.0.1.0
	libgoa-1.0.so.0 -> libgoa-1.0.so.0.0.0
	libgdkmm-2.4.so.1 -> libgdkmm-2.4.so.1.1.0
	libgexiv2.so.0 -> libgexiv2.so.0.0.0
	libdevhelp-3.so.0 -> libdevhelp-3.so.0.0.0
	libept.so.1 -> libept.so.1.0.5
	libgsm.so.1 -> libgsm.so.1.0.12
	libcairomm-1.0.so.1 -> libcairomm-1.0.so.1.4.0
	libsvn_subr-1.so.1 -> libsvn_subr-1.so.1.0.0
	libapt-inst.so.1.3 -> libapt-inst.so.1.3.0
	libgnome-menu.so.2 -> libgnome-menu.so.2.4.13
	libicalss.so.0 -> libicalss.so.0.44.0
	libtelepathy-farsight.so.0 -> libtelepathy-farsight.so.0.1.6
	libwebkitgtk-1.0.so.0 -> libwebkitgtk-1.0.so.0.7.3
	libbonobo-activation.so.4 -> libbonobo-activation.so.4.0.0
	librlog.so.5 -> librlog.so.5.0.0
	libcelt0.so.0 -> libcelt0.so.0.0.0
	libasprintf.so.0 -> libasprintf.so.0.0.0
	libtelepathy-logger.so.2 -> libtelepathy-logger.so.2.2.0
	libGLEWmx.so.1.5 -> libGLEWmx.so.1.5.2
	libpyglib-gi-2.0-python2.7.so.0 -> libpyglib-gi-2.0-python2.7.so.0.0.0
	libappindicator3.so.1 -> libappindicator3.so.1.0.0
	libgpgme-pth.so.11 -> libgpgme-pth.so.11.7.0
	libyajl.so.1 -> libyajl.so.1.0.12
	libarchive.so.2 -> libarchive.so.2.8.4
	libnm-util.so.2 -> libnm-util.so.2.1.0
	libts-0.0.so.0 -> libts-0.0.so.0.1.1
	libdbusmenu-glib.so.4 -> libdbusmenu-glib.so.4.0.5
	libgmp.so.10 -> libgmp.so.10.0.1
	libsvn_fs-1.so.1 -> libsvn_fs-1.so.1.0.0
	libfribidi.so.0 -> libfribidi.so.0.3.1
	libcdda_interface.so.0 -> libcdda_interface.so.0.10.2
	libx264.so.116 -> libx264.so.116
	libXp.so.6 -> libXp.so.6.2.0
	libspgrove.so.1 -> libspgrove.so.1.0.3
	libunity-misc.so.4 -> libunity-misc.so.4.1.0
	libupower-glib.so.1 -> libupower-glib.so.1.0.1
	libsvn_wc-1.so.1 -> libsvn_wc-1.so.1.0.0
	libatspi.so.0 -> libatspi.so.0.0.1
	libgnome-control-center.so.1 -> libgnome-control-center.so.1.0.0
	libgssdp-1.0.so.2 -> libgssdp-1.0.so.2.0.0
	libcdio.so.10 -> libcdio.so.10.0.0
	libvisual-0.4.so.0 -> libvisual-0.4.so.0.0.0
	libmysqlclient.so.16 -> libmysqlclient.so.16.0.0
	libcdaudio.so.1 -> libcdaudio.so.1.0.0
	libdconf-qt.so.0 -> libdconf-qt.so.0.0.0
	libexempi.so.3 -> libexempi.so.3.2.1
	libfftw3f_threads.so.3 -> libfftw3f_threads.so.3.2.4
	libopencore-amrnb.so.0 -> libopencore-amrnb.so.0.0.2
	libgpod.so.4 -> libgpod.so.4.3.1
	libpolkit-gobject-1.so.0 -> libpolkit-gobject-1.so.0.0.0
	libcdio_paranoia.so.0 -> libcdio_paranoia.so.0.0.3
	libhal-storage.so.1 -> libhal-storage.so.1.0.0
	libgstcontroller-0.10.so.0 -> libgstcontroller-0.10.so.0.29.0
	libpolkit-backend-1.so.0 -> libpolkit-backend-1.so.0.0.0
	libchromeXvMC.so.1 -> libchromeXvMC.so.1.0.0
	libdirect-1.2.so.9 -> libdirect-1.2.so.9.0.1
	libnatpmp.so.1 -> libnatpmp.so.1
	libquvi.so.0 -> libquvi.so.0.4.0
	libutouch-grail.so.1 -> libutouch-grail.so.1.1.0
	libgstrtp-0.10.so.0 -> libgstrtp-0.10.so.0.24.0
	libwx_gtk2u_aui-2.8.so.0 -> libwx_gtk2u_aui-2.8.so.0.7.0
	libstyle.so.1 -> libstyle.so.1.0.3
	libdvdcss.so.2 -> libdvdcss.so.2.1.0
	libneon-gnutls.so.27 -> libneon-gnutls.so.27.2.6
	libedataserverui-3.0.so.1 -> libedataserverui-3.0.so.1.0.0
	libindicate.so.5 -> libindicate.so.5.0.5
	libsvn_auth_kwallet-1.so.1 -> libsvn_auth_kwallet-1.so.1.0.0
	libwx_baseu_xml-2.8.so.0 -> libwx_baseu_xml-2.8.so.0.7.0
	liborc-0.4.so.0 -> liborc-0.4.so.0.14.0
	libschroedinger-1.0.so.0 -> libschroedinger-1.0.so.0.10.0
	libpth.so.20 -> libpth.so.20.0.27
	libwmf-0.2.so.7 -> libwmf-0.2.so.7.1.0
	libGeoIP.so.1 -> libGeoIP.so.1.4.8
	libmatroska.so.4 -> libmatroska.so.4
	libedata-book-1.2.so.11 -> libedata-book-1.2.so.11.0.0
	libORBit-imodule-2.so.0 -> libORBit-imodule-2.so.0.0.0
	libcanberra-gtk3.so.0 -> libcanberra-gtk3.so.0.1.8
	libmp3lame.so.0 -> libmp3lame.so.0.0.0
	libsvn_diff-1.so.1 -> libsvn_diff-1.so.1.0.0
	libindicator3.so.6 -> libindicator3.so.6.0.0
	libgupnp-igd-1.0.so.3 -> libgupnp-igd-1.0.so.3.0.4
	libespeak.so.1 -> libespeak.so.1.1.45
	libcdda_paranoia.so.0 -> libcdda_paranoia.so.0.10.2
	libgupnp-1.0.so.3 -> libgupnp-1.0.so.3.0.0
	libguile-srfi-srfi-1-v-3.so.3 -> libguile-srfi-srfi-1-v-3.so.3.0.2
	libgtkspell.so.0 -> libgtkspell.so.0.0.0
	libsoup-2.4.so.1 -> libsoup-2.4.so.1.4.0
	libcaca++.so.0 -> libcucul++.so.0.99.17
	libflite_cmu_us_slt.so.1 -> libflite_cmu_us_slt.so.1.4
	libopencc.so.1 -> libopencc.so.1.0.0
	liborc-test-0.4.so.0 -> liborc-test-0.4.so.0.14.0
	libglibmm_generate_extra_defs-2.4.so.1 -> libglibmm_generate_extra_defs-2.4.so.1.3.0
	libnetsnmphelpers.so.15 -> libnetsnmphelpers.so.15.1.2
	libspeechd.so.2 -> libspeechd.so.2.3.0
	libfftw3f.so.3 -> libfftw3f.so.3.2.4
	libdvbpsi.so.7 -> libdvbpsi.so.7.0.0
	libwebkitgtk-3.0.so.0 -> libwebkitgtk-3.0.so.0.7.3
	libnux-core-1.0.so.0 -> libnux-core-1.0.so.0.1400.0
	libdv.so.4 -> libdv.so.4.0.3
	libdc1394.so.22 -> libdc1394.so.22.1.5
	libmpeg2.so.0 -> libmpeg2.so.0.0.0
	libt1.so.5 -> libt1.so.5.1.2
	libgstinterfaces-0.10.so.0 -> libgstinterfaces-0.10.so.0.24.0
	libgstpbutils-0.10.so.0 -> libgstpbutils-0.10.so.0.24.0
	libkpathsea.so.5 -> libkpathsea.so.5.0.0
	libguilereadline-v-17.so.17 -> libguilereadline-v-17.so.17.0.3
	libgstphotography-0.10.so.0 -> libgstphotography-0.10.so.0.0.0
	libmpeg2convert.so.0 -> libmpeg2convert.so.0.0.0
	libhunspell-1.2.so.0 -> libhunspell-1.2.so.0.0.0
	libmad.so.0 -> libmad.so.0.2.1
	libdbusmenu-gtk.so.4 -> libdbusmenu-gtk.so.4.0.5
	libpolkit-agent-1.so.0 -> libpolkit-agent-1.so.0.0.0
	libxkbfile.so.1 -> libxkbfile.so.1.0.2
	libnm-glib.so.4 -> libnm-glib.so.4.2.0
	libunistring.so.0 -> libunistring.so.0.1.2
	libunity-2d-private.so.0 -> libunity-2d-private.so.0.0.0
	libgtkmm-2.4.so.1 -> libgtkmm-2.4.so.1.1.0
	libfolks-telepathy.so.25 -> libfolks-telepathy.so.25.2.2
	libgif.so.4 -> libungif.so.4.1.6
	libbrasero-media3.so.1 -> libbrasero-media3.so.1.2.0
	libxcb-keysyms.so.1 -> libxcb-keysyms.so.1.0.0
	libportaudio.so.2 -> libportaudio.so.2.0.0
	libXmuu.so.1 -> libXmuu.so.1.0.0
	libnm-glib-vpn.so.1 -> libnm-glib-vpn.so.1.1.0
	libdbusmenu-gtk3.so.4 -> libdbusmenu-gtk3.so.4.0.5
	libgrip.so.0 -> libgrip.so.0.302.0
	libwx_gtk2u_html-2.8.so.0 -> libwx_gtk2u_html-2.8.so.0.7.0
	libgnome-desktop-3.so.2 -> libgnome-desktop-3.so.2.0.1
	libbrasero-utils3.so.1 -> libbrasero-utils3.so.1.2.0
	libubuntuone-1.0.so.1 -> libubuntuone-1.0.so.1.0.0
	libgconf-2.so.4 -> libgconf-2.so.4.1.5
	libguile.so.17 -> libguile.so.17.4.0
	libgtksourceview-2.0.so.0 -> libgtksourceview-2.0.so.0.0.0
	libxklavier.so.16 -> libxklavier.so.16.1.0
	libnl-genl.so.3 -> libnl-genl.so.3.0.0
	libQtBamf.so.1 -> libQtBamf.so.1.0.0
	libwavpack.so.1 -> libwavpack.so.1.1.4
/usr/lib/i386-linux-gnu/sse2: (hwcap: 0x0000000004000000)
	libspeexdsp.so.1 -> libspeexdsp.so.1.5.0

```

Appreciate the help. Not entirely sure how to interpret above, completely out of my depth at this point!

---

### Post by Toz on 2011-10-18
Here is how I compiled liferea-1.8-RC1 ([http://sourceforge.net/projects/liferea/files/Liferea%20Unstable/1.8-RC1/liferea-1.8-RC1.tar.gz/download]("http://sourceforge.net/projects/liferea/files/Liferea%20Unstable/1.8-RC1/liferea-1.8-RC1.tar.gz/download")):
```
sudo apt-get install build-essential intltool libgtk2.0-dev libgconf2-dev libunique-dev libxml2-dev libxslt-dev libsqlite3-dev libwebkit-dev libjson-glib-dev
./configure
make
sudo make install

```

---

### Post by jb5 on 2011-10-18
Ah - Thanks. :popcorn:

Appears I was missing  libunique-dev   !!!

Is there some way I could have determined what exactly was missing, either from ldconfig or some other command?

---

### Post by Toz on 2011-10-18
Actually, the README file in the main source directory lists the required dependencies. I did have to figure out though that gtk2 meant libgtk2.0, gconf2 meant libgconf2 and sqlite3 meant libsqlite3. I just used apt-cache search to figure out what the actual ubuntu package names were.

---

### Post by jb5 on 2011-10-18
I did look in the README file, I just didn't fully comprehend it. :)

I didn't realise I needed to add the lib-prefix & assorted suffixes etc.   for each of the library dependences. 
I kept stumbling at the first requirement, gtk2; it wasn't clear if I had met the minimum dependency even checking via synaptic.


```
3.1 Dependencies
----------------

The library dependencies for Liferea are: 


   gtk2, gconf2, libunique, libxml2, libxslt, sqlite3,
   libwebkit and libjson-glib
   
   
Ensure that you have installed the libraries and there headers.
If you use distribution packages then you usually need to install
a package named like the library and one with a suffix "-dev" or
"-devel". You need both to compile Liferea.
```

I suppose the ```
No package 'unique-1.0' found
``` in the original configure error message should have tipped me off, or at least given me something else to search for! (Hindsight, wonderful thing!)

---

### Post by azmyth on 2011-10-18
Sometimes a config.log file is generated so you can grep it as it'll usually tell you what it was looking for before it kicked out the error. Then you'll want to use apt-file search xxx to try to figure out the package you need.

---

