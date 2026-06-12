---
title: "BPM DJ library issues"
date: 2010-02-27
forum: General Help
---

### Post by djbushido on 2010-02-27
Ok, so I grabbed the binary version of bpm-dj. The libraries it needs are - (as reported by ldd) "ldd kbpm-dj
	linux-gate.so.1 =>  (0xf7734000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf76fa000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf7632000)
	librt.so.1 => /lib32/librt.so.1 (0xf7628000)
	libfftw3.so.3 => not found
	libqt-mt.so.3 => not found
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf7536000)
	libm.so.6 => /lib32/libm.so.6 (0xf7510000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf74f1000)
	libc.so.6 => /lib32/libc.so.6 (0xf73ac000)
	/lib/ld-linux.so.2 (0xf7735000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf73a8000)"
However, both of the "missing" libraries are in /usr/lib.
Am I missing something?

---

