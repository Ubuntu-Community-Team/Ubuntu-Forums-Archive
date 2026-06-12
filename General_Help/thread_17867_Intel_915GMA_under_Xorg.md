---
title: "Intel 915GMA under Xorg"
date: 2005-03-03
forum: General Help
---

### Post by lyly on 2005-03-03
I installed Ubuntu on a Dell Latitude D610 with SXGA extention. I come with an Intel 915 GM/GMA chipset. It seems to be a PCI Express device.

I try to make Xorg work with 1400x1050 resolution. Unfortunatlly the highest resolution I can retrieve is 1280x1024. :cry:

It seems that the driver can't allocate more than 8Mb memory to the card (the 8Mb are set and cannot be changed in the bios(v. A02)) But the card and the panel seems to be well detect.

I have X.org 6.8.2 (upgraded yesterday) installed.

In attachment are my xorg.conf and Xorg.log such as lsmod and lspci ouput files
(The Xorg.log was too big, I had to cut some of it and break it in 2 files)

Thx for any help!

Lynda

---

### Post by lyly on 2005-03-10
Sure? nobody know?

---

### Post by giovanni on 2005-03-18
I'm having similar problems with my D610 with Gentoo.

However the cause is not (only) the lack of memory.
This can be solved by adding the following kernel modules
(with modprobe):
intel-agp (which implies agpgart)
i915 (which implies drm)

By so doing you should get the device /dev/agpgart that
was missing according to your Xorg.log


Bye,
Giovanni

---

### Post by daniels on 2005-03-19
Right -- you can't change the amount of video RAM without AGP.

---

### Post by samo on 2005-04-05
[QUOTE=lyly]
I try to make Xorg work with 1400x1050 resolution. Unfortunatlly the highest resolution I can retrieve is 1280x1024. :cry:
[/QUOTE]

Have you or someone else come to any resolution for this? I'm having the exact same problem. Tried to switch to xfree86 suggested by a friend, but ended up with an empty XF86Config-4 file. So right now I'm back to xorg and 1280x1024...

/ samo

---

### Post by jebr0wn on 2005-06-02
I am having the exact same problem.  Dell Latitude D610 with the Intel 915 Graphics Chipset.

Did anyone find a solution to this? I would really like to run in 1400x1050

--Jason

---

### Post by samo on 2005-06-02
After some reading I found out that it _was_ "not possible" with the Dell BIOS because it does not return 1400x1050 as a valid mode. I found some hacks for other, earlier, Dell machines to fix this type of problem, but they didn't work for the D610. Sorry, but I don't have links to the sources...

(I never solved it, but changed role of my computers, my old D600 went for Linux/Ubuntu and my new D610 got Windows - swapped the disks - and the problems went away. My D600 has an ATI graphics card and works with Ubuntu like a charm, in 1400x1050.)

Regards
Björn

---

### Post by lyly on 2005-06-09
Someone in my university write a patch for the intel driver and a hack for the bios, but for Fedora... 

Unfortunalty as the Ubuntu kernel is not the same as Fedora they don't work, at least in hoary (I didn't test in breezy)...  :cry:

Is someone ready to make an adaptation for ubuntu? please please please  :) 

intel driver: 
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

You can find the patch at
[http://poseidon.epfl.ch/webdav/site/poseidon/shared/intel915gm_latest.patch](http://poseidon.epfl.ch/webdav/site/poseidon/shared/intel915gm_latest.patch)

and the bios hack program:
[http://poseidon.epfl.ch/webdav/site/poseidon/shared/915resolution.tar.gz](http://poseidon.epfl.ch/webdav/site/poseidon/shared/915resolution.tar.gz)

---

### Post by paradox on 2005-07-20
[QUOTE=lyly]

intel driver: 
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=1862&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

You can find the patch at
[http://poseidon.epfl.ch/webdav/site/poseidon/shared/intel915gm_latest.patch](http://poseidon.epfl.ch/webdav/site/poseidon/shared/intel915gm_latest.patch)

and the bios hack program:
[http://poseidon.epfl.ch/webdav/site/poseidon/shared/915resolution.tar.gz](http://poseidon.epfl.ch/webdav/site/poseidon/shared/915resolution.tar.gz)[/QUOTE]

Hi

I have a same card in a Enface laptop. My problem is different: the characters and all images is fuzzy....at now i work under vesa driver but intel driver suggested not compiled yet with Kernel 2.6.11....you find problems with this drivers? Bios hack program, instead, work correctly.

TNX!

---

### Post by bugmenot on 2005-08-20
The 915resolution script is independent of kernel or distro. More info on using it to enable 1400x1050 can be found here: [http://home.comcast.net/~canez/d610/](http://home.comcast.net/~canez/d610/)

---

