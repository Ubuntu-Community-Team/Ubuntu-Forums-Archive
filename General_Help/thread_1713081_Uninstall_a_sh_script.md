---
title: "Uninstall a sh script"
date: 2011-03-23
forum: General Help
---

### Post by UnknownDiety on 2011-03-23
Hello all.

I installed a sh script earlier (Thought it was an what I needed, but it wasn't)

the contents of the sh script is

```
#!/bin/sh

cp libsfmpq.so.1.0.7.4 /lib/
cp libsfmpq.so.1.0.7.4 /usr/lib/

cd /lib
ln -sf libsfmpq.so.1.0.7.4 libsfmpq.so.1

cd /usr/lib
ln -sf libsfmpq.so.1.0.7.4 libsfmpq.so.1.0.7
ln -sf libsfmpq.so.1.0.7 libsfmpq.so.1.0
ln -sf libsfmpq.so.1.0 libsfmpq.so.1
ln -sf libsfmpq.so.1 libsfmpq.so
```

---

### Post by WorMzy on 2011-03-23
I can find no references to any of those files in any of the packages in the repos, so you'll probably be fine just deleting them.

```
sudo rm /lib/libsfmpq.so.1.0.7.4 /lib/libsfmpq.so.1 /usr/lib/libsfmpq.so.1.0.7.4 /usr/lib/libsfmpq.so.1.0.7 /usr/lib/libsfmpq.so.1.0 /usr/lib/libsfmpq.so.1 /usr/lib/libsfmpq.so
```

I'd wait for a second opinion though.

---

