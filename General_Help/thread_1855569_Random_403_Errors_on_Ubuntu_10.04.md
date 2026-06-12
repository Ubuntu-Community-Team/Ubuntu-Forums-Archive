---
title: "Random 403 Errors on Ubuntu 10.04"
date: 2011-10-06
forum: General Help
---

### Post by sgmurphy19 on 2011-10-06
I have apache2, Ubuntu 10.04 server, ISPConfig3 using virtual hosts and a I am experiencing the following strange behavior. 
I can browse a given site on my server for awhile but eventually it will throw a 403  forbidden error. If I wait about 1 minute then refresh the page will  load properly. If I restart apache, the page will reload immediately.

Has anyone else experienced this sort of behavior before?

I am open to any ideas.

Thanks!
Sean

---

### Post by sgmurphy19 on 2011-10-06
Ok, I think I have it figured out. I had the module mod-evasive enable.  Disabling this seems to have fixed it. At least I've gone over 100  clicks without generating a 403 error.

---

