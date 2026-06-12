---
title: "Ogre problems in hardy"
date: 2010-02-02
forum: General Help
---

### Post by r.stiltskin on 2010-02-02
I installed libogre-dev, libode0-dev and related packages and tried to compile the first tutorial code here: [http://www.ogre3d.org/wiki/index.php/Basic_Tutorial_1]("http://www.ogre3d.org/wiki/index.php/Basic_Tutorial_1").

It failed, giving "ExampleApplication.h: No such file or directory" as the reason.  That file was not part of any of the 13 packages just installed so I grabbed a copy that I found online and recompiled.  This time it failed on "ExampleFrameListener.h: No such file ..." so I downloaded a copy of that and tried again.  Failed again on "OIS/OIS.h: No such file ..."  I installed libois-dev and tried again.  Finally, I was able to compile the basic tutorial, but when I try to run it, it crashes with:
"OGRE EXCEPTION(6:FileNotFoundException): 'resources.cfg' file not found! in ConfigFile::load at OgreConfigFile.cpp (line 84).

This is getting monotonous.  Do the Ubuntu Ogre packages work for anybody, or do I have to build it from source?

Edit: solution is in this thread: [HowTo: Install and Use OGRE]("http://ubuntuforums.org/showthread.php?t=1148570").  (It might also be OK to use the binary packages, including libois-dev, but still follow the "Creating an OGRE Project" instructions in the HowTo".)

---

