---
title: "jnlp application suddenly stopped working in 11.04"
date: 2011-08-18
forum: General Help
---

### Post by stepheny on 2011-08-18
I use a small application called bendometer.jnlp. On my desktop running 10.04 it runs fine after opening with "OpenJDK Java 6 Web Start".

I have installed the same application on my brand new laptop running Ubuntu 11.04 and it was running perfectly until yesterday. Yesterday it hung during the startup and since I killed the hung process it has refused to start again. If I now run it in a terminal using the command 

```
javaws "/home/steve/Music/Bendo/bendometer.jnlp"
```

I get the following errors

```
Unable to use Firefox's proxy settings. Using "DIRECT" as proxy type.
Exception in thread "Thread-2" java.lang.InternalError: Corrupt LRU file entries
	at net.sourceforge.jnlp.cache.CacheLRUWrapper$1.compare(CacheLRUWrapper.java:184)
	at net.sourceforge.jnlp.cache.CacheLRUWrapper$1.compare(CacheLRUWrapper.java:172)
	at java.util.Arrays.mergeSort(Arrays.java:1283)
	at java.util.Arrays.mergeSort(Arrays.java:1294)
	at java.util.Arrays.mergeSort(Arrays.java:1295)
	at java.util.Arrays.sort(Arrays.java:1223)
	at java.util.Collections.sort(Collections.java:176)
	at net.sourceforge.jnlp.cache.CacheLRUWrapper.getLRUSortedEntries(CacheLRUWrapper.java:172)
	at net.sourceforge.jnlp.cache.CacheUtil.getCacheFileIfExist(CacheUtil.java:325)
	at net.sourceforge.jnlp.cache.CacheUtil.getCacheFile(CacheUtil.java:306)
	at net.sourceforge.jnlp.cache.CacheEntry.<init>(CacheEntry.java:56)
	at net.sourceforge.jnlp.cache.ResourceTracker.initializeResource(ResourceTracker.java:769)
	at net.sourceforge.jnlp.cache.ResourceTracker.processResource(ResourceTracker.java:611)
	at net.sourceforge.jnlp.cache.ResourceTracker.access$500(ResourceTracker.java:72)
	at net.sourceforge.jnlp.cache.ResourceTracker$Downloader$1.run(ResourceTracker.java:1115)
	at net.sourceforge.jnlp.cache.ResourceTracker$Downloader$1.run(ResourceTracker.java:1113)
	at java.security.AccessController.doPrivileged(Native Method)
	at net.sourceforge.jnlp.cache.ResourceTracker$Downloader.run(ResourceTracker.java:1113)
	at java.lang.Thread.run(Thread.java:679)
```

I have checked in var/log/apt/history and I cannot see that any Java updates have taken place recently but I have reinstalled the icedtea/openJDK-6 files that where shown as being installed under a search for icedtea in Synaptic.

Any help would be greatly appreciated.

---

### Post by deppy on 2011-08-18
Try:

/usr/bin/javaws -Xclearcache

I've seen a lot of java apps under 11.04 having issues such as this, but haven't been able to pinpoint the root cause so far.

---

### Post by stepheny on 2011-08-18
Thanks deppy, that fixed it.

---

