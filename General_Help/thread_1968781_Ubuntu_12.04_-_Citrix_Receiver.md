---
title: "Ubuntu 12.04 - Citrix Receiver"
date: 2012-04-29
forum: General Help
---

### Post by A4orce84 on 2012-04-29
Hey Everyone,

I am trying to get Citrix Receiver working on my fresh Ubuntu 12.04 install using the following guide:
[http://tinyurl.com/bncnwbq/](http://tinyurl.com/bncnwbq/)

However, it seems that whenever I try to install the .deb package from the citrix website I get a weird error:

"Internal Error
The file “/home/aahmad/Downloads/icaclient_12.1.0_i386.deb” could not be opened."

Has anyone been able to successfully install and get this working?

Thanks,

--Asif

---

### Post by Lindexter on 2012-04-29
> **A4orce84 said:**
> Hey Everyone,

I am trying to get Citrix Receiver working on my fresh Ubuntu 12.04 install using the following guide:
[http://tinyurl.com/bncnwbq/](http://tinyurl.com/bncnwbq/)

However, it seems that whenever I try to install the .deb package from the citrix website I get a weird error:

"Internal Error
The file &#8220;/home/aahmad/Downloads/icaclient_12.1.0_i386.deb&#8221; could not be opened."

Has anyone been able to successfully install and get this working?

Thanks,

--Asif

I just downloaded this from the same site and here is what the error looks like:

```
 dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: invalid distance too far back'
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
dpkg-deb: error: subprocess tar returned error exit status 2
dpkg: error processing icaclient_12.1.0_i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 icaclient_12.1.0_i386.deb

```

However, the 64 bit deb package still works.

icaclient_12.1.0_amd64.deb

If your system can handle it, use that one instead.

---

### Post by A4orce84 on 2012-04-29
I'm running 32bit unfortunately.  =(

---

### Post by keithpeter on 2012-04-29
Hello A4orce84

There is a thread on the Citrix support forums, someone has made a mistake in packaging version 12.10

Google for the previous icaclient_12.0.0_i386.deb if you don't have backups of the debs from last time. Google Code is a trusted source.

I'd keep a watch on the Citrix thread though as it is best to have the most up to date version.

[http://forums.citrix.com/thread.jspa?threadID=306346&tstart=0](http://forums.citrix.com/thread.jspa?threadID=306346&tstart=0)

---

