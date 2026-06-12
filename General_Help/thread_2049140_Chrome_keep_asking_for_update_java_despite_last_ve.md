---
title: "Chrome keep asking for update java despite last version is installed"
date: 2012-08-28
forum: General Help
---

### Post by macozz on 2012-08-28
Hi all,
I dig in the forum and other sources to realize why this happens but no luck.
I am running 12.04, with chrome 22.0.1229.14 beta, Oracle java 1.7.0_06 (latest version downloaded from Oracle site). I removed all other java versions (openjdk, and previous Oracle), the Chrome plugin is the one of the 1.7.0_06. However, when go to the Oracle testing page a message is displayed asking to update the plugin offering to run just this time...
When the test runs it identify that last version is installed, but the "update" message continue to appears any time.
Any one have and idea why? Any one else have the same issue? Any idea how to solve it? 

Cheers

---

### Post by Rexilion on 2012-08-28
I guess it's a bug, you should just ignore it for now. Why not install icedtea through the official repo's?

---

### Post by TristanSt on 2012-08-28
Is it definitely picking up the right one? Go to about:plugins in Chrome and see which version of the plugin is referenced.

In mine it's showing as:

```
Java - Version: 1.6.0_32 Download Critical Security Update
The next generation Java plug-in for Mozilla browsers.
Name:	Java(TM) Plug-in 1.6.0_32
Description:	The next generation Java plug-in for Mozilla browsers.
Version:	1.6.0_32
Location:	/usr/lib/jvm/jre1.6.0_32/lib/amd64/libnpjp2.so
Type:	NPAPI
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-java-vm	Java™ Plug-in	
application/x-java-applet	Java™ Plug-in Applet	
application/x-java-applet;version=1.1	Java™ Plug-in	
application/x-java-applet;version=1.1.1	Java™ Plug-in	
application/x-java-applet;version=1.1.2	Java™ Plug-in	
application/x-java-applet;version=1.1.3	Java™ Plug-in	
application/x-java-applet;version=1.2	Java™ Plug-in	
application/x-java-applet;version=1.2.1	Java™ Plug-in	
application/x-java-applet;version=1.2.2	Java™ Plug-in	
application/x-java-applet;version=1.3	Java™ Plug-in	
application/x-java-applet;version=1.3.1	Java™ Plug-in	
application/x-java-applet;version=1.4	Java™ Plug-in	
application/x-java-applet;version=1.4.1	Java™ Plug-in	
application/x-java-applet;version=1.4.2	Java™ Plug-in	
application/x-java-applet;version=1.5	Java™ Plug-in	
application/x-java-applet;version=1.6	Java™ Plug-in	
application/x-java-applet;jpi-version=1.6.0_32	Java™ Plug-in	
application/x-java-bean	Java™ Plug-in JavaBeans	
application/x-java-bean;version=1.1	Java™ Plug-in	
application/x-java-bean;version=1.1.1	Java™ Plug-in	
application/x-java-bean;version=1.1.2	Java™ Plug-in	
application/x-java-bean;version=1.1.3	Java™ Plug-in	
application/x-java-bean;version=1.2	Java™ Plug-in	
application/x-java-bean;version=1.2.1	Java™ Plug-in	
application/x-java-bean;version=1.2.2	Java™ Plug-in	
application/x-java-bean;version=1.3	Java™ Plug-in	
application/x-java-bean;version=1.3.1	Java™ Plug-in	
application/x-java-bean;version=1.4	Java™ Plug-in	
application/x-java-bean;version=1.4.1	Java™ Plug-in	
application/x-java-bean;version=1.4.2	Java™ Plug-in	
application/x-java-bean;version=1.5	Java™ Plug-in	
application/x-java-bean;version=1.6	Java™ Plug-in	
application/x-java-bean;jpi-version=1.6.0_32	Java™ Plug-in	
application/x-java-vm-npruntime	Java™ Plug-in	

```

Which is a little crazy as I can't work out how to get Chrome to point to the new v7 one.

Any ideas on that one?

---

### Post by macozz on 2012-08-28
The version of my plugin is 1.7.0_06, the latest available, but still as for download critical security update:

Java (2 files) - Version: 1.7.0_06 Download Critical Security Update
Java plug-in for NPAPI-based browsers.
Name:	Java(TM) Plug-in 1.7.0_06
Description:	Java plug-in for NPAPI-based browsers.
Version:	1.7.0_06
Location:	/usr/lib/jvm/jre1.7.0_06/lib/amd64/libnpjp2.so
Type:	NPAPI
 	 Disable

There is no way to fix it? It is, to say the best, annoying 
The icedtea and other open java does not work with my bank sites, so I need Oracle.
Thanks

---

