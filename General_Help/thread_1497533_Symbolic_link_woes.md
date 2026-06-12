---
title: "Symbolic link woes"
date: 2010-05-30
forum: General Help
---

### Post by AbtZ on 2010-05-30
OK I tried to create a symbolic link thusly:
```
sudo ln -s test /usr/local/bin/
```
This should create a link in /usr/local/bin to the file "test" in the current directory, right?

Well, when I got to /usr/local/bin here's the link that was created:
```
$ ls -al | grep test
lrwxrwxrwx  1 root root    4 2010-05-30 23:30 test -> test
```

It seems it creates a symbolic link in that directory that is linking to itself, which is totally useless. Am I totally misunderstanding the syntax, or what?

---

### Post by squaregoldfish on 2010-05-30
ln -s will create a link to the exact path you give it in the specified destination - it doesn't try to add the full path structure to the current directory, which is why you got the result you did.

What you need to do is create a symbolic link to the full path:

```
sudo ln -s /other/dir/test /usr/local/bin/
```

I usually find it easier to change to the destination directory to create symbolic links - it makes more intuitive sense:

```
cd /usr/local/bin
sudo ln -s /other/dir/test .
```

Steve.

---

### Post by AbtZ on 2010-05-31
Ah, I see. I was assuming it worked like cp or mv, my bad. Thanks!

---

### Post by ibuclaw on 2010-05-31
> **AbtZ said:**
> OK I tried to create a symbolic link thusly:
```
sudo ln -s test /usr/local/bin/
```
This should create a link in /usr/local/bin to the file "test" in the current directory, right?

Well, when I got to /usr/local/bin here's the link that was created:
```
$ ls -al | grep test
lrwxrwxrwx  1 root root    4 2010-05-30 23:30 test -> test
```

It seems it creates a symbolic link in that directory that is linking to itself, which is totally useless. Am I totally misunderstanding the syntax, or what?
The syntax for ln is:
```
ln -s DEST NAME
```
You need to be very specific in the DEST parameter as to where the link is, so ideally use the full path every time.

ergo, your original example should have been
```
ln -s `pwd`/test /usr/local/bin
```

Keep that for reference in the future.

Regards

---

