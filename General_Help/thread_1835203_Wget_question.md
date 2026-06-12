---
title: "Wget question"
date: 2011-08-28
forum: General Help
---

### Post by yeikel on 2011-08-28
Hi , I have a little question with the tool wget...

I have a website that have this estructure : 

website.com\images\1
website.com\images\2
website.com\images\3
.....

I want to download all files at \images\ including the sub directories..

I tried wget -r  website\com\images but I just get index.html from \1\ and not the jpg files :( 

Thanks :guitar:

---

### Post by papibe on 2011-08-28
Even using the -r options has to be called with an actual page not a directory. If you open that address in the browser, what happens? Are you redirected to another page?

Regards.

---

