---
title: "Error when running sudo-apt get update."
date: 2010-10-17
forum: General Help
---

### Post by Jetso on 2010-10-17
When I go to terminal and run ```
sudo apt-get update
```
It runs for a while, then at the end it gives me a error message that says: ```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```
Now what am I supposed to do to fix this problem?

---

### Post by ivarn on 2010-10-17
Funny, I just asked the same question and still waiting for an answer lol.
But since more people are dealing with this issue I assume igetdeb.net are having troubles with their servers.
Are there any alternative servers out there, plz post them here :)

---

### Post by Jetso on 2010-10-17
Oh, that could be the problem. I everyone running maverick is having problems. -_-

---

### Post by Toz on 2010-10-17
Have a look at:

[http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html](http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html)

---

### Post by Hippytaff on 2010-10-17
Theres nothing to upgrade in maverick at the moment...odd why this error appears though, I just get

```

Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Jetso on 2010-10-17
Oh, well then haha. I guess I'll just mark this as solved, and if it doesn't work when there *is[I]*[/I]something to update, I'll complain. ;)

---

### Post by 23dornot23d on 2010-10-17
Here is the Answer .... there are a few like this ..... [LINK]("http://www.webupd8.org/2010/10/fix-nopubkey-error-for-extras-ubuntu.html")

Search Google on ..... NO_PUBKEY 16126D3A3E5C1192

---

### Post by Jetso on 2010-10-17
That worked! I just followed the instructions in the link, and it didn't give me an error, so I assume it worked.

---

