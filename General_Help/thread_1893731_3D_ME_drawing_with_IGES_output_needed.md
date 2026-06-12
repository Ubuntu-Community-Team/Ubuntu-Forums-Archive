---
title: "3D ME drawing with IGES output needed"
date: 2011-12-10
forum: General Help
---

### Post by fester225 on 2011-12-10
I've been spending the last couple of years learning how to use SketchUp. Now that I have a whole mess of files, it has come to my attention I can't use them to generate CNC output files to have those parts made. No matter what I do, SketchUp files will never reliably produce the files I need, it uses the wrong methodology and was never meant to do so.

What (free) 3D drawing programs are available for Ubuntu which will output the IGES files I need? (Using wine is OK.)

---

### Post by oldtimer7777 on 2011-12-10
> **fester225 said:**
> I've been spending the last couple of years learning how to use SketchUp. Now that I have a whole mess of files, it has come to my attention I can't use them to generate CNC output files to have those parts made. No matter what I do, SketchUp files will never reliably produce the files I need, it uses the wrong methodology and was never meant to do so.

What (free) 3D drawing programs are available for Ubuntu which will output the IGES files I need? (Using wine is OK.)

Have you tried this way:

[http://ubuntuguide.net/install-google-sketchup-cad-style-app-in-ubuntu-using-wine](http://ubuntuguide.net/install-google-sketchup-cad-style-app-in-ubuntu-using-wine)

---

### Post by fester225 on 2011-12-10
Between wine and PlayOnLinux (that program helps a lot!), I have SketchUp running fine.

The problem is that the way SketchUp stores information is fundamentally unusable by a program which produces files for CNC machines so they can make things.

Thanks for the thought!

---

### Post by oldtimer7777 on 2011-12-10
> **fester225 said:**
> Between wine and PlayOnLinux (that program helps a lot!), I have SketchUp running fine.

The problem is that the way SketchUp stores information is fundamentally unusable by a program which produces files for CNC machines so they can make things.

Thanks for the thought!

Have you checked out Blender? or Inkscape?

sudo apt-get install blender
sudo apt-get install inkscape

And you can import your SketchUp files into Blender if you like:

[http://www.katsbits.com/tutorials/blender/import-google-sketchup-kmz-models.php](http://www.katsbits.com/tutorials/blender/import-google-sketchup-kmz-models.php)

---

### Post by fester225 on 2011-12-10
Blender is a graphics program intended for artists and movie makers.

It doesn't have an IGES export function.

---

### Post by oldtimer7777 on 2011-12-10
> **fester225 said:**
> Blender is a graphics program intended for artists and movie makers.

It doesn't have an IGES export function.

Try importing your SketchUp files into Blender to test it:

[http://www.katsbits.com/tutorials/bl...kmz-models.php]("http://www.katsbits.com/tutorials/blender/import-google-sketchup-kmz-models.php")

What is it exactly you are trying to accomplish would probably be a better question for me to ask... Maybe there is something native in Ubuntu that will handle the job?

---

### Post by fester225 on 2011-12-10
What (free) 3D CAD/CAM drawing programs are available for Ubuntu which will output the IGES files I need? (Using wine is OK.)

---

### Post by oldtimer7777 on 2011-12-10
> **fester225 said:**
> What (free) 3D CAD/CAM drawing programs are available for Ubuntu which will output the IGES files I need? (Using wine is OK.)

Have you checked into Draftsight? 

[http://www.3ds.com/products/draftsight/download-draftsight/](http://www.3ds.com/products/draftsight/download-draftsight/)

Prerequisite installation packages: 
```
sudo apt-get install libxcb-render-util0 
sudo apt-get install libdirectfb-extra
```And if you are running 64-bit version of Ubuntu you will need to do a force installation of that deb file. Hopefully you are running 32-bit Ubuntu. If it is a production system and you are doing commerial work, don't force it, just install 32-bit Ubuntu.

---

### Post by fester225 on 2011-12-10
Draftsight is 2D.

Do you know about anything else out there?

---

### Post by oldtimer7777 on 2011-12-10
> **fester225 said:**
> Draftsight is 2D.

Do you know about anything else out there?

Have you tried opening a 3d file in Draftsight?

[http://www.jcopro.net/2011/03/23/draftsight-limited-3d-capability/](http://www.jcopro.net/2011/03/23/draftsight-limited-3d-capability/)

[http://www.jcopro.net/2010/12/29/draftsight-review-like-autocad-but-free/](http://www.jcopro.net/2010/12/29/draftsight-review-like-autocad-but-free/)

Sometimes you have to work with with you have, but I will keep looking.

---

### Post by fester225 on 2011-12-11
To be honest, I haven't. The website said Draftsight was for 2D.

---

### Post by oldtimer7777 on 2011-12-11
> **fester225 said:**
> To be honest, I haven't. The website said Draftsight was for 2D.

Well, from the look of the reviews I have read, it appears to open 3d files.  You should give it a go. 

They say it is comparable to AutoCAD LT which saves you around 1000 bucks.  :) 

I can't think of anything else that would be better than Draftsight for what you are trying to do. Hopefully it will work for you.

:popcorn:

---

### Post by Derek Karpinski on 2011-12-11
FreeCAD in the software center may work for you.

---

### Post by Gemnoc on 2011-12-17
Hello,

I'm not writing this for fester since he joined us over at the FreeCAD forums after Derek's suggestion.

For the benefit of others, depending on which Ubuntu version you have, the FreeCAD package in the repos is really outdated (the latest available release is v0.11.4446 in Ubuntu 11.10, Natty and Maverick have v0.10 and Lucid has v0.9). FreeCAD's development has been fast in the past year, and many features were added in the upcoming v0.12 release. It's currently at release candidate status and should be officially published soon.

The FreeCAD team set up two PPAs on Launchpad for people wanting to test the latest version.

[FreeCAD Daily Builds]("https://launchpad.net/~freecad-maintainers/+archive/freecad-daily") updates daily with packages automatically built from the development branch (now set at v0.13)

[FreeCAD Devel]("https://launchpad.net/~freecad-maintainers/+archive/freecad-dev") is manually updated (by me!) every 2-4 weeks whenever I remember to do it, or if someone asks (you can PM*me). These packages are copied from the Daily Builds PPA.

---

