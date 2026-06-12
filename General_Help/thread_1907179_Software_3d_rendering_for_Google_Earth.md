---
title: "Software 3d rendering for Google Earth"
date: 2012-01-10
forum: General Help
---

### Post by hcurtiss on 2012-01-10
First, total newb, and loving first experience with linux.  I have a Lenovo T410s with the Intel HD GMA on-chip video, running Ubuntu 11.10, and Google Earth 6.1.0.  I'm getting an error on GE startup that says clamped polygons aren't supported because my graphics card wont't support it.

Of course, the machine will support it (works fine in Windows).  I'm pretty certain this is an intel driver problem.  This page ([link here]("https://bugzilla.redhat.com/show_bug.cgi?id=543920")) indicates that if I set Ubuntu to use software OpenGL 3d rendering for Google Earth it will work.  The command listed

LIBGL_ALWAYS_SOFTWARE=1 googleearth

doesn't seem to work in Ubuntu ("googleearth: command not found").  Is there a way to set Google Earth to use software 3d rendering in Ubuntu?

---

### Post by hcurtiss on 2012-01-10
I should also add, FWIW, the out of the box video drivers for Ubuntu actually work better than the Intel Windows drivers (screen refreshes WAY faster.  It's just google earth that tells me my video card is deficient.  It's totally humiliating.  Somebody please save my relationship with google earth.

---

### Post by hcurtiss on 2012-01-10
Well, for what it's worth, I made some progress.  

From terminal, I navigated to usr/bin, then I used 

LIBGL_ALWAYS_SOFTWARE=1 google-earth

That starts Google Earth, but then it gives me a warning that I'm opening in Open GL Software Emulation mode, and recommends using DirectX mode.  If I click No, the program shuts down (terminal indicates it's crashing).  If I click yes (to run in DirectX mode), then it opens.

And what do you know, there are my polygons!!  UNFORTUNATELY, the display refresh is TERRIBLE.  Just crawling.  Still working on it.  Help much appreciated.  It seems like DirectX mode sucks, and I'd like it to run in Open GL Software Emulation mode, but it just shuts down.  Help?

---

