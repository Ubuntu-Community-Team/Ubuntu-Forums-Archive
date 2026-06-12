---
title: "GLIBCXX_3.4.11 and GLIBC_2.11 not found"
date: 2011-05-25
forum: General Help
---

### Post by finalovo on 2011-05-25
Hello everyone
I write a program and it run on Ubuntu 10.04 without any problem.
However when I copy my executable file to Ubuntu 8.04; it comes out error:

```
./gred: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by ./gred)
./gred: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by ./gred)
```

I used  ldd -v ./gred and the output is:
```
./gred: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by ./gred)
./gred: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by ./gred)
	linux-gate.so.1 =>  (0xb7f2f000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0xb7ebf000)
	libGLU.so.1 => /usr/lib/libGLU.so.1 (0xb7e3c000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb7ac4000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7a40000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb7a26000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0xb79c5000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb799e000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb7985000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb7948000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb78db000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb78b1000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb7875000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7871000)
	libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb786b000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb7862000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb77b1000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb77ae000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0xb77a6000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb7783000)
	libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7762000)
	libz.so.1 => /usr/lib/libz.so.1 (0xb774d000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7749000)
	libgvc.so.5 => ./greddir/guiREDLib/libgvc.so.5 (0xb76e3000)
	libgraph.so.4 => ./greddir/guiREDLib/libgraph.so.4 (0xb76d6000)
	libcdt.so.4 => ./greddir/guiREDLib/libcdt.so.4 (0xb76cf000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb75dc000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb75b7000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb75ac000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7594000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7444000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb735d000)
	libpathplan.so.4 => ./greddir/guiREDLib/libpathplan.so.4 (0xb7354000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7346000)
	libXxf86vm.so.1 => /usr/lib/libXxf86vm.so.1 (0xb7341000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0xb733d000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb7338000)
	libdrm.so.2 => /usr/lib/libdrm.so.2 (0xb732e000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb7325000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0xb7322000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb72bf000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb72b7000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb72af000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb72a9000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb72a0000)
	libselinux.so.1 => /lib/libselinux.so.1 (0xb7286000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb7265000)
	/lib/ld-linux.so.2 (0xb7f30000)
	libpcre.so.3 => /usr/lib/libpcre.so.3 (0xb723e000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0xb7226000)
	libxdot.so.4 => ./greddir/guiREDLib/libxdot.so.4 (0xb7221000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb721f000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb7207000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb7204000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0xb71da000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb71d5000)

	Version information:
	./gred:
		libdl.so.2 (GLIBC_2.1) => /lib/tls/i686/cmov/libdl.so.2
		libdl.so.2 (GLIBC_2.0) => /lib/tls/i686/cmov/libdl.so.2
		libm.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libm.so.6
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
		libgcc_s.so.1 (GCC_3.0) => /lib/libgcc_s.so.1
		libgcc_s.so.1 (GLIBC_2.0) => /lib/libgcc_s.so.1
		libpthread.so.0 (GLIBC_2.2) => /lib/tls/i686/cmov/libpthread.so.0
		libpthread.so.0 (GLIBC_2.3.2) => /lib/tls/i686/cmov/libpthread.so.0
		libpthread.so.0 (GLIBC_2.1) => /lib/tls/i686/cmov/libpthread.so.0
		libpthread.so.0 (GLIBC_2.0) => /lib/tls/i686/cmov/libpthread.so.0
		libpng12.so.0 (PNG12_0) => /usr/lib/libpng12.so.0
		libstdc++.so.6 (GLIBCXX_3.4.11) => not found
		libstdc++.so.6 (GLIBCXX_3.4.9) => /usr/lib/libstdc++.so.6
		libstdc++.so.6 (CXXABI_1.3) => /usr/lib/libstdc++.so.6
		libstdc++.so.6 (GLIBCXX_3.4) => /usr/lib/libstdc++.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.11) => not found
		libc.so.6 (GLIBC_2.3.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.7) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libGL.so.1:
		libdl.so.2 (GLIBC_2.1) => /lib/tls/i686/cmov/libdl.so.2
		libdl.so.2 (GLIBC_2.0) => /lib/tls/i686/cmov/libdl.so.2
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
		libpthread.so.0 (GLIBC_2.0) => /lib/tls/i686/cmov/libpthread.so.0
	/usr/lib/libGLU.so.1:
		libgcc_s.so.1 (GCC_3.0) => /lib/libgcc_s.so.1
		libstdc++.so.6 (CXXABI_1.3) => /usr/lib/libstdc++.so.6
		libstdc++.so.6 (GLIBCXX_3.4) => /usr/lib/libstdc++.so.6
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libgtk-x11-2.0.so.0:
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libgdk-x11-2.0.so.0:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libatk-1.0.so.0:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libgio-2.0.so.0:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libpangoft2-1.0.so.0:
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libgdk_pixbuf-2.0.so.0:
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libpango-1.0.so.0:
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libfreetype.so.6:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libfontconfig.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libgobject-2.0.so.0:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libgmodule-2.0.so.0:
		libdl.so.2 (GLIBC_2.1) => /lib/tls/i686/cmov/libdl.so.2
		libdl.so.2 (GLIBC_2.0) => /lib/tls/i686/cmov/libdl.so.2
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libgthread-2.0.so.0:
		librt.so.1 (GLIBC_2.2) => /lib/tls/i686/cmov/librt.so.1
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
		libpthread.so.0 (GLIBC_2.1) => /lib/tls/i686/cmov/libpthread.so.0
		libpthread.so.0 (GLIBC_2.0) => /lib/tls/i686/cmov/libpthread.so.0
		libpthread.so.0 (GLIBC_2.3.2) => /lib/tls/i686/cmov/libpthread.so.0
	/lib/tls/i686/cmov/librt.so.1:
		ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
		libpthread.so.0 (GLIBC_2.1) => /lib/tls/i686/cmov/libpthread.so.0
		libpthread.so.0 (GLIBC_2.2) => /lib/tls/i686/cmov/libpthread.so.0
		libpthread.so.0 (GLIBC_PRIVATE) => /lib/tls/i686/cmov/libpthread.so.0
		libpthread.so.0 (GLIBC_2.0) => /lib/tls/i686/cmov/libpthread.so.0
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_PRIVATE) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libglib-2.0.so.0:
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libXinerama.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libSM.so.6:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libpng12.so.0:
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libjpeg.so.62:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libz.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/lib/tls/i686/cmov/libdl.so.2:
		ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_PRIVATE) => /lib/tls/i686/cmov/libc.so.6
	./greddir/guiREDLib/libgvc.so.5:
		libz.so.1 (ZLIB_1.2.0) => /usr/lib/libz.so.1
		libdl.so.2 (GLIBC_2.1) => /lib/tls/i686/cmov/libdl.so.2
		libdl.so.2 (GLIBC_2.0) => /lib/tls/i686/cmov/libdl.so.2
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.7) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	./greddir/guiREDLib/libgraph.so.4:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.7) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	./greddir/guiREDLib/libcdt.so.4:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libstdc++.so.6:
		ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2
		libgcc_s.so.1 (GCC_4.2.0) => /lib/libgcc_s.so.1
		libgcc_s.so.1 (GLIBC_2.0) => /lib/libgcc_s.so.1
		libgcc_s.so.1 (GCC_3.3) => /lib/libgcc_s.so.1
		libgcc_s.so.1 (GCC_3.0) => /lib/libgcc_s.so.1
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
	/lib/tls/i686/cmov/libm.so.6:
		ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/lib/libgcc_s.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/lib/tls/i686/cmov/libpthread.so.0:
		ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2
		ld-linux.so.2 (GLIBC_2.1) => /lib/ld-linux.so.2
		ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_PRIVATE) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/lib/tls/i686/cmov/libc.so.6:
		ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
		ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2
		ld-linux.so.2 (GLIBC_2.1) => /lib/ld-linux.so.2
	/usr/lib/libX11.so.6:
		libdl.so.2 (GLIBC_2.1) => /lib/tls/i686/cmov/libdl.so.2
		libdl.so.2 (GLIBC_2.0) => /lib/tls/i686/cmov/libdl.so.2
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	./greddir/guiREDLib/libpathplan.so.4:
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libXext.so.6:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libXxf86vm.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libXdamage.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libXfixes.so.3:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libdrm.so.2:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libpangocairo-1.0.so.0:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
	/usr/lib/libXcomposite.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libcairo.so.2:
		libgcc_s.so.1 (GLIBC_2.0) => /lib/libgcc_s.so.1
		libgcc_s.so.1 (GCC_3.4) => /lib/libgcc_s.so.1
		libpng12.so.0 (PNG12_0) => /usr/lib/libpng12.so.0
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
		libm.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libm.so.6
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
	/usr/lib/libXrender.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libXi.so.6:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libXrandr.so.2:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libXcursor.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/lib/libselinux.so.1:
		ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2
		libdl.so.2 (GLIBC_2.1) => /lib/tls/i686/cmov/libdl.so.2
		libdl.so.2 (GLIBC_2.0) => /lib/tls/i686/cmov/libdl.so.2
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libexpat.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libpcre.so.3:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libICE.so.6:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	./greddir/guiREDLib/libxdot.so.4:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.7) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libxcb-xlib.so.0:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libxcb.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libXau.so.6:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libpixman-1.so.0:
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libXdmcp.so.6:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6

```

I have tried downloading libc6_2.7-10ubuntu8_i386.deb on [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/?C=M;O=D](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/?C=M;O=D) and reinstall it

But it still can't work.
Could anyone help me run my program on Ubuntu 8.04
Thank you!

---

