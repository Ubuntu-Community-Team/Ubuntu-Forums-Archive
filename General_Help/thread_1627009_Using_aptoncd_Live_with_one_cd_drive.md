---
title: "Using aptoncd Live with one cd drive?"
date: 2010-11-20
forum: General Help
---

### Post by planetofdeviants on 2010-11-20
I'm using a Live edition and am trying to load an archive of apt files made by aptoncd.  I only have one cd/dvd drive, so I'm trying to do it from a iso file on non-cd/dvd drive.

Having trouble getting aptoncd to load from this the archive iso it made.

I've tried mounting the iso with:
mount -o loop apt-archive.iso /aptmountpoint, but aptoncd doesn't recognize this virtual cd.  Is it possible to get aptoncd to do its search and think a virtual mount is a real one?

I've thought about the command line and these are the only options in the man page:

OPTIONS
       APTonCD accept the following command-line call methods:

       -c, --packages-list=FILE
              Starts aptoncd listing the packages in FILE

       -l, --cache-dir=PATH
              Uses PATH as apt cache dir (instead of /var/cache/apt/archives

       -r, --temp-dir=PATH
              Uses PATH as temporary directory for copying files and mounting images


I haven't got those to load anything into it's gui.  Anyone know what to do in this situation?

---

