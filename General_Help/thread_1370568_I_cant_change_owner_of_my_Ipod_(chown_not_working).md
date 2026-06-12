---
title: "I cant change owner of my Ipod (chown not working)..."
date: 2010-01-02
forum: General Help
---

### Post by switch10 on 2010-01-02
so i just did a restore on my ipod using Virtualbox and windows.  When i try to add songs to the ipod in rhythmbox I get an error saying I don't have permission.  So I did this:
```
sudo chown dave:dave /media/DAVE\'S\ IPOD/
```

and I get this back:
```
chown: changing ownership of `/media/DAVE\'S IPOD/': Operation not permitted
```

Whats going on here?

Dave

---

### Post by switch10 on 2010-01-02
Ha!  never mind.  I got it working.  I had to pick the language on the Ipod..

---

