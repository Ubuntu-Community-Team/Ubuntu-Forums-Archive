---
title: "Octave 3.2.4 in Lucid (10.04)"
date: 2010-05-26
forum: General Help
---

### Post by kakila on 2010-05-26
Hi everybody,

I usually compile Octave from source code, since compilation works perfectly.
When recompiling for Ubuntu 10.04 I got the following "errors" (look like warnings to me)

/usr/local/share/applications/www.octave.org-octave.desktop: error: (will be fatal in the future): value "Math" in key "Categories" in group "Desktop Entry" requires another category to be present among the following categories: Education;Science
/usr/local/share/applications/www.octave.org-octave.desktop: error: (will be fatal in the future): value "Science" in key "Categories" in group "Desktop Entry" requires another category to be present among the following categories: Education

Can anybody explain to me what odes it mean.

Thanks,

JPi

---

### Post by dino99 on 2010-05-26
be sure to only use lucid repo into synaptic repo

clean the cache then update upgrade

[http://ubuntuforums.org/showthread.php?t=1471235](http://ubuntuforums.org/showthread.php?t=1471235)

[https://launchpad.net/ubuntu/+ppas?name_filter=octave](https://launchpad.net/ubuntu/+ppas?name_filter=octave)

---

### Post by kakila on 2010-05-26
Hi
Thanks for the prompt answer.
I am not using the synaptic repo, I am compiling from source code downloaded form Octave website. I want t use 3.2.4

Does this make any difference?

JPi

---

### Post by dino99 on 2010-05-26
maverick repo have 3.2.4-6 package, so you can update your sources.list, update, install octave, then change sources.list back to lucid and update again to clean the cache.

---

