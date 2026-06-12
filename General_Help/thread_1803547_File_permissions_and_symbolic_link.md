---
title: "File permissions and symbolic link"
date: 2011-07-13
forum: General Help
---

### Post by dwlamb on 2011-07-13
Good day,

I have a challenge with forming a symbolic link for a web development folder symbolically linked to /var/www

My link in www is webdev -> /home/daniel/Documents/webdev

I can not access the contents of webdev unless I modify all the permissions to 777.  Apache returns a Forbidden error.

Is this normal?  If I make a directory simply under my home folder (e.g., /home/daniel/webdev) and redo the symbolic link pointing to that, modification of the permissions is not required.

Is there a way to have the webdev under Documents, create the link and modify Apache settings to allow access without making the directory and all content 777?

Thanks for reading this and have a Great day,

D.

---

