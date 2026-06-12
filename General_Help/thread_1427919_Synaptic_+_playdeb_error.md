---
title: "Synaptic + playdeb error"
date: 2010-03-12
forum: General Help
---

### Post by Alseimik on 2010-03-12
Hi, often when i try to install i get this error:

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) jaunty Release: The following signatures were invalid: Badsig 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Could not get [http://dk.archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://dk.archive.ubuntu.com/ubuntu/dists/jaunty/Release)

W: Some index files could not be retrieved, they were ignored or the old ones used instead.

What does this mean, and what should i do?

---

### Post by zvacet on 2010-03-12
```
sudo apt-get update
```

If that doesn't work under system>sdmin>software sources change server to main.

---

### Post by Alseimik on 2010-03-14
> If that doesn't work under system>sdmin>software sources change server to main.

And what does that mean? 

And no, the update gave the exact same error.

---

### Post by zvacet on 2010-03-14
Type in terminal

```
cat /etc/apt/sources.list
```

and post it here.

---

