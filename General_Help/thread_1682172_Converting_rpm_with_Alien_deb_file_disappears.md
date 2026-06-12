---
title: "Converting rpm with Alien: deb file disappears"
date: 2011-02-05
forum: General Help
---

### Post by pingtoft on 2011-02-05
On Ubuntu 10.10 with Alien 8.81 I do a
```
sudo alien -dvc ICAClient-11.0-1.i386.rpm
```
(out below)

The file deb file appears for a moment but is then removed.
I have used Alien before without any problems and I have no idea what I'm doing wrong :confused:

```
	LANG=C rpm -qp --queryformat %{NAME} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qp --queryformat %{VERSION} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qp --queryformat %{RELEASE} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qp --queryformat %{ARCH} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qp --queryformat %{SUMMARY} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qp --queryformat %{DESCRIPTION} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qp --queryformat %{PREFIXES} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qp --queryformat %{POSTIN} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qp --queryformat %{POSTUN} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qp --queryformat %{PREUN} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qp --queryformat %{LICENSE} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qp --queryformat %{PREIN} ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qcp ICAClient-11.0-1.i386.rpm
	rpm -qpi ICAClient-11.0-1.i386.rpm
	LANG=C rpm -qpl ICAClient-11.0-1.i386.rpm
	mkdir ICAClient-11.0
	chmod 755 ICAClient-11.0
	rpm2cpio ICAClient-11.0-1.i386.rpm | lzma -t -q > /dev/null 2>&1
	rpm2cpio ICAClient-11.0-1.i386.rpm | (cd ICAClient-11.0;  cpio --extract --make-directories --no-absolute-filenames --preserve-modification-time) 2>&1
	chmod 755 ICAClient-11.0/./
	chmod 755 ICAClient-11.0/./usr
	chmod 755 ICAClient-11.0/./usr/lib
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient
	chmod 555 ICAClient-11.0//usr/lib/ICAClient
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/CHARICONV.DLL
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/CHARICONV.DLL
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/NDS.DLL
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/NDS.DLL
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/PDCRYPT1.DLL
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/PDCRYPT1.DLL
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/PDCRYPT2.DLL
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/PDCRYPT2.DLL
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/TW1.DLL
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/TW1.DLL
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/VDMM.DLL
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/VDMM.DLL
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/VDSCARD.DLL
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/VDSCARD.DLL
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/VDSPMIKE.DLL
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/VDSPMIKE.DLL
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/VDSSPI.DLL
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/VDSSPI.DLL
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/config
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config/.server
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/config/.server
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config/All_Regions.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/config/All_Regions.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config/Trusted_Region.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/config/Trusted_Region.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config/Unknown_Region.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/config/Unknown_Region.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config/Untrusted_Region.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/config/Untrusted_Region.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config/canonicalization.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/config/canonicalization.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config/regions.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/config/regions.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config/usertemplate
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/config/usertemplate
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config/usertemplate/All_Regions.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/config/usertemplate/All_Regions.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config/usertemplate/Trusted_Region.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/config/usertemplate/Trusted_Region.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config/usertemplate/Unknown_Region.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/config/usertemplate/Unknown_Region.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/config/usertemplate/Untrusted_Region.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/config/usertemplate/Untrusted_Region.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/desktop
	chmod 755 ICAClient-11.0//usr/lib/ICAClient/desktop
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/desktop/wfcmgr.desktop
	chmod 644 ICAClient-11.0//usr/lib/ICAClient/desktop/wfcmgr.desktop
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/help
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/help
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/icons
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/icons
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/icons/manager.xpm
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/icons/manager.xpm
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/icons/session.xpm
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/icons/session.xpm
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/keyboard
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/age2.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/age2.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/agex2.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/agex2.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/automatic.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/automatic.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/dcint401.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/dcint401.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/dcintpcx.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/dcintpcx.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/dcus401.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/dcus401.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/dcuspcx.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/dcuspcx.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/dec401.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/dec401.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/dec401uk.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/dec401uk.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/decpcx.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/decpcx.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/decpcxuk.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/decpcxuk.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/dg.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/dg.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/dgfr.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/dgfr.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/dggr.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/dggr.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/dguk.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/dguk.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/dgus.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/dgus.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hp101.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hp101.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpfritf.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpfritf.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpgritf.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpgritf.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpint101.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpint101.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpintps2.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpintps2.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpitf.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpitf.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpps2.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpps2.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpuk101.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpuk101.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpukitf.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpukitf.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpukps2.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpukps2.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpus101.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpus101.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpusitf.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpusitf.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpusps2.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/hpusps2.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/ibm.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/ibm.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/keyboard.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/keyboard.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/linux-ja.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/linux-ja.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/linux.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/linux.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/mac101.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/mac101.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/ncdn-101.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/ncdn-101.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/ncdn-102.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/ncdn-102.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/netbsd.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/netbsd.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/scoos5.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/scoos5.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/scouw2.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/scouw2.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sg.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sg.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sgindy.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sgindy.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sgindyfr.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sgindyfr.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sgindygr.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sgindygr.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sgindyuk.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sgindyuk.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sgindyus.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sgindyus.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sngr.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sngr.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparc3.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparc3.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparc4.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparc4.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparc5.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparc5.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparc6usb.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparc6usb.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcfr4.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcfr4.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcfr5.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcfr5.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcgr4.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcgr4.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcgr5.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcgr5.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcuk4.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcuk4.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcuk5.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcuk5.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcus3.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcus3.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcus4.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcus4.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcus5.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/sparcus5.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keyboard/trimodal.kbd
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keyboard/trimodal.kbd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keystore
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/keystore
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts/BTCTRoot.crt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts/BTCTRoot.crt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts/Class3PCA_G2_v2.crt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts/Class3PCA_G2_v2.crt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts/Class4PCA_G2_v2.crt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts/Class4PCA_G2_v2.crt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts/GTECTGlobalRoot.crt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts/GTECTGlobalRoot.crt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts/Pcs3ss_v4.crt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts/Pcs3ss_v4.crt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts/SecureServer.crt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/keystore/cacerts/SecureServer.crt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/libctxssl.so
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/libctxssl.so
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/libproxy.so
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/libproxy.so
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/de
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/Npica.ad
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/Npica.ad
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/Wfcmgr
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/Wfcmgr
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/Wfica
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/Wfica
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/XCapture.ad
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/XCapture.ad
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/eula.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/eula.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/install.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/install.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/pna.nls
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/pna.nls
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/readme.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/readme.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/setupwfc.msg
	chmod 644 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/setupwfc.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/wfcmgr.msg
	chmod 644 ICAClient-11.0//usr/lib/ICAClient/nls/de/UTF-8/wfcmgr.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/Wfcmgr
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/Wfcmgr
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/Wfica
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/Wfica
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/XCapture.ad
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/de/XCapture.ad
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/appsrv.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/appsrv.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/eula.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/eula.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/hinst.msg
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/de/hinst.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/index.htm
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/index.htm
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/install.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/install.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/module.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/module.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/pna.nls
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/de/pna.nls
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/readme.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/readme.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/setupwfc.msg
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/de/setupwfc.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/wfclient.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/wfclient.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/de/wfcmgr.msg
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/de/wfcmgr.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/en
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/Npica.ad
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/Npica.ad
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/Wfcmgr
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/Wfcmgr
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/Wfica
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/Wfica
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/XCapture.ad
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/XCapture.ad
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/eula.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/eula.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/install.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/install.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/pna.nls
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/pna.nls
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/readme.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/readme.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/setupwfc.msg
	chmod 644 ICAClient-11.0//usr/lib/ICAClient/nls/en/UTF-8/setupwfc.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/Wfcmgr
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/Wfcmgr
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/Wfica
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/Wfica
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/XCapture.ad
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/en/XCapture.ad
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/appsrv.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/appsrv.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/eula.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/eula.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/hinst.msg
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/en/hinst.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/index.htm
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/index.htm
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/install.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/install.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/module.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/module.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/pna.nls
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/en/pna.nls
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/readme.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/readme.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/setupwfc.msg
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/en/setupwfc.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/wfclient.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/wfclient.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/en/wfcmgr.msg
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/en/wfcmgr.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/ja
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/Npica.ad
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/Npica.ad
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/Wfcmgr
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/Wfcmgr
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/Wfica
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/Wfica
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/XCapture.ad
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/XCapture.ad
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/eula.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/eula.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/install.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/install.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/pna.nls
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/pna.nls
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/readme.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/readme.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/setupwfc.msg
	chmod 644 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/setupwfc.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/wfcmgr.msg
	chmod 644 ICAClient-11.0//usr/lib/ICAClient/nls/ja/UTF-8/wfcmgr.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/Wfcmgr
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/Wfcmgr
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/Wfica
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/Wfica
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/XCapture.ad
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/ja/XCapture.ad
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/appsrv.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/appsrv.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/eula.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/eula.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/hinst.msg
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/ja/hinst.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/index.htm
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/index.htm
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/install.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/install.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/module.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/module.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/pna.nls
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/ja/pna.nls
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/readme.txt
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/readme.txt
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/setupwfc.msg
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/nls/ja/setupwfc.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/wfclient.ini
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/wfclient.ini
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/nls/ja/wfcmgr.msg
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/nls/ja/wfcmgr.msg
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/npica.so
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/npica.so
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/util
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util/echo_cmd
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/util/echo_cmd
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util/gst_play
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/util/gst_play
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util/icalicense.sh
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/util/icalicense.sh
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util/integrate.sh
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/util/integrate.sh
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util/libgstflatstm.so
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/util/libgstflatstm.so
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util/nslaunch
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/util/nslaunch
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util/pac.js
	chmod 444 ICAClient-11.0//usr/lib/ICAClient/util/pac.js
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util/pacexec
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/util/pacexec
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util/sunraymac.sh
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/util/sunraymac.sh
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util/wfcmgr
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/util/wfcmgr
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util/what
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/util/what
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/util/xcapture
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/util/xcapture
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/wfcmgr.bin
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/wfcmgr.bin
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/wfica
	chmod 555 ICAClient-11.0//usr/lib/ICAClient/wfica
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/wfica.sh
	chmod 755 ICAClient-11.0//usr/lib/ICAClient/wfica.sh
	chown 0:0 ICAClient-11.0//usr/lib/ICAClient/wfica_assoc.sh
	chmod 755 ICAClient-11.0//usr/lib/ICAClient/wfica_assoc.sh
	mkdir ICAClient-11.0/debian
	hostname
	date -R
	hostname
	date -R
	chmod 755 ICAClient-11.0/debian/rules
	debian/rules binary 2>&1
icaclient_11.0-2_i386.deb generated
	find ICAClient-11.0 -type d -exec chmod 755 {} ;
	rm -rf ICAClient-11.0
```

---

### Post by GOROSSI on 2011-02-05
the c switch is your problem. 

try it without

---

### Post by pingtoft on 2011-02-05
I have tried '-d' and '-d --scripts' but neither makes a difference. :/

---

### Post by dino99 on 2011-02-05
sudo alien -k packagename.tar.gz

---

### Post by GOROSSI on 2011-02-05
i'll build it & see

---

### Post by GOROSSI on 2011-02-05
[http://www.ezunix.org/index.php?title=Install_Citrix_client_on_Ubuntu#Software]("http://www.ezunix.org/index.php?title=Install_Citrix_client_on_Ubuntu#Software")

read the above

---

### Post by pingtoft on 2011-02-05
I opted to install from the tarball in stead but I'm still confused why Alien acted the way it did.

Anyway, problem solved, so you don't have to waste any more time on my behalf.
Thanks for the help. :)

---

