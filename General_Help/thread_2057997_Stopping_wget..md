---
title: "Stopping wget."
date: 2012-09-14
forum: General Help
---

### Post by cheat117 on 2012-09-14
Hello, Im writing a web page and since I know how wget can grab web files, how can i stop wget from downloading my file?

I was thinking an embedded control-c could work but then i remembered that it grabs by filename, not filecontent. is there a way short of robots.txt(which can be set to be ignored.)?

---

### Post by dniMretsaM on 2012-09-14
I suppose you could block the wget user agent, but the downloader can easily get around this with the [FONT=Courier New]--user-agent[/FONT] option.

And just curious, but why do you want to do this?

---

### Post by wojox on 2012-09-14
> **dniMretsaM said:**
>  can easily get around this with the [FONT=Courier New]--user-agent[/FONT] option.

Then all your pages are belong to us. :p

---

### Post by dniMretsaM on 2012-09-14
> **wojox said:**
> Then all your pages are belong to us. :p

Lol so true. :lol: If it's on the Internet it can be downloaded. No getting around that (due to the fact that it needs to be downloaded to be viewed...).

---

