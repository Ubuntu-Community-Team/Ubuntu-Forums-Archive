---
title: "gpg error when using synaptic"
date: 2012-08-28
forum: General Help
---

### Post by boregard on 2012-08-28
W:hi all, i keep getting errors when trying to update with synaptic .  anybody got any ideas on how on how to resolve this? any help will be  greatly appreciated, thanks ```
GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

---

### Post by wojox on 2012-08-28
Copy and paste this command in the terminal:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5 16126D3A3E5C1192
```

---

### Post by boregard on 2012-08-28
> **wojox said:**
> Copy and paste this command in the terminal:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5 16126D3A3E5C1192
```thanks for fast reply, i copied & pasted the cmd. in terminal and still get same error.

---

### Post by wojox on 2012-08-28
These should clean up badsigs:
```
sudo apt-get clean 
cd /var/lib/apt 
sudo mv lists lists.old 
sudo mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update
```

The other command was for no_pub_key.

---

### Post by boregard on 2012-08-28
> **wojox said:**
> These should clean up badsigs:
```
sudo apt-get clean 
cd /var/lib/apt 
sudo mv lists lists.old 
sudo mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update
```The other command was for no_pub_key.
thanks for your help wojox, that fixed it. have a good one!:p

---

