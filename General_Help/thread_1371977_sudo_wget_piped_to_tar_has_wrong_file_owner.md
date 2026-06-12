---
title: "sudo wget piped to tar has wrong file owner"
date: 2010-01-04
forum: General Help
---

### Post by ninegill on 2010-01-04
Greetings,

I'm trying to download a file and extract it in one line, but the extracted file is owned by me instead of root even though I'm using sudo:

```
sudo sh -c 'wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz -O- | tar -xzf -'
```

If I don't try to extract the file, it is owned by root as I expected:

```
sudo sh -c 'wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz'
```

Any ideas on why this happens and how to work around it?

Thanks!

---

### Post by kjohri on 2010-01-04
Apparently, you can execute a single command as superuser with sudo and not a pipeline. For example, if there is a bash script which creates a file and you run the script with sudo, the created file will still have your user and group ids. If required, you can make root the owner of file as,

```
sudo chown root *filename*
```

---

