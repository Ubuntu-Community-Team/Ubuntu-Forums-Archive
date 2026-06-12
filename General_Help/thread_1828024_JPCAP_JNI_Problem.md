---
title: "JPCAP JNI Problem"
date: 2011-08-18
forum: General Help
---

### Post by g1njackal on 2011-08-18
I'm trying to run a process that uses jpcap and after a lot of tweaking finally got libpcap installed and compiled jpcap and put it in the right place. The problem is, now I'm getting an error of not being able to open a Native Method and I've never seen this before. If anyone could help out it would be great!

This is the error that I'm getting
```
Exception in thread "main" java.lang.UnsatisfiedLinkError: net.sourceforge.jpcap.capture.PacketCapture.openOffline(ILjava/lang/String;)V
	at net.sourceforge.jpcap.capture.PacketCapture.openOffline(Native Method)
```

Thanks!!

---

