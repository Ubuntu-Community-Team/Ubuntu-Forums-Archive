---
title: "Alien failing to correctly convert RPMs to DEBs (Canon MP160)"
date: 2011-04-07
forum: General Help
---

### Post by 0x90 on 2011-04-07
For some reason, the alien command is not letting me convert some RPMs that I have into DEBs. I need them for printer drivers for my server that is running Ubuntu Server 10.10.
Here is the command that I executed:
```
# alien --scripts --verbose *.rpm > output.log
```
Here is the verbose output of Alien for both of the packages:
```

	LANG=C rpm -qp --queryformat %{NAME} common.rpm
	LANG=C rpm -qp --queryformat %{VERSION} common.rpm
	LANG=C rpm -qp --queryformat %{RELEASE} common.rpm
	LANG=C rpm -qp --queryformat %{ARCH} common.rpm
	LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} common.rpm
	LANG=C rpm -qp --queryformat %{SUMMARY} common.rpm
	LANG=C rpm -qp --queryformat %{DESCRIPTION} common.rpm
	LANG=C rpm -qp --queryformat %{PREFIXES} common.rpm
	LANG=C rpm -qp --queryformat %{POSTIN} common.rpm
	LANG=C rpm -qp --queryformat %{POSTUN} common.rpm
	LANG=C rpm -qp --queryformat %{PREUN} common.rpm
	LANG=C rpm -qp --queryformat %{LICENSE} common.rpm
	LANG=C rpm -qp --queryformat %{PREIN} common.rpm
	LANG=C rpm -qcp common.rpm
	rpm -qpi common.rpm
	LANG=C rpm -qpl common.rpm
	mkdir cnijfilter-common-2.70
	chmod 755 cnijfilter-common-2.70
	rpm2cpio common.rpm | lzma -t -q > /dev/null 2>&1
	rpm2cpio common.rpm | (cd cnijfilter-common-2.70;  cpio --extract --make-directories --no-absolute-filenames --preserve-modification-time) 2>&1
	chmod 755 cnijfilter-common-2.70/./
	chmod 755 cnijfilter-common-2.70/./usr
	chmod 755 cnijfilter-common-2.70/./usr/local
	chmod 755 cnijfilter-common-2.70/./usr/local/bin
	chmod 755 cnijfilter-common-2.70/./usr/share
	chmod 755 cnijfilter-common-2.70/./usr/share/doc
	chmod 755 cnijfilter-common-2.70/./usr/lib
	chmod 755 cnijfilter-common-2.70/./usr/lib/cups
	chmod 755 cnijfilter-common-2.70/./usr/lib/cups/filter
	chmod 755 cnijfilter-common-2.70/./usr/lib/cups/backend
	chown 0:0 cnijfilter-common-2.70//usr/lib/cups/backend/cnij_usb
	chmod 755 cnijfilter-common-2.70//usr/lib/cups/backend/cnij_usb
	chown 0:0 cnijfilter-common-2.70//usr/lib/cups/filter/pstocanonij
	chmod 755 cnijfilter-common-2.70//usr/lib/cups/filter/pstocanonij
	chown 0:0 cnijfilter-common-2.70//usr/local/bin/cngpij
	chmod 755 cnijfilter-common-2.70//usr/local/bin/cngpij
	chown 0:0 cnijfilter-common-2.70//usr/share/doc/cnijfilter-common-2.70
	chmod 755 cnijfilter-common-2.70//usr/share/doc/cnijfilter-common-2.70
	chown 0:0 cnijfilter-common-2.70//usr/share/doc/cnijfilter-common-2.70/LICENSE-cnijfilter-2.70E.txt
	chmod 644 cnijfilter-common-2.70//usr/share/doc/cnijfilter-common-2.70/LICENSE-cnijfilter-2.70E.txt
	chown 0:0 cnijfilter-common-2.70//usr/share/doc/cnijfilter-common-2.70/LICENSE-cnijfilter-2.70J.txt
	chmod 644 cnijfilter-common-2.70//usr/share/doc/cnijfilter-common-2.70/LICENSE-cnijfilter-2.70J.txt
	mkdir cnijfilter-common-2.70/debian
	hostname
	date -R
	hostname
	date -R
	chmod 755 cnijfilter-common-2.70/debian/rules
	debian/rules binary 2>&1
cnijfilter-common_2.70-2_i386.deb generated
	find cnijfilter-common-2.70 -type d -exec chmod 755 {} ;
	rm -rf cnijfilter-common-2.70
	LANG=C rpm -qp --queryformat %{NAME} mp160.rpm
	LANG=C rpm -qp --queryformat %{VERSION} mp160.rpm
	LANG=C rpm -qp --queryformat %{RELEASE} mp160.rpm
	LANG=C rpm -qp --queryformat %{ARCH} mp160.rpm
	LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} mp160.rpm
	LANG=C rpm -qp --queryformat %{SUMMARY} mp160.rpm
	LANG=C rpm -qp --queryformat %{DESCRIPTION} mp160.rpm
	LANG=C rpm -qp --queryformat %{PREFIXES} mp160.rpm
	LANG=C rpm -qp --queryformat %{POSTIN} mp160.rpm
	LANG=C rpm -qp --queryformat %{POSTUN} mp160.rpm
	LANG=C rpm -qp --queryformat %{PREUN} mp160.rpm
	LANG=C rpm -qp --queryformat %{LICENSE} mp160.rpm
	LANG=C rpm -qp --queryformat %{PREIN} mp160.rpm
	LANG=C rpm -qcp mp160.rpm
	rpm -qpi mp160.rpm
	LANG=C rpm -qpl mp160.rpm
	mkdir cnijfilter-mp160-2.70
	chmod 755 cnijfilter-mp160-2.70
	rpm2cpio mp160.rpm | lzma -t -q > /dev/null 2>&1
	rpm2cpio mp160.rpm | (cd cnijfilter-mp160-2.70;  cpio --extract --make-directories --no-absolute-filenames --preserve-modification-time) 2>&1
	chmod 755 cnijfilter-mp160-2.70/./
	chmod 755 cnijfilter-mp160-2.70/./usr
	chmod 755 cnijfilter-mp160-2.70/./usr/local
	chmod 755 cnijfilter-mp160-2.70/./usr/local/bin
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/zh_TW
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/zh_TW/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/tr
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/tr/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/ko
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/ko/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/it
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/it/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/ja
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/ja/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/th
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/th/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/sv
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/sv/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/pl
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/pl/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/zh
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/zh/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/el
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/el/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/ru
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/ru/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/fr
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/fr/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/nl
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/nl/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/fi
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/fi/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/nb
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/nb/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/cs
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/cs/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/hu
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/hu/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/pt
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/pt/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/da
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/da/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/de
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/de/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/es
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/locale/es/LC_MESSAGES
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/printuimp160
	chmod 755 cnijfilter-mp160-2.70/./usr/local/share/cngpijmonmp160
	chmod 755 cnijfilter-mp160-2.70/./usr/share
	chmod 755 cnijfilter-mp160-2.70/./usr/share/cups
	chmod 755 cnijfilter-mp160-2.70/./usr/share/cups/model
	chmod 755 cnijfilter-mp160-2.70/./usr/lib
	chmod 755 cnijfilter-mp160-2.70/./usr/lib/bjlib
	chown 0:0 cnijfilter-mp160-2.70//usr/lib/bjlib/cifmp160.conf
	chmod 755 cnijfilter-mp160-2.70//usr/lib/bjlib/cifmp160.conf
	chown 0:0 cnijfilter-mp160-2.70//usr/lib/bjlib/cnb_2910.tbl
	chmod 755 cnijfilter-mp160-2.70//usr/lib/bjlib/cnb_2910.tbl
	chown 0:0 cnijfilter-mp160-2.70//usr/lib/bjlib/cnbpname291.tbl
	chmod 755 cnijfilter-mp160-2.70//usr/lib/bjlib/cnbpname291.tbl
	chown 0:0 cnijfilter-mp160-2.70//usr/lib/libcnbpcmcm291.so.6.50.1
	chmod 755 cnijfilter-mp160-2.70//usr/lib/libcnbpcmcm291.so.6.50.1
	chown 0:0 cnijfilter-mp160-2.70//usr/lib/libcnbpcnclapi291.so.3.3.0
	chmod 755 cnijfilter-mp160-2.70//usr/lib/libcnbpcnclapi291.so.3.3.0
	chown 0:0 cnijfilter-mp160-2.70//usr/lib/libcnbpcnclbjcmd291.so.3.3.0
	chmod 755 cnijfilter-mp160-2.70//usr/lib/libcnbpcnclbjcmd291.so.3.3.0
	chown 0:0 cnijfilter-mp160-2.70//usr/lib/libcnbpcnclui291.so.3.3.0
	chmod 755 cnijfilter-mp160-2.70//usr/lib/libcnbpcnclui291.so.3.3.0
	chown 0:0 cnijfilter-mp160-2.70//usr/lib/libcnbpess291.so.3.0.9
	chmod 755 cnijfilter-mp160-2.70//usr/lib/libcnbpess291.so.3.0.9
	chown 0:0 cnijfilter-mp160-2.70//usr/lib/libcnbpo291.so.1.0.4
	chmod 755 cnijfilter-mp160-2.70//usr/lib/libcnbpo291.so.1.0.4
	chown 0:0 cnijfilter-mp160-2.70//usr/local/bin/cifmp160
	chmod 755 cnijfilter-mp160-2.70//usr/local/bin/cifmp160
	chown 0:0 cnijfilter-mp160-2.70//usr/local/bin/cngpijmonmp160
	chmod 755 cnijfilter-mp160-2.70//usr/local/bin/cngpijmonmp160
	chown 0:0 cnijfilter-mp160-2.70//usr/local/bin/lgmonmp160
	chmod 755 cnijfilter-mp160-2.70//usr/local/bin/lgmonmp160
	chown 0:0 cnijfilter-mp160-2.70//usr/local/bin/printuimp160
	chmod 755 cnijfilter-mp160-2.70//usr/local/bin/printuimp160
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps
	chmod 755 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_15_Low.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_15_Low.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_15_Unknown.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_15_Unknown.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_16_Low.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_16_Low.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_16_Unknown.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_16_Unknown.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_Low.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_Low.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_Out.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_Out.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_Refill.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icon_Refill.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icond_Low.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icond_Low.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icond_Out.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icond_Out.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icond_Refill.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Icond_Refill.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Iconw_Low.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Iconw_Low.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Iconw_Out.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Iconw_Out.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Iconw_Refill.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Iconw_Refill.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26b.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26b.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26bb.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26bb.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26c.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26c.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26cy.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26cy.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26ma.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26ma.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26pc.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26pc.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26pm.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26pm.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26sb.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26sb.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26ye.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink26ye.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15_Level40.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15_Level40.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15_Low.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15_Low.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15_Notdisplay.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15_Notdisplay.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15_Under.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15_Under.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15_Unknown.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15_Unknown.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15_Unset.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_15_Unset.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16_Level40.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16_Level40.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16_Low.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16_Low.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16_Notdisplay.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16_Notdisplay.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16_Under.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16_Under.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16_Unknown.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16_Unknown.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16_Unset.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_16_Unset.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24b.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24b.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24b1.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24b1.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24b2.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24b2.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24b3.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24b3.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24bf.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24bf.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24c.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24c.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24c1.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24c1.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24c2.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24c2.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24c3.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24c3.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24cf.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_24cf.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_Level_00.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_Level_00.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_Level_10.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_Level_10.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_Level_40.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_Level_40.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_Level_70.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_Level_70.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_Level_uk.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_Level_uk.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_bb.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_bb.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_bk.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_bk.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_cy.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_cy.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_el.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_el.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_er.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_er.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_gr.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_gr.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_low.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_low.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_low010.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_low010.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_low040.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_low040.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_low070.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_low070.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_low_bb.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_low_bb.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_ma.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_ma.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_out.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_out.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_out_bb.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_out_bb.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_pb.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_pb.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_pc.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_pc.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_pm.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_pm.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_re.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_re.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_sp.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_sp.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_ye.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Ink_ye.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkd_Level_00.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkd_Level_00.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkd_Level_10.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkd_Level_10.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkd_Level_40.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkd_Level_40.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkd_Level_70.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkd_Level_70.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkd_Level_uk.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkd_Level_uk.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26b.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26b.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26bb.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26bb.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26c.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26c.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26cy.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26cy.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26ma.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26ma.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26pc.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26pc.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26pm.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26pm.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26sb.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26sb.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26ye.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg26ye.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_bb.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_bb.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_bk.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_bk.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_cy.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_cy.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_el.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_el.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_er.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_er.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_gr.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_gr.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_ma.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_ma.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_pb.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_pb.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_pc.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_pc.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_pm.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_pm.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_re.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_re.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_sp.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_sp.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_ye.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkg_ye.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkw_Level_00.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkw_Level_00.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkw_Level_10.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkw_Level_10.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkw_Level_40.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkw_Level_40.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkw_Level_70.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkw_Level_70.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkw_Level_uk.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/cngpijmonmp160/pixmaps/Inkw_Level_uk.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/cs/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/cs/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/cs/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/cs/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/da/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/da/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/da/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/da/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/de/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/de/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/de/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/de/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/el/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/el/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/el/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/el/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/es/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/es/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/es/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/es/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/fi/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/fi/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/fi/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/fi/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/fr/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/fr/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/fr/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/fr/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/hu/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/hu/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/hu/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/hu/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/it/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/it/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/it/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/it/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/ja/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/ja/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/ja/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/ja/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/ko/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/ko/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/ko/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/ko/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/nb/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/nb/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/nb/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/nb/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/nl/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/nl/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/nl/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/nl/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/pl/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/pl/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/pl/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/pl/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/pt/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/pt/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/pt/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/pt/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/ru/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/ru/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/ru/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/ru/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/sv/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/sv/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/sv/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/sv/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/th/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/th/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/th/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/th/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/tr/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/tr/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/tr/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/tr/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/zh/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/zh/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/zh/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/zh/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/zh_TW/LC_MESSAGES/cngpijmonmp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/zh_TW/LC_MESSAGES/cngpijmonmp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/locale/zh_TW/LC_MESSAGES/printuimp160.mo
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/locale/zh_TW/LC_MESSAGES/printuimp160.mo
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/black_bar.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/black_bar.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/contrast_bar.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/contrast_bar.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/cyan_bar.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/cyan_bar.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/cyan_bar2.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/cyan_bar2.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/locale-table
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/locale-table
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/magenta_bar.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/magenta_bar.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/magenta_bar2.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/magenta_bar2.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/ngptn_mp160.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/ngptn_mp160.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/okptn_mp160.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/okptn_mp160.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/printui.glade
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/printui.glade
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/printui.res
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/printui.res
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/yellow_bar.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/yellow_bar.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/local/share/printuimp160/yellow_bar2.xpm
	chmod 644 cnijfilter-mp160-2.70//usr/local/share/printuimp160/yellow_bar2.xpm
	chown 0:0 cnijfilter-mp160-2.70//usr/share/cups/model/canonmp160.ppd
	chmod 644 cnijfilter-mp160-2.70//usr/share/cups/model/canonmp160.ppd
	mkdir cnijfilter-mp160-2.70/debian
	hostname
	date -R
	hostname
	date -R
	chmod 755 cnijfilter-mp160-2.70/debian/rules
	debian/rules binary 2>&1
cnijfilter-mp160_2.70-2_i386.deb generated
	find cnijfilter-mp160-2.70 -type d -exec chmod 755 {} ;
	rm -rf cnijfilter-mp160-2.70


```
They are Canon MP160 Printer drivers if that helps.
Thanks in advance.

---

