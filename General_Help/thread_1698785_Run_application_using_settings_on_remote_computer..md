---
title: "Run application using settings on remote computer."
date: 2011-03-02
forum: General Help
---

### Post by FooAtari on 2011-03-02
I want to run a local application, in this case Pan, but have it use the settings folder for Pan installed on a remote PC.  I'm pretty sure this is possible, but not sure how to go about setting it up.

---

### Post by sanderd17 on 2011-03-02
> **FooAtari said:**
> I want to run a local application, in this case Pan, but have it use the settings folder for Pan installed on a remote PC.  I'm pretty sure this is possible, but not sure how to go about setting it up.

I assume you already have your remote computer mounted somewhere in your own computer.

then you can just create a symlink to the settings folder on the remote computer and give the symlink the same name as the setings folder on your computer.

type
```

ln --help 

```
for more info on how to do it



You should watch out for the permissions.

---

### Post by FooAtari on 2011-03-02
Thanks :-)

---

