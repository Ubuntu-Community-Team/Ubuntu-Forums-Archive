---
title: "Symbolic Link"
date: 2012-07-24
forum: General Help
---

### Post by vandorjw on 2012-07-24
Hey Everyone, 

I have a neat problem, something I haven't seen before.

I have made a symbolic link of a folder, and wish to remove this link.
This is the result.

> 
[****@BlackFedora Dropbox]$ rm Pictures/
rm: cannot remove `Pictures/': Is a directory

[****@BlackFedora Dropbox]$ rmdir Pictures/
rmdir: failed to remove `Pictures/': Not a directory

[****@BlackFedora Dropbox]$ rm Pictures/
rm: cannot remove `Pictures/': Is a directory


What is going on here?

Extra hints
> 
[vandorp@BlackFedora Dropbox]$ ls -l
total 256
lrwxrwxrwx 1 home-user home-user     23 Jun  6 17:31 Pictures -> /home/home-user/Pictures/


---

### Post by spjackson on 2012-07-24
```
rm Pictures
```Note, no trailing slash.

---

### Post by Cheesemill on 2012-07-24
My default rm doesn't delete directories, you have to use the -r switch.
```
rm -r Pictures
```

It doesn't make a difference whether you type the trailing slash or not.

---

### Post by spjackson on 2012-07-24
> **Cheesemill said:**
> My default rm doesn't delete directories, you have to use the -r switch.

@Cheesemill Perhaps I'm mistaken, but from the topic and 'ls -l' in the OP, I had understood that the intent was to remove a **link** to a directory, not to remove a directory. Apologies if I've misunderstood.

---

### Post by Cheesemill on 2012-07-24
> **spjackson said:**
> @Cheesemill Perhaps I'm mistaken, but from the topic and 'ls -l' in the OP, I had understood that the intent was to remove a **link** to a directory, not to remove a directory. Apologies if I've misunderstood.
Yep, you're right. I was getting it mixed up with something else. You just need:
```
rm Pictures
```

---

