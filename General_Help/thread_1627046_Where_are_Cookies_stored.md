---
title: "Where are Cookies stored?"
date: 2010-11-21
forum: General Help
---

### Post by Liliitha on 2010-11-21
I have been looking all over for this answer.  I know how to delete cookies, I actually want to open the cookie files and read them.  I can do it on Window's IE but I am not sure if Firefox even saves cookies to an open file like that.  Any ideas on what to do or how Firefox is holding cookies?  I've looked under firefox's folder in the root directory, but still nothing.  Windows had them in a hidden file, maybe there is a hidden file for this too or something else?

---

### Post by maruchin on 2010-11-21
Hi,

cookies are in your /home directory.
just cd .mozilla/firefox/
then there has to be a weird directory name.
mine is 68oyiz3n.default
And in this directory there is the cookies.sqlite file.
this is what you are looking for.

regards
maru

---

### Post by lovinglinux on 2010-11-21
> **maruchin said:**
> Hi,

cookies are in your /home directory.
just cd .mozilla/firefox/
then there has to be a weird directory name.
mine is 68oyiz3n.default
And in this directory there is the cookies.sqlite file.
this is what you are looking for.

regards
maru

You need a sqlite database reader, like sqlitebrowser, to read that.

You can read the cookies in Firefox by going to the Privacy tab in Preferences. There is a "Show Cookies" button there.

---

