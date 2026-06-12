---
title: "Last upgrade stops my video"
date: 2009-10-04
forum: General Help
---

### Post by xxxwwwxxx on 2009-10-04
Hello,
After receiving last upgrade I can't play any video or audio but ubuntu sounds works good... Any player starts and closes at ones. How to return back old versions of packages which were before installing?

Also I tried to install LXDE I mentioned that it should work but same story appears. Now LxDE deleted all important packages like gnome network manager and so on... so Now I am without internet and I want to install it from CD but it always says me that server does not reachable but I have tick near CD-Rom in repository options... why it does not want to install from CD... CD-rom is mounted.

---

### Post by 3rdalbum on 2009-10-04
Have you by any chance added the PPA for Openshot video editor?

That is known to completely bork video playback; how ironic.

The solution is to disable the Openshot PPA and "force version" back to the old versions, on the packages whose names start with "libav". They must be done in the correct order or it will try to remove all packages that depend on ffmpeg. If you use the Force Version function on a package and it says that it will also mark VLC and others for deletion, then click Cancel and try Force Versioning another package, until they are all done.

Don't try following this if you haven't added the PPA repository for Openshot Video Editor.

---

### Post by xxxwwwxxx on 2009-10-04
Probably error not in video... because it is same with any mp3 file
I have not chosen any extra options than Standart update

I installed some extra players and some of them works ok...
But gnome player starts and closes at ones...

---

