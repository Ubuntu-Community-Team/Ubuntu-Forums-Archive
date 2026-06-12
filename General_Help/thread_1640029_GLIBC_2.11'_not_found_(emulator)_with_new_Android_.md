---
title: "GLIBC_2.11' not found (emulator) with new Android 2.3"
date: 2010-12-07
forum: General Help
---

### Post by saurabhnigam on 2010-12-07
Hi all ,
I am using Ubuntu 9.10 .I recently updated my eclipse to get latest android 2.3 sdk but after that I am not able to run android emulator with the message
```
android /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (emulator)
```
After a ```
ldd -v installed/android-sdk-linux_x86-1.6_r1_1/tools/emulator
```
I got 

```

installed/android-sdk-linux_x86-1.6_r1_1/tools/emulator: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by installed/android-sdk-linux_x86-1.6_r1_1/tools/emulator)
	linux-gate.so.1 =>  (0x0096d000)
	libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0x002c3000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0x009f6000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0x005d3000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0x0033b000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0x00def000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00eba000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00306000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0x00110000)
	/lib/ld-linux.so.2 (0x00b8a000)

	Version information:
	installed/android-sdk-linux_x86-1.6_r1_1/tools/emulator:
		libutil.so.1 (GLIBC_2.0) => /lib/tls/i686/cmov/libutil.so.1
		libstdc++.so.6 (GLIBCXX_3.4) => /usr/lib/libstdc++.so.6
		libstdc++.so.6 (CXXABI_1.3) => /usr/lib/libstdc++.so.6
		librt.so.1 (GLIBC_2.2) => /lib/tls/i686/cmov/librt.so.1
		libm.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libm.so.6
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
		libdl.so.2 (GLIBC_2.0) => /lib/tls/i686/cmov/libdl.so.2
		libdl.so.2 (GLIBC_2.1) => /lib/tls/i686/cmov/libdl.so.2
		libgcc_s.so.1 (GLIBC_2.0) => /lib/libgcc_s.so.1
		libpthread.so.0 (GLIBC_2.2) => /lib/tls/i686/cmov/libpthread.so.0
		libpthread.so.0 (GLIBC_2.1) => /lib/tls/i686/cmov/libpthread.so.0
		libpthread.so.0 (GLIBC_2.3.2) => /lib/tls/i686/cmov/libpthread.so.0
		libpthread.so.0 (GLIBC_2.0) => /lib/tls/i686/cmov/libpthread.so.0
		libc.so.6 (GLIBC_2.2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.8) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.7) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.11) => not found
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/lib/tls/i686/cmov/libutil.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/lib/tls/i686/cmov/librt.so.1:
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
	/lib/tls/i686/cmov/libm.so.6:
		ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/lib/tls/i686/cmov/libdl.so.2:
		ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_PRIVATE) => /lib/tls/i686/cmov/libc.so.6
	/usr/lib/libstdc++.so.6:
		libm.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libm.so.6
		ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2
		libgcc_s.so.1 (GCC_4.2.0) => /lib/libgcc_s.so.1
		libgcc_s.so.1 (GLIBC_2.0) => /lib/libgcc_s.so.1
		libgcc_s.so.1 (GCC_3.3) => /lib/libgcc_s.so.1
		libgcc_s.so.1 (GCC_3.0) => /lib/libgcc_s.so.1
		libc.so.6 (GLIBC_2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.3.2) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2) => /lib/tls/i686/cmov/libc.so.6
	/lib/libgcc_s.so.1:
		libc.so.6 (GLIBC_2.1.3) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.2.4) => /lib/tls/i686/cmov/libc.so.6
		libc.so.6 (GLIBC_2.0) => /lib/tls/i686/cmov/libc.so.6
	/lib/tls/i686/cmov/libc.so.6:
		ld-linux.so.2 (GLIBC_PRIVATE) => /lib/ld-linux.so.2
		ld-linux.so.2 (GLIBC_2.3) => /lib/ld-linux.so.2
		ld-linux.so.2 (GLIBC_2.1) => /lib/ld-linux.so.2


```
Notice
```
	libc.so.6 (GLIBC_2.11) => not found
```
Please help me out of this issue as currently I have 2.10 latest version libc6

---

### Post by prati on 2010-12-07
Hi All,

I am also currently having the same problem. I am using Ubuntu 8.10 and Ganymede eclipse 3.4.1. When I try to run the application, it gives GLIBC_2.11 not found error. Emulator property shows that GLIBC_2.11 is missing. Please help, I did not find any solutions on the net yet.

---

### Post by nasif_20 on 2010-12-08
i am also facing the same problem , help me to sorted out...

---

### Post by orarangzelek on 2010-12-08
I got same problem. :(

any bodies help us here? plz

---

### Post by AntonJ on 2010-12-08
Looks, like this is a 2.3 update issue.
[http://groups.google.com/group/android-platform/browse_thread/thread/dee2a5f213fed983/2a2c78d662f13e49?fwc=1](http://groups.google.com/group/android-platform/browse_thread/thread/dee2a5f213fed983/2a2c78d662f13e49?fwc=1)
I have 2 PC's one is 9.10 and second - 10.10. 
10.10 works fine, but 9.10 - can't launch emulator...

Moreover, my app can't run any more on my SE Xperia X10i (Android 2.1)
when compiled on Ubuntu 10.10.
I will do some  configuration manipulations for app this evening...

---

### Post by hic3456 on 2010-12-09
Yup, the folks on Android team are very much aware of the problem and working to fix it - expect an 'official' fix to appear shortly.

In the meantime, I've [posted here a hacky workaround]("http://codetrips.blogspot.com/2010/12/latest-update-for-android-sdk-breaks.html").

---

### Post by nmtri on 2010-12-09
Dear All,
Hic Hic, :cry:, now i face same problem. Pls help me.
I work on ubuntu 9.10, and android sdk : [android-sdk_r08-linux_86.tgz. ]("http://dl.google.com/android/android-sdk_r08-linux_86.tgz")
When i run app on android and through error:
[COLOR=Red]Emulator] ./android-sdk-linux_86/tools/emulator: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by ./android-sdk-linux_86/tools/emulator)[/COLOR]
Thanks ^^

---

### Post by eckschi on 2010-12-09
Hi, had the same problem. This can be solved if you still have the old tar archive of the sdk hanging around. Backup the file android-sdk-linux_x86/tools/emulator and replace it with the one from the old sdk. It seems only the emulator was built with dependencies to this version of glibc.

hth

---

### Post by eckschi on 2010-12-09
bummer, what i forgot to mention, I guess then also only android apps <=2.2 are supported. Still helped me though, since I'm still on 2.1 :)

---

### Post by AntonJ on 2010-12-09
> **hic3456 said:**
> Yup, the folks on Android team are very much aware of the problem and working to fix it - expect an 'official' fix to appear shortly.

In the meantime, I've [posted here a hacky workaround]("http://codetrips.blogspot.com/2010/12/latest-update-for-android-sdk-breaks.html").

Can't open [http://dl.google.com/android/repository/tools_r07.zip](http://dl.google.com/android/repository/tools_r07.zip), I've got error 404.

I have solved problem when it was impossible to launch app. None of configurations helped. So I have uninstalled my old app and installed new one.

---

### Post by madhukaraphatak on 2010-12-09
The link to download tools is [http://dl-ssl.google.com/android/repository/tools_r07-linux.zip](http://dl-ssl.google.com/android/repository/tools_r07-linux.zip)

---

### Post by Shaista Naaz on 2010-12-10
> **madhukaraphatak said:**
> The link to download tools is [http://dl-ssl.google.com/android/repository/tools_r07-linux.zip](http://dl-ssl.google.com/android/repository/tools_r07-linux.zip)


Thanks..... :p This has solved the problem. I am now able to see my emulator up and running.

---

### Post by Exx on 2010-12-27
Sweet, yer hack worked in a jiff.

---

### Post by amgtorre on 2011-01-04
it works ! 

Thanks for the tips

---

