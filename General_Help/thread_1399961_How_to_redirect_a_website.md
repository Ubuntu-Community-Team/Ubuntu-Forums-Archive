---
title: "How to redirect a website?"
date: 2010-02-06
forum: General Help
---

### Post by karthick87 on 2010-02-06
I like to redirect some websites to google.com how to perform this?For example when i enter "www.abc.com" it should redirect it to "www.google.com"

---

### Post by nc_jed on 2010-02-06
I like using the Meta Refresh method ([http://en.wikipedia.org/wiki/Meta_refresh](http://en.wikipedia.org/wiki/Meta_refresh)).  This has the benefit of allowing you to insert a database call or a script to count usage or populate other database tables.  

Put the scripts in your index.htm(l) page and users to [http://www.abc.com](http://www.abc.com) won't have to specify a page (index loads by default).  Also, consider putting this script on your error pages (404, 500, etc).

- Jed

---

### Post by nikhilbhardwaj on 2010-02-06
you could make static mapping in /etc/hosts

---

### Post by t4thfavor on 2010-02-06
You can use response.redirect("site) in some javascript, or you could set up a proxy on apache, if you have multiple places you need different sites redirected to.

---

### Post by karthick87 on 2010-02-06
I am using squid Proxy,so is there anyway to redirect a website using that proxy?

---

### Post by t4thfavor on 2010-02-11
I am sure there is, you can probably redirect anything with squid, it's just complicated. You will probably need to get really familliar with the doc.

---

### Post by lisati on 2010-02-11
> **getyourkarthick said:**
> I like to redirect some websites to google.com how to perform this?For example when i enter "www.abc.com" it should redirect it to "www.google.com"

My main router has a similar facility built in to its parental controls.

---

