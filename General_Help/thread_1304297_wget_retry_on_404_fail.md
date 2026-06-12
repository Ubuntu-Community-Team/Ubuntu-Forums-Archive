---
title: "wget retry on 404 fail"
date: 2009-10-29
forum: General Help
---

### Post by blazemore on 2009-10-29
Is there a way to get wget to retry on a 404 error?

---

### Post by blazemore on 2009-10-29
Or is there a way to do this:
I want to download  [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent) to a specific folder that is watched by my torrent server.

Is there any way to do this?

---

### Post by blazemore on 2009-10-29
Hacked it with this
```
#/bin/bash
while true; do
        if [ -e "ubuntu-9.10-desktop-amd64.iso.torrent" ]
        then
                exit
        fi
wget http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent 
done

```

---

