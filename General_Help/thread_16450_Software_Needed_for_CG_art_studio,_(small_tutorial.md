---
title: "Software Needed for CG art studio, (small tutorial included)"
date: 2005-02-21
forum: General Help
---

### Post by polaris30 on 2005-02-21
Hi all!

There are a few software packages I would like to request to be put into the apt repositorys, or for someone to please post some instructions on how to get them compiled/installed/running with either warty or Hoary.... I am currently running warty

Thanks In Advanced for this help (TIA) !!

Others I am listing I already have working,I will post some install instructions for other CG artists to get a quick head start on some great software! most titles you will need working OpenGL, and a kernel update for whatever processor you own (mine !686)......

Titles I need:

Cinelerra-
Please, I need this software verry bad!!! anyone know how to get it working please post instructions... this software has a 32 and 64 bit build.... Verry cool stuff!
[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)

LiVES video editing software-
yet another cool video editing software.... Great features with this one!
[http://www.xs4all.nl/~salsaman/lives/](http://www.xs4all.nl/~salsaman/lives/)

Kino-
Even more Video editing Goodness!
 [http://kino.schirmacher.de/article/static/2](http://kino.schirmacher.de/article/static/2)




Titles I already got Running, If I am not installing the titles right, please feel free to correct me.. I am verry new to linux:

Blender 3d Bleeding edge version-
 I have this software running on warty warthog with 686 kernel, and Nvidia drivers for Open GL . 
install is totaly painless, download the NON-static version, uncompress it into your desired location(home/yourname/ is best place), and then open the blender folder you uncompressed , and loook inside folder for .blender folder (press control H in nautalis to see the hidded file), copy .blender folder into your /home folder.... If you want to run blender from any command line you must make symbolic link in your /usr/local/bin, otherwise just point your launcher icon at the blender executable... 
To run .blend files by clicking on them in file manager , you must simply associate .blend files with the blender executable, rightclick and look in file propertys... 


Wings 3d bleeding edge STABLE version- 

Verry simple install ! down load linux version, find it in console window, and type :
$gunzip wings3d.restofthefilenamehere.run.gz
and then simply
$sh wings.etc.foo.whatever.run
it will make a "wings3D" folder in your /home/youname/ folder, look there for executable file, and 
$sh wings
to run it.
if you want it to open .wings files just find a wings file and rightclick on it in nautalis and tell it  to open with wings in the propertys...
to run from any command line just make a symbolic link in your /usr/local/bin
I recomend NOT useing the Wings that is in synaptic, it is verry outdated, and you will be missing out on  a BUNCH of features.

Gimp2.2 - yet another Piece of software I got running pretty good.... this is an easy one! type:
Ubuntu Backports 
in a Google search window and go to the current backports page and follow instructions. you can get this with synaptic! 

well, that is it for now... hope i was able to help someone....
Thanks for anyone helping me with the above titles... also for any future corrections on my install methods....


Have a nice day everyone :)

---

