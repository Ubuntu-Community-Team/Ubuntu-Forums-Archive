---
title: "CAD System?"
date: 2010-04-20
forum: General Help
---

### Post by rocket16 on 2010-04-20
Friends, a friend of mine asked me about CADs for Ubuntu. I referred to QCAD and Cycas. But online, I find that QCAD is not free. But however, in Synaptic, it is shown as a free Software. I also installed QCAD (from command line, sudo apt-get install qcad command). But it is not shown in Software Centre. What is the reason?

See here: [http://www.qcad.org/](http://www.qcad.org/) To see, that QCAD is non-free.

But why is it then in Ubuntu repository as a free download?

---

### Post by valhemmer on 2010-04-20
what about autcad, theres a free student version that i'd like to put on my system but i dont know if it runs native in linux or myb in wine. anyone know about acad running on any linuxs

---

### Post by rocket16 on 2010-04-20
I am mainly talking about QCAD, and AutoCad on wine will be slower. My question is related to QCAD, why is it commercial but available for free download as a Synaptic Package? Thanks for any reply.

---

### Post by rocket16 on 2010-04-20
Oh, I got it. There is a Community version, for Linux. And that is in Ubuntu repository. It is shown in [http://www.qcad.org/qcad_downloads.html](http://www.qcad.org/qcad_downloads.html)

---

### Post by Untitled_No4 on 2010-04-20
From [http://en.wikipedia.org/wiki/QCad](http://en.wikipedia.org/wiki/QCad) :
> QCad is a computer-aided design (CAD) software package for 2D design and drafting. It is available for Linux, Mac OS X, Unix and Microsoft Windows. The QCad Community Edition, which lacks functionality present in the full version[1], is released under the GNU General Public License and is not (officially) available for Windows[2], though unofficial builds do exist. Precompiled packages are available for some Linux platforms, such as Debian, via the distribution's package manager.

It's similar to VirtualBox. You have the OSE edition and the proprietary edition (which is closed source but free as in beer).

As to why you don't find an icon in your menu perhaps the system just didn't generate one. Press Alt + F2 and type qcad and then press enter, see if it runs. 
This is with the assumption that the qcad is the name of the file, but I don't know for sure if it is.

---

### Post by scania_gti on 2010-04-20
[**Community Edition** (Source Code, GPL)]("http://www.qcad.org/qcad_downloads.html") is free :)

---

### Post by rocket16 on 2010-04-20
Thanks to all, for the info.

---

### Post by Gemnoc on 2010-04-26
The CAD on Linux field has been bleak for a long time, but it's finally starting to get interesting.

On the commercial side of it, two CAD companies are working on Autocad clones running on Linux: Bricscad from Bricsys, and ARES from Graebert. Both should offer Light (2D only) and Pro (ACIS modeling) versions by the end of 2010.

Bricsys has an open development program: anybody can freely download the alpha release to test it out, provided you register and supply some personal info. Latest release is expiring by April 30th, so I suggest you monitor the [Bricscad for Linux forum]("https://www.bricsys.com/common/support/forumtopics.jsp?forum=20") where the next release should be announced in the coming week. (I've reviewed Bricscad on my "CAD on Linux" blog: if anyone is interested, look at my profile for the link to my website.)

Graebert has also a beta-test program that you can apply to, but it's more "closed": the EULA requires that you don't divulge any specifics on it. You can register on [their website]("http://www.graebert.com/#18") (look for the February 9th entry).

On the open source side, there is no finalized app yet, but two projects are starting to take shape: [FreeCAD]("http://sourceforge.net/apps/mediawiki/free-cad/index.php?title=Main_Page") and [HeeksCAD]("http://code.google.com/p/heekscad/"), both 3D modeling apps based on OpenCascade. HeeksCAD might be somewhat difficult to install on Ubuntu, but FreeCAD is in Lucid's repositories.

---

### Post by Greg Hood on 2010-06-18
I may be entering the discussion a little late, but I hope someone is still watching or reading. I too am an AutoCAD user. To answer one question, the older student version wer NOT print enabled. AutoCAD LT is just what it sound like, good but not fully enabled. 
 
Now what brings me here is I am about to make the leap off the Windows wagon, but I would still like to use my various versions of AutoCAD. I see a bunch of people talking about QCad - are all files tranferrable without data loss and how's the user interface? How much is QCad and should there be a truely free version is it fully enabled? The simplest solution for me is to continue using AutoCAD. Lastly, at least for the moment, has anyone tried downloading RIVET files to any Linux based CAD program? A lot of questions... 
 
Thanks / G

---

### Post by Gemnoc on 2010-06-18
> **Greg Hood said:**
> Now what brings me here is I am about to make the leap off the Windows wagon, but I would still like to use my various versions of AutoCAD.
Word of advice: you need to run your various versions (why more than one btw?) of AutoCAD? DON'T make the leap. Stay on Windows, save yourself headeaches. Or do a dual-boot: keep your Windows partition for your CAD work, and Ubuntu for everything else. Running AutoCAD with Wine is a stopgap measure, it won't run as well as in Windows (if you ever succeeed in making it running), plain and simple.

[quote=Greg Hood]I see a bunch of people talking about QCad - are all files tranferrable without data loss and how's the user interface? How much is QCad and should there be a truely free version is it fully enabled?[/quote]
Forget QCad. It takes DXF 2000 only, no DWG. It has limited features, and a not a very good UI, even the commercial version (which is only about 30€).

[quote=Greg Hood] The simplest solution for me is to continue using AutoCAD. [/quote]
Then see my first answer above.

> Lastly, at least for the moment, has anyone tried downloading RIVET files to any Linux based CAD program? 
Did you mean REVIT ? If REVIT's file format is proprietary, I'm guessing no other app can open it, be it on Windows or otherwise.

---

