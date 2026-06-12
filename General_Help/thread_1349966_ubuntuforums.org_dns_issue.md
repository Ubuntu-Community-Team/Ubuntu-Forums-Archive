---
title: "ubuntuforums.org dns issue"
date: 2009-12-08
forum: General Help
---

### Post by billybowden on 2009-12-08
I want to add ubuntuforums.org to my hosts to make visiting the site faster. To do this I have used nslookup, dig, ping and they report the ip address of ubuntuforums.org to be 91.189.94.12. However enter this into a browser and you are directed to [http://www.canonical.com/](http://www.canonical.com/). To get to this site you have to enter ubuntuforums.org. So what is happening am I being redirected?

---

### Post by slakkie on 2009-12-08
Apache has a default setting, that it will redirect you to the first vhost config if it cannot find a correct vhost definition. I suspect something like that.

---

### Post by dcstar on 2009-12-09
> **slakkie said:**
> Apache has a default setting, that it will redirect you to the first vhost config if it cannot find a correct vhost definition. I suspect something like that.

Yep, you need a URL in the browser so the correct Host Header is delivered.

The days of every website having a unique IP address are long gone.

---

