---
title: "installing plr and postgres 8.3 on 9.10"
date: 2009-12-29
forum: General Help
---

### Post by pinan on 2009-12-29
Hi 

I trying to install plr under postgres 8.3 on ubuntu 9.10 the Karmic Koala.

I had assumed it was the case that you had to do something like


psql database < plr.sql

Where plr.sql can be found in /usr/share/postgresql/8.3/plr.sql

When I attempt to run this I get diagnostics

could not load library "/usr/lib/postgresql/8.3/lib/plr.so": libR.so: cannot open shared object file: No such file or directory
etc

I have libR.so in  /usr/lib/postgresql/8.3/lib/plr.so

I have LD_LIBRARY_PATH set to 

LD_LIBRARY_PATH=/lib:/usr/lib:/usr/local/lib:/usr/lib/postgresql/8.3/lib

Have I forgotten to do something or is this a known issue?

---

### Post by pinan on 2009-12-30
It seems the problem is that  libR.so is not being found.

I attempted to hack envronment for the local postgres cluster in /etc/postgresql/8.3/main by adding an LD_LIBRARY_PATH statment eg
LD_LIBRARY_PATH=/usr/lib/postgresql/8.3/lib:/usr/lib/R/lib
export LD_LIBRARY_PATH

That did not work.

Doing an ldd on the ldd /usr/lib/R/lib/libR.so indicated an unbound  libR.so

So my fix was to insert a file in to /etc/ld.so.conf.d with the contents /usr/lib/R/lib

The plr install script works as expected.

---

### Post by ron619 on 2011-02-06
Then the "The Lazy *Man's Guide*  to Online Business" just might be the most important *ebook* you ever read. Here's why: Your own online business can be a "lazy [B]...

[/B][URL="http://www.plrprivatelabelrights.com/private_label_ebooks/diet_ebooks/summer_diets"]
[/URL] 							 								[Diet Ebooks]("http://www.plrprivatelabelrights.com/private_label_ebooks/diet_ebooks/summer_diets")

---

### Post by mini02 on 2011-02-25
**Important!** Please note that in order for us to perform successful tracking of each post, you must have the **URL**
 shown and clickable in your post as a link, so please make sure that it
 is included in the posting at the end. You need to build this link 
manually using URL and URL Text fields. **URL Preview** field shows how your **URL Link should look like** when posted at the end of signature.

<a href="[http://www.plrprivatelabelrights.com/plr-ebooks/online-ebooks/seo-ebooks]("http://ubuntuforums.org/view-source:http://www.plrprivatelabelrights.com/plr-ebooks/online-ebooks/seo-ebooks")">SEO Ebooks </a>
[url=
[http://www.plrprivatelabelrights.com/plr-ebooks/online-ebooks/seo-ebooks]("http://ubuntuforums.org/view-source:http://www.plrprivatelabelrights.com/plr-ebooks/online-ebooks/seo-ebooks")"]SEO Ebooks[/url]

---

### Post by mini02 on 2011-02-25
**Important!** Please note that in order for us to perform successful tracking of each post, you must have the **URL**
 shown and clickable in your post as a link, so please make sure that it
 is included in the posting at the end. You need to build this link 
manually using URL and URL Text fields. **URL Preview** field shows how your **URL Link should look like** when posted at the end of signature.


[]("http://www.plrprivatelabelrights.com/plr-ebooks/online-ebooks/seo-ebooks")[SEO Ebooks]("http://www.plrprivatelabelrights.com/plr-ebooks/online-ebooks/seo-ebooks%5B/URL%5D")

---

