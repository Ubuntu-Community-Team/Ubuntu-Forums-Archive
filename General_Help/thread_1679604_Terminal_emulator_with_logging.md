---
title: "Terminal emulator with logging"
date: 2011-02-01
forum: General Help
---

### Post by Fran2298 on 2011-02-01
I am looking for a terminal emulator that can log output to a file, preferably one where the log file can be easily selected and logging can be turned on/off. I need it to use as a simpler way to transfer text files from a remote server I log in to via ssh, as file transfer is very tedious in this case.

---

### Post by tredegar on 2011-02-01
Please see **man script**

But if you can **ssh** why don't you just **scp** the file?

---

### Post by Fran2298 on 2011-02-01
I can, but I connect to that server through three other servers (don't ask), so I would have to sftp it three times to get it locally.

---

### Post by Habitual on 2011-02-01
> **Fran2298 said:**
> I am looking for a terminal emulator that can log output to a file, preferably one where the log file can be easily selected and logging can be turned on/off. I need it to use as a simpler way to transfer text files from a remote server I log in to via ssh, as file transfer is very tedious in this case.

```
ssh -t user@domain.com 'cat /path/to/file' > file.out
```

will copy the remote /path/to/file to a local copy named file.out
It doesn't get any "easier" than that. :)

HTH.

---

### Post by Fran2298 on 2011-02-02
You don't understand, I'm going through three servers, my 'local' is three ssh's away

---

### Post by Habitual on 2011-02-02
putty logs.

```
sudo apt-get install -y putty
```

---

### Post by Fran2298 on 2011-02-04
Thank you, that's exactly what I was looking for :)

---

