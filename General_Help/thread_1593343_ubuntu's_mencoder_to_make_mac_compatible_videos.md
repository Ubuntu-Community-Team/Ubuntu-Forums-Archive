---
title: "ubuntu's mencoder to make mac compatible videos"
date: 2010-10-11
forum: General Help
---

### Post by adamSpline on 2010-10-11
Hi all,

I am using an ubuntu server to generate movies from a set of images for a web app.  Using mencoder, my current method is working well, but the videos it produces do no seem to be compatible with the typcial mac setup.  This is the command I am using:
```

mencoder mf://@imagePaths.txt -mf fps=30 -o myVid.avi -ovc lavc -lavcopts vcodec=msmpeg4v2:vbitrate=800
```I like the results I get from this command (decent speed to encode and small files), but I really need it to work on a mac also.  Any ideas?  Thanks,

-Adam

---

