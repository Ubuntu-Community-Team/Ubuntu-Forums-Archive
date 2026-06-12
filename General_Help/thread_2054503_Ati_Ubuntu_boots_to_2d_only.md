---
title: "Ati Ubuntu boots to 2d only"
date: 2012-09-07
forum: General Help
---

### Post by elliotn on 2012-09-07
guys help me, I can't get 3d

 ```
elliotn@elliotn-ubuntu:~$ fglrxinfo
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  13
  Current serial number in output stream:  13
elliotn@elliotn-ubuntu:~$
```

and here is my xorg.conf

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

And amdcccle

```
elliotn@elliotn-ubuntu:~$ sudo amdcccle
[sudo] password for elliotn: 
[xcb] Unknown sequence number while appending request
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called
[xcb] Aborting, sorry about that.
amdcccle: ../../src/xcb_io.c:160: append_pending_request: Assertion `!xcb_xlib_unknown_seq_number' failed.
elliotn@elliotn-ubuntu:~$ 

```

help guys I installed fglr from the repo via synaptic

---

### Post by QIII on 2012-09-07
The ATI Radeon X... series cards are no longer supported by the ATI driver.  Are you sure about the model?  Is it an ATI Radeon HD 3xxx series?

---

### Post by elliotn on 2012-09-07
> **QIII said:**
> The ATI Radeon X... series cards are no longer supported by the ATI driver.  Are you sure about the model?  Is it an ATI Radeon HD 3xxx series?
no no its a ATI Radeon HD 2400

---

### Post by QIII on 2012-09-07
First:  since amdcccle is a graphical interface, you should use gksudo to avoid problems with changing ownership of files!

Did you install fglrx-updates and fglrx-amdcccle-updates by chance?  That causes problems for many users.  So does using graphical methods to install the driver.

---

### Post by elliotn on 2012-09-07
> **QIII said:**
> First:  since amdcccle is a graphical interface, you should use gksudo to avoid problems with changing ownership of files!

Did you install fglrx-updates and fglrx-amdcccle-updates by chance?  That causes problems for many users.  So does using graphical methods to install the driver.

nope I didn't install that at all

---

### Post by QIII on 2012-09-07
Sometimes graphical installation methods do not work.  Why that is true is a mystery to me.

I generally recommend the "Using the Ubuntu repository, alternate command line method" as described in the ATI driver wiki in my signature.

---

### Post by elliotn on 2012-09-08
its solved but don't know exactly how to put it but I purge removed fglrx and amdcccle then installed a kernel patch with a module.... hell I don't remember what I exactly did but it all got fixed

---

