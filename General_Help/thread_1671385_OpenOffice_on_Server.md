---
title: "OpenOffice on Server"
date: 2011-01-19
forum: General Help
---

### Post by pi3.1415926535... on 2011-01-19
I was wondering if there was some way of running OpenOffice on Ubuntu Server such that it can be used from a Windows computer somewhat like Google Docs.

---

### Post by HermanAB on 2011-01-20
Yes, install OpenOffice on the server and install Cygwin on Windows.

Then open a Cygwin Bash console and type:
c:\> ssh -X -C -c blowfish user@serveripaddress writer

---

### Post by Ranko Kohime on 2011-01-20
> **HermanAB said:**
> Yes, install OpenOffice on the server and install Cygwin on Windows.

Then open a Cygwin Bash console and type:
c:\> ssh -X -C -c blowfish user@serveripaddress writer
That's a nifty trick.  Is there a Mac analogue, assuming one has X11 installed?

---

