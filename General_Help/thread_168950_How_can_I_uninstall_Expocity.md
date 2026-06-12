---
title: "How can I uninstall Expocity?"
date: 2006-05-01
forum: General Help
---

### Post by mankyuhan on 2006-05-01
I installed expocity. 
My first trial failed, but the second trial was successful..(kind of..)
but, it takes more than minute to load metacity when I log in.
It was not like this until I installed expocity.  So, I like to uninstall expocity.
But, I don't know how.

Can someone please tell me how?

Thanx

---

### Post by Ramses de Norre on 2006-05-01
How did you install it?

---

### Post by mankyuhan on 2006-05-01
I followed this post.
[http://www.ubuntuforums.org/showthread.php?t=148709&highlight=expocity]("http://www.ubuntuforums.org/showthread.php?t=148709&highlight=expocity")

Still, Can anyone answer my original question?

---

### Post by Ramses de Norre on 2006-05-01
I see it's compiled from source, did you use checkinstall? If so: sudo dpkg -r package_name, if not: you'll need to search and remove all files manually, deleting the executables will stop it from executing.
Did you replace your original metcity with it? In that case you'll need to reinstall that.

---

