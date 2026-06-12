---
title: "Redirecting URL?"
date: 2010-04-09
forum: General Help
---

### Post by nizdobs on 2010-04-09
Here's the scenario:

I like the idea of using GoodSearch as a search engine to give me the search results I need while benefiting a charity I support. My family is theoretically on board with this but we all forget to go to goodsearch for searches and instead go to google by force of habit.

I'd like to configure my ubuntu box so that anytime a user types [www.google.com](www.google.com) into any browser they get redirected to [www.goodsearch.com](www.goodsearch.com).

Is this possible? Any reason it's not a good idea?

Thanks,

- Niz

---

### Post by elliotn on 2010-04-09
u can just tell em to go to goodsearch.com

---

### Post by lisati on 2010-04-09
I'm don't know how it might be done in Ubuntu - perhaps through some kind of proxy? - but my router (Thomson Speedtouch) offers an option to do that on its Parental Control settings page.

---

### Post by emanuel.b on 2010-04-09
You could perhaps set it as your homepage...

---

### Post by fragos on 2010-04-09
Open Chrome Options, Basic tab and click the Manage button. You'll be able to add the search engine you wish to use and set it as default.

---

### Post by Wardje on 2010-04-09
I think it's easier to add visual indications towards using goodsearch on your computer then. For example setting it as standard in the search bar as well as a bookmark to it in bookmarks bar.

If you want to go really extreme I guess you could edit
```
/etc/hosts
```
but I'd advice against that for this particular purpose :o

---

### Post by new_tolinux on 2010-04-09
If goodsearch has a static IP, you could edit your /etc/hosts file.
```
999.999.999.999 www.google.com
```

If you've got a webserver/website with a static IP, you could edit your /etc/hosts file.
If that webserver is "local", it is no problem either.

Then just create some basic HTML-page, probably you want to do some explaining on _why_ they come there when they typed google in the address bar.
Keep it simple, not too long, and place a clickable link to the desired searchpage.

---

