---
title: "How to make a modem and Fax program to work"
date: 2009-12-03
forum: General Help
---

### Post by dln9 on 2009-12-03
I am running Ubuntu 9.10.  

I am trying to get the program efax-gtk-3.0.17 to work.  However, I always get this error:  


efax-0.9a: 12:49:43 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 12:49:43 opened /dev/ttyS1
efax-0.9a: 12:49:43 failed page /home/main1/Downloads/output.ps.001
efax-0.9a: 12:49:43 Error: fax device write: Input/output error
efax-0.9a: 12:49:45 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 12:49:47 Error: fax device write: Input/output error
efax-0.9a: 12:49:49 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 12:49:49 sync: dropping DTR
efax-0.9a: 12:49:49 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 12:49:49 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 12:49:51 Error: fax device write: Input/output error
efax-0.9a: 12:49:53 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 12:49:53 Error: fax device write: Input/output error
efax-0.9a: 12:49:53 Error: fax device write: Input/output error
efax-0.9a: 12:49:53 sync: sending escapes
efax-0.9a: 12:49:53 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 12:49:53 Error: fax device write: Input/output error
efax-0.9a: 12:49:53 Error: fax device write: Input/output error
efax-0.9a: 12:49:55 Error: fax device write: Input/output error
efax-0.9a: 12:49:57 Error: fax device write: Input/output error
efax-0.9a: 12:49:59 Error: sync: modem not responding
efax-0.9a: 12:49:59 Error: tcgetattr on fd=3 failed: Input/output error
efax-0.9a: 12:49:59 finished - unrecoverable error


I don't know where to begin to fix this.  I've done searches on Google, but everything I've found has gotten far too technical and involved for me.  Does anyone know of a succinct resource that would guide me on what to do?  Or - Is there a better, more robust tool than efax-gtk?  

Thanks.

---

