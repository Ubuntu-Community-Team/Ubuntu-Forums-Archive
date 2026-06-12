---
title: "Could not download all repository indexes. [9.10]"
date: 2010-01-23
forum: General Help
---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2010-01-23
I upgraded a few months back (network upgrade)
And ever since I couldn't update or i could but it would just give me errors.

> Failed to fetch [http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/dists/karmic/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.

I've changed servers many times, and also chose "best server' with no luck.. what is the archive for? is it still important, and is it possible to remove?

Thank you in advance.

---

### Post by stoneage on 2010-01-23
It looks like you have the wrong addresses. It should be:-
> [http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz)

You could edit your software sources or sources.list. I don't know if you would need to update the keyring. Try it and see.....

---

