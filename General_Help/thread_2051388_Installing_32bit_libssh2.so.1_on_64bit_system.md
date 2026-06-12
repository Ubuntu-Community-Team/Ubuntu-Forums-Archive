---
title: "Installing 32bit libssh2.so.1 on 64bit system"
date: 2012-09-01
forum: General Help
---

### Post by RichardUK on 2012-09-01
This is on 12.04 64Bit AMD system.

I have some software that is 32bit and one of it's libs uses Curl and when I do ldd on it, it reports libssh2.so.1 is missing. I can see in 64bit version but the 32bit version is not in the 'i386-linux-gnu' folders.

Is there an easy way to get it installed? I have a 32bit system running on Atom hardware, can I copy it over from there or is that a naughty thing to do? ;)

Many thanks,
Richard e Collins

```

ldd /usr/lib/Sense/CurlPlugin
	linux-gate.so.1 =>  (0xf77c7000)
	libcurl.so.4 => /usr/lib/i386-linux-gnu/libcurl.so.4 (0xf773d000)
	libssl.so.0.9.8 => /lib/i386-linux-gnu/libssl.so.0.9.8 (0xf76ef000)
	libssh2.so.1 => not found
	libcrypto.so.0.9.8 => /lib/i386-linux-gnu/libcrypto.so.0.9.8 (0xf7575000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf73d0000)
	libidn.so.11 => /usr/lib/i386-linux-gnu/libidn.so.11 (0xf739c000)
	liblber-2.4.so.2 => /usr/lib/i386-linux-gnu/liblber-2.4.so.2 (0xf738d000)
	libldap_r-2.4.so.2 => /usr/lib/i386-linux-gnu/libldap_r-2.4.so.2 (0xf733a000)
	librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf7331000)
	libgssapi_krb5.so.2 => /usr/lib/i386-linux-gnu/libgssapi_krb5.so.2 (0xf72f3000)
	libssl.so.1.0.0 => /lib/i386-linux-gnu/libssl.so.1.0.0 (0xf729d000)
	libcrypto.so.1.0.0 => /lib/i386-linux-gnu/libcrypto.so.1.0.0 (0xf70f2000)
	librtmp.so.0 => /usr/lib/i386-linux-gnu/librtmp.so.0 (0xf70d7000)
	libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf70c1000)
	libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf70bc000)
	/lib/ld-linux.so.2 (0xf77c8000)
	libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xf70a4000)
	libsasl2.so.2 => /usr/lib/i386-linux-gnu/libsasl2.so.2 (0xf7088000)
	libgssapi.so.3 => /usr/lib/i386-linux-gnu/libgssapi.so.3 (0xf704a000)
	libgnutls.so.26 => /usr/lib/i386-linux-gnu/libgnutls.so.26 (0xf6f86000)
	libgcrypt.so.11 => /lib/i386-linux-gnu/libgcrypt.so.11 (0xf6f01000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf6ee6000)
	libkrb5.so.3 => /usr/lib/i386-linux-gnu/libkrb5.so.3 (0xf6e17000)
	libk5crypto.so.3 => /usr/lib/i386-linux-gnu/libk5crypto.so.3 (0xf6dee000)
	libcom_err.so.2 => /lib/i386-linux-gnu/libcom_err.so.2 (0xf6de9000)
	libkrb5support.so.0 => /usr/lib/i386-linux-gnu/libkrb5support.so.0 (0xf6de0000)
	libheimntlm.so.0 => /usr/lib/i386-linux-gnu/libheimntlm.so.0 (0xf6dd8000)
	libkrb5.so.26 => /usr/lib/i386-linux-gnu/libkrb5.so.26 (0xf6d55000)
	libasn1.so.8 => /usr/lib/i386-linux-gnu/libasn1.so.8 (0xf6caf000)
	libhcrypto.so.4 => /usr/lib/i386-linux-gnu/libhcrypto.so.4 (0xf6c7a000)
	libroken.so.18 => /usr/lib/i386-linux-gnu/libroken.so.18 (0xf6c64000)
	libtasn1.so.3 => /usr/lib/i386-linux-gnu/libtasn1.so.3 (0xf6c52000)
	libp11-kit.so.0 => /usr/lib/i386-linux-gnu/libp11-kit.so.0 (0xf6c40000)
	libgpg-error.so.0 => /lib/i386-linux-gnu/libgpg-error.so.0 (0xf6c3a000)
	libkeyutils.so.1 => /lib/i386-linux-gnu/libkeyutils.so.1 (0xf6c36000)
	libwind.so.0 => /usr/lib/i386-linux-gnu/libwind.so.0 (0xf6c0d000)
	libheimbase.so.1 => /usr/lib/i386-linux-gnu/libheimbase.so.1 (0xf6bfe000)
	libhx509.so.5 => /usr/lib/i386-linux-gnu/libhx509.so.5 (0xf6bb7000)
	libsqlite3.so.0 => /usr/lib/i386-linux-gnu/libsqlite3.so.0 (0xf6b11000)
	libcrypt.so.1 => /lib/i386-linux-gnu/libcrypt.so.1 (0xf6ae0000)


```

---

### Post by Tobeus on 2012-09-01
Ok, please don't take this as an expert reply, because I'm no expert, but I know that some i386 packages can be installed from the command line by adding :i386 to the end.  Not sure if this will fix your issue, but if you want to give it a go, it's up to you.

Basically it would look something like this:

```
sudo apt-get update
sudo apt-get install [package name]:i386
```

Hope that helps in some way.  If anything, it is a good thing to know.

-Tobeus

---

### Post by RichardUK on 2012-09-01
> **Tobeus said:**
> Ok, please don't take this as an expert reply, because I'm no expert, but I know that some i386 packages can be installed from the command line by adding :i386 to the end.  Not sure if this will fix your issue, but if you want to give it a go, it's up to you.

Basically it would look something like this:

```
sudo apt-get update
sudo apt-get install [package name]:i386
```

Hope that helps in some way.  If anything, it is a good thing to know.

-Tobeus

You star that work! 

```

sudo apt-get install libssh2-1:i386

```

All the years I've run 64bit linux and I never new that! Many thanks.

The dependency is now fixed. Program still not working but that must be a different issue.

---

### Post by Tobeus on 2012-09-01
Yeah, I remember reading about that whilst trying to figure out a dependency for EVE online in Wine.  I remember seeing it and going, "Oh, so that's how you get 32 bit packages in there on a 64 install."

Glad it worked, and make sure you spread the word if you see anyone else having that kind of issue.

-Tobeus

---

### Post by RichardUK on 2012-09-02
Just a foot note, got the app running, just needed to join the dialout group for ttyUSB0 access. But never would have got that far without getting that dependency fixed.

---

### Post by Bachstelze on 2012-09-02
> **RichardUK said:**
> 
All the years I've run 64bit linux and I never new that! Many thanks.


That feature was actually introduced fairly recently. ;)

---

