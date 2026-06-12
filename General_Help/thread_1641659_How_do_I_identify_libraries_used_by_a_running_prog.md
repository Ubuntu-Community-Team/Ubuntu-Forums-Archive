---
title: "How do I identify libraries used by a running program?"
date: 2010-12-09
forum: General Help
---

### Post by The Altruist on 2010-12-09
I'm using the FortiClient SSL VPN free version provided by my University. I can't get tech support from the university OR Fortigate. I have it running on one system, but I have no idea what the sequence of libraries I installed was. I need it to run on a second machine. pstree is only telling me that the FortiClient ssl daemon depends on pppd. I need to know how to find out what else it's using: LibPKCS and the like.

---

### Post by The Altruist on 2010-12-09
NVM, I discovered LDD. For those curious the list is as follows:
```

	linux-gate.so.1 =>  (0xf7793000)
	libgtk-x11-2.0.so.0 => /usr/lib32/libgtk-x11-2.0.so.0 (0xf7383000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf737e000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf7374000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7289000)
	libm.so.6 => /lib32/libm.so.6 (0xf7263000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7247000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf722e000)
	libc.so.6 => /lib32/libc.so.6 (0xf70d4000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib32/libgdk_pixbuf-2.0.so.0 (0xf70ba000)
	libgdk-x11-2.0.so.0 => /usr/lib32/libgdk-x11-2.0.so.0 (0xf7023000)
	libpango-1.0.so.0 => /usr/lib32/libpango-1.0.so.0 (0xf6fe1000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf6ec4000)
	libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf6e82000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf6e7d000)
	libglib-2.0.so.0 => /lib32/libglib-2.0.so.0 (0xf6dae000)
	librt.so.1 => /lib32/librt.so.1 (0xf6da5000)
	libXinerama.so.1 => /usr/lib32/libXinerama.so.1 (0xf6da1000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf6d91000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6d86000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf6d78000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf6d70000)
	libXcursor.so.1 => /usr/lib32/libXcursor.so.1 (0xf6d66000)
	libpangocairo-1.0.so.0 => /usr/lib32/libpangocairo-1.0.so.0 (0xf6d5a000)
	libXcomposite.so.1 => /usr/lib32/libXcomposite.so.1 (0xf6d56000)
	libXdamage.so.1 => /usr/lib32/libXdamage.so.1 (0xf6d51000)
	libXfixes.so.3 => /usr/lib32/libXfixes.so.3 (0xf6d4b000)
	libatk-1.0.so.0 => /usr/lib32/libatk-1.0.so.0 (0xf6d30000)
	libcairo.so.2 => /usr/lib32/libcairo.so.2 (0xf6c7d000)
	libpng12.so.0 => /lib32/libpng12.so.0 (0xf6c58000)
	libgio-2.0.so.0 => /usr/lib32/libgio-2.0.so.0 (0xf6b6b000)
	libpangoft2-1.0.so.0 => /usr/lib32/libpangoft2-1.0.so.0 (0xf6b45000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf6ace000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf6ab9000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf6a89000)
	libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf6a84000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf6a4f000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf6a36000)
	libuuid.so.1 => /lib32/libuuid.so.1 (0xf6a31000)
	/lib/ld-linux.so.2 (0xf7794000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf6a16000)
	libpixman-1.so.0 => /usr/lib32/libpixman-1.so.0 (0xf69b6000)
	libxcb-shm.so.0 => /usr/lib32/libxcb-shm.so.0 (0xf69b2000)
	libxcb-render.so.0 => /usr/lib32/libxcb-render.so.0 (0xf69aa000)
	libresolv.so.2 => /lib32/libresolv.so.2 (0xf6995000)
	libselinux.so.1 => /lib32/libselinux.so.1 (0xf6979000)
	libexpat.so.1 => /lib32/libexpat.so.1 (0xf6952000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf694e000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf6948000)

```

---

### Post by SpawnHappyJake on 2011-10-05
OP answers own question here: [http://ubuntuforums.org/showthread.php?t=1569368&highlight=forticlient](http://ubuntuforums.org/showthread.php?t=1569368&highlight=forticlient) . You need the 32-bit libraries installed.

Just doing a clean-sweep of the threads having to do with FortiClient because I just got it working on my Linux machine. Don't want unsolved threads lying around.

Jake

---

