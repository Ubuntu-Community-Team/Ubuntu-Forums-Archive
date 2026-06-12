---
title: "Can't find offical java relase in ubuntu apt-get repositories"
date: 2010-08-18
forum: General Help
---

### Post by timewaves on 2010-08-18
Hey all!

I'm trying up upgrade my lab's ubuntu-based appserver to v10.04 from 9.04.

The problem is that the default lucid apt-get repositories do not contain the Sun's official distribution like Jaunty's does.  Is there any way to get the official Java distribution on lucid (not sure how the others measure up) or is it just not officially supported?

Thanks in advance -

---

### Post by Sef on 2010-08-18
Applications > Ubuntu Software Center > Edit > Software Sources > Tic Universe and Multiverse.  Sun Java is under Multiverse because it is not free (as in speech) software.  If you want free (as in speech) Java, then use OpenJDK.

---

### Post by McNils on 2010-08-18
sun-java has been moved to a partner repo. Just enable it and install.

---

### Post by Vrroom on 2010-08-18
Also after enabling partner repositories and installing java....go to official sun website and test that whether it installed correctly or not...it will show you  the current version also

---

### Post by timewaves on 2010-08-18
Thank you for your help everybody - Problem solved.

Both universe and multiverse were checkmarked by default, that's not what was holding me back.

I went to the "other software" tab and checked the:
archive.canonical.com/ubuntu lucid partner 
checkbox and was able to install java from apt get

out of curiosity why isn't that checked by default, and is what I checked a repository of packages from old distros?

Cheers!

---

