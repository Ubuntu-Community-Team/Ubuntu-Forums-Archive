---
title: "Kernel compile error"
date: 2010-12-11
forum: General Help
---

### Post by gfajdi on 2010-12-11
I get the following error at the end of compiling process when trying to generate a custom kernel package.

What's wrong?

$ fakeroot make-kpkg --initrd --append-to-version=-custom kernel-image kernel-headers
/debian/pkg/image/preinst > /home/grega/osebno/source/kernel/linux-2.6/debian/linux-image-2.6.37-rc5-custom+/DEBIAN/preinst
chmod 755 /home/grega/osebno/source/kernel/linux-2.6/debian/linux-image-2.6.37-rc5-custom+/DEBIAN/preinst
sed -e 's/=V/2.6.37-rc5-custom+/g'    -e 's/=IB//g'    \
	    -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=KPV/12.033/g'                       \
	    -e 's/=K/vmlinuz/g'  	     \
	    -e 's/=I/YES/g'     -e 's,=D,/boot,g'	     \
	    -e 's/=MD//g'				     \
	    -e 's@=MK@@g' -e 's@=A@i386@g'   \
	    -e 's@=M@@g'    -e 's/=OF//g'    \
	    -e 's/=S//g' -e 's@=B@i386@g'     \
	 ./debian/pkg/image/prerm > /home/grega/osebno/source/kernel/linux-2.6/debian/linux-image-2.6.37-rc5-custom+/DEBIAN/prerm
chmod 755 /home/grega/osebno/source/kernel/linux-2.6/debian/linux-image-2.6.37-rc5-custom+/DEBIAN/prerm
po2debconf debian/templates.in > debian/templates.l10n
sed -e 's/=V/2.6.37-rc5-custom/g'    -e 's/=IB//g'    \
	    -e 's/=ST/linux/g'  -e 's/=R//g' \
            -e 's/=KPV/12.033/g'                       \
	    -e 's/=K/vmlinuz/g'           \
	    -e 's@=MK@@g' -e 's@=A@i386@g'   \
	    -e 's/=I/YES/g'     -e 's,=D,/boot,g'        \
	    -e 's/=MD//g'                                \
	    -e 's@=M@@g'    -e 's/=OF//g'    \
	    -e 's/=S//g' -e 's@=B@i386@g'     \
	 ./debian/templates.l10n   > ./debian/templates.master
install -p    -o root -g root  -m  644 ./debian/templates.master /home/grega/osebno/source/kernel/linux-2.6/debian/linux-image-2.6.37-rc5-custom+/DEBIAN/templates
dpkg-gencontrol -DArchitecture=i386 -isp	     \
			-plinux-image-2.6.37-rc5-custom+ -P/home/grega/osebno/source/kernel/linux-2.6/debian/linux-image-2.6.37-rc5-custom+/
dpkg-gencontrol: error: package linux-image-2.6.37-rc5-custom+ not in control info
make[2]: *** [debian/stamp/binary/linux-image-2.6.37-rc5-custom+] Error 255
make[2]: Leaving directory `/home/grega/osebno/source/kernel/linux-2.6'
make[1]: *** [debian/stamp/binary/pre-linux-image-2.6.37-rc5-custom+] Error 2
make[1]: Leaving directory `/home/grega/osebno/source/kernel/linux-2.6'
make: *** [kernel-image] Error 2

---

