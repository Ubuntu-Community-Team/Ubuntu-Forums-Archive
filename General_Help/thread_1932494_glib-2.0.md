---
title: "glib-2.0?"
date: 2012-02-27
forum: General Help
---

### Post by Ertai87 on 2012-02-27
I'm trying to create a project in Processing ([www.processing.org](www.processing.org)) using video capture.  Apparently a project has been developed to get around the fact that Processing uses Quicktime for its video capture management (located here: [http://gsvideo.sourceforge.net/](http://gsvideo.sourceforge.net/)).  However, after I set up GSVideo and get the libraries imported, I get the following error message from Processing:

> Exception in thread "Animation Thread" java.lang.UnsatisfiedLinkError: Unable to load library 'glib-2.0': libglib-2.0.so: cannot open shared object file: No such file or directory

Can anyone help?  According to the GSVideo site, GSVideo has dependencies on gstreamer and gstreamer-java, but Synaptic has no such packages listed, and trying to apt-get them also gives me no favourable results.

Thanks.

---

