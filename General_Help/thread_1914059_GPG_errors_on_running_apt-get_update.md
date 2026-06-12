---
title: "GPG errors on running apt-get update"
date: 2012-01-23
forum: General Help
---

### Post by yanom on 2012-01-23
I'm unable to use the ```
sudo apt-get update
``` command, because i get these errors:
```
 

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric-security/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```
I saw some howtos on deleting those keys and getting new ones but that didnt work.

---

### Post by bluexrider on 2012-01-23
This is what I would do with a badsig.

```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

---

### Post by yanom on 2012-01-23
> **bluexrider said:**
> This is what I would do with a badsig.

```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

that didn't work for me. What else should I try?

---

### Post by xyzzyman on 2012-01-23
That happened to me this morning. Just waited until my mirror was fixed.

---

### Post by bluexrider on 2012-01-23
You could change servers to get the updates. Use Software Sources to do that.

---

