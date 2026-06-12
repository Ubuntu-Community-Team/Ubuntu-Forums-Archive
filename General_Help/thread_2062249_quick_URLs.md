---
title: "quick URLs"
date: 2012-09-24
forum: General Help
---

### Post by sienile on 2012-09-24
I'm looking to make a set of "quick URLs", meaning ultra-short URLs for sites I frequently go to. I know in Windows this can be done via the HOSTS file, but I'm not sure if it can be done in Linux and I don't want to break anything by trying without confirming that it's safe.

I know the HOSTS file in Linux is /etc/hosts. Opening it up I see the top portion looks similar to the Windows one. > 127.0.0.1	localhost I want to know if it's possible to have a URL instead of an IP for the first portion.

If this method won't work, what would be the proper way to make the quick URLs? (Example: G = [www.google.com](www.google.com))

---

### Post by vasa1 on 2012-09-24
> **sienile said:**
> I'm looking to make a set of "quick URLs", meaning ultra-short URLs for sites I frequently go to. I know in Windows this can be done via the HOSTS file...

If this method won't work, what would be the proper way to make the quick URLs? (Example: G = [www.google.com](www.google.com))

Have you yourself done it in Windows? Do you then type G in your browser address bar and that takes you to [www.google.com?](www.google.com?)

I do things quite differently. Either use the browser's bookmarks or have a local page with frequently visited links. In the latter case, I could have:
```
<a href="www.google.com">G</a>
```
Then, I click on G and I'm taken to [www.google.com](www.google.com).

---

### Post by sienile on 2012-09-24
Yeah, it works great in Windows XP.

I'm trying to avoid using a local page to do it. And I like to have as few bookmarks as possible so they all fit on the toolbar. I reserve that space for hard to remember URLs.

---

### Post by vexorian on 2012-09-24
You could just put one of google IP addresses: 173.194.37.98.

I actually find it odd that windows allows you to place hosts. in There.

What happens if you put:

google.com google.com 

In windows?

Ok... may be I need to grab somebody's windows computer...

---

