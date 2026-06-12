---
title: "Couponing with Bash"
date: 2011-01-09
forum: General Help
---

### Post by Xoanan on 2011-01-09
Hi All

I am trying to assist my wife with some couponing and I feel that there is probably an easier method of retrieving all the info we need to make it work.  For instance, I was thinking that instead of going to Kroger.com to look for the deals, I could use either wget or elinks to pull up the page, and use grep to look for the deals and list them.  

Unfortunately, for Kroger.com, you have to enter in your zip code before you look.  Any thoughts on this little project?:P

---

### Post by hawkmage on 2011-01-09
If you look at the HTML source of the page you should be able to see what the field name is for the ZIP you need to enter and then you can use wget and the "--post-data=STRING" option.  The URL you want to use is the one for the form post action.  If the site sets a sesion cookie you will need to use the "--save-cookies=FILE" option on the inital request and then "--load-cookies=FILE" on subsequent requests.

---

