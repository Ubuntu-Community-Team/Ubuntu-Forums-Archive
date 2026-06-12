---
title: "Keyring"
date: 2009-11-12
forum: General Help
---

### Post by kouakou on 2009-11-12
I am running into a weird problem: I cannot access my keyring ( I don't know what the pw is) so I try to delete it: Problem is there is nothing to delete. The default keyring file DOES NOT exist. I am at a loss as to where to go from here since I am still unable to log into several apps because of that....
Help please ????

---

### Post by delcypher on 2009-11-12
What locations have you tried for the gnome keyring?

Mine is in
```
~/.gnome2/keyrings/
```

Be aware that the .gnome2 directory is hidden because its first character is a dot and it won't be visible in nautilus unless you tell it to show hidden folders.

It might be worth checking the permissions on the keyrings folder too to make sure your user is the owner and the you have read and write access.

If the directory is truly empty then I'm not sure if I can help you.

---

### Post by kouakou on 2009-11-12
I did a ctrl h to show all hidden files ....I still cannot find it in ~/.gnome2/keyrings/

---

