---
title: "&quot;Invalid Encoding&quot; after downloading a Music"
date: 2010-10-29
forum: General Help
---

### Post by benyben123 on 2010-10-29
Hi
I downloaded music from my own cloud backup (old music that I have), and it's not in English (if that makes a different). 

When I extract, the folder is showing up like this:

??????? (Invalid Encoding)


What can I do?
:(
thanks

---

### Post by utterness on 2010-12-09
I ran into the same problem.  I'm trying to find another program that won't cause this error atm.  I'll report back here if I find a solution.

---

### Post by tredegar on 2010-12-09
I think the problem is that linux is using UTF-8 and your character set is different.
The names need to be converted, there's a perl script called **convmv** to do this for you.

See here: [http://freshmeat.net/projects/convmv/](http://freshmeat.net/projects/convmv/) or search on it
It is in the (lucid) repositories.

Edit: here's a nice HOWTO 
[http://www.linux-support.com/cms/en/component/content/article/57589-migration-of-file-and-directory-names](http://www.linux-support.com/cms/en/component/content/article/57589-migration-of-file-and-directory-names)
/Edit

---

### Post by utterness on 2010-12-11
fixed it with UTF-8 Migration Tool in my repositories.  ran that and it scanned my files for any conversions and found everything needed then fixed them up.  the files I had truble with are now fine.

---

