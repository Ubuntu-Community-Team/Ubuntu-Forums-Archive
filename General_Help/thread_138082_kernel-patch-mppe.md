---
title: "kernel-patch-mppe"
date: 2006-03-01
forum: General Help
---

### Post by vinthund on 2006-03-01
synaptic says:
```
Point-to-Point Tunneling Protocol (PPTP) Client
Client for the proprietary Microsoft Point-to-Point Tunneling
Protocol, PPTP.  Allows connection to a PPTP based VPN as used
by employers and some cable and ADSL service providers.
MPPE (Microsoft Point-to-Point Encryption) support requires
an additionnal kernel module, provided by package kernel-patch-mppe.
```
How can I install kernel-patch-mppe? There is no such a package in all my Synaptic. I have 5.04, not 5.10, but 5.04 forum has one post in a few days so I hope to get an answer here.

mv

---

### Post by hw-tph on 2006-03-01
Since the main Debian package directory is down, here is a link to the [relevant page](http://pdo.debian.net/unstable/comm/kernel-patch-mppe) on the [backup server](http://pdo.debian.net).

Be warned that applying the patch requires patching the kernel source, building a new kernel and installing it.


Håkan

---

### Post by vinthund on 2006-03-01
oh, so it is not already built in?
so you mean i need to recompile kernel?

---

### Post by hw-tph on 2006-03-01
It appears it is already compiled in - it is included in the patchset applied to the Ubuntu kernel (check out linux-patch-ubuntu-2.6.12). That giant patch contains all the patches applied to a vanilla (kernel.org) kernel to create the Ubuntu kernel. It contains this patch, which should be the one you're after:
```
+config PPP_MPPE_MPPC
+	tristate "Microsoft PPP compression/encryption (MPPC/MPPE)"
+	depends on PPP
+	select CRYPTO_SHA1
+	select CRYPTO_ARC4
+	---help---
+	  Support for the Microsoft Point-To-Point Compression (RFC2118) and 
+	  Microsoft Point-To-Point Encryption (RFC3078). These protocols are
+	  supported by Microsoft Windows and wide range of "hardware" access
+	  servers. MPPE is common protocol in Virtual Private Networks. According
+	  to RFC3078, MPPE supports 40, 56 and 128-bit key lengths. Depending on
+	  PPP daemon configuration on both ends of the link, following scenarios
+	  are possible:
+		- only compression (MPPC) is used,
+		- only encryption (MPPE) is used,
+		- compression and encryption (MPPC+MPPE) are used.
+
+	  Please note that Hi/Fn (http://www.hifn.com) holds patent on MPPC so
+	  you should check if this patent is valid in your country in order to
+	  avoid legal problems.
+
+	  For more information please visit http://free.polbox.pl/h/hs001
+
+	  To compile this driver as a module, choose M here. The module will
+	  be called ppp_mppe_mppc.ko.
+
```

So, to make a long story short: It appears you do not have to build a kernel of your own.

Håkan

---

