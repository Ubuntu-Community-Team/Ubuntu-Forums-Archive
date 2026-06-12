---
title: "Everytime I add a new package using Synaptic I get the following error:"
date: 2010-02-23
forum: General Help
---

### Post by ale8ster on 2010-02-23
E: nvidia-185-kernel-source: subprocess installed post-installation script returned error exit status 127
E: nvidia-glx-185: dependency problems - leaving unconfigured

I'm not sure what other information to post.  I believe I'm using the nvidia 190 file, but I've tried to remove 185 and that made me have to boot up in "low graphics mode."

---

### Post by ubunterooster on 2010-02-23
it appears 190 has dependencies in the 185 version. or you removed some more packages along w/ the removal of185. try to reinstall 185.

---

### Post by ale8ster on 2010-02-23
I have reinstalled:

nvidia-glx-185
nvidia-185-kernal-source

I get the same error, and it does not seem to re-install the packages.

Details:

dependency problems - leaving unconfigured
No apport report written becuase the error message indicates its a follup error from a previous failure.  
Errors were encountered while processing:
nvidia-185-kernal-source
nvidia-glx-185
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Settup nvidia-185-kernal-source...
/var/ib/dpkg/info/nvidia-185-kernel-source.postinst: 39: /usr/lib/dkms/common.postinst: not found
dpkg: error processing nvidia-185-kernel-source (--configure):
   subprocess installed post-installation script returned error exit status 127 
dpkg:  dependency problems prevent configuration of nvidia-glx-185:
 Package nvidia-185-kernal-source is not configured yet.

...

---

### Post by ale8ster on 2010-02-23
Well, I just started over with a fresh install, and I'm no longer having the issue.

---

### Post by ubunterooster on 2010-02-24
ah yes, the install fixes all. If I had a dollar for ea. time I reinstalled...

please remember to mark this thread as solved. :)

---

