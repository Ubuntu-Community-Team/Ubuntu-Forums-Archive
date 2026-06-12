---
title: "&quot;Failed to download package files. Check your internet connection.&quot; -- Software Cente"
date: 2012-03-02
forum: General Help
---

### Post by wasilcopter on 2012-03-02
I get this message any time I try to install anything from the software center. I know that my internet connection is fine and that it isn't a particular network, as I've tried to download on several protected and unprotected networks. I have run

sudo get-apt update

as I was told to do in a few other threads but it hasn't worked for me as it seems to have for other people. 

any help would be appreciated! thanks errbuddy.

Edit:

When I run the update command I mentioned above, at the end I get

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by josephmills on 2012-03-02
hello there could you open your terminal and enter in 
```
 cat /etc/apt/sources.list

```
then 
```
ls /etc/apt/sources.list.d/
 
```

then paste that here please 
thanks

---

### Post by cortman on 2012-03-02
It appears you have GPG errors. There are instructions [here]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/") for fixing that.

---

