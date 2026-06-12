---
title: "bad signature, not authenticated"
date: 2012-02-14
forum: General Help
---

### Post by techvish81 on 2012-02-14
i installed xubuntu on a machine and now i'm trying to update it, it shows over 200mb to be downloaded and when i click on ok , it gives an error and says bad signature.

any help would be highly appreciated!!!

---

### Post by Toz on 2012-02-14
Open a terminal window, type in the following command and post back the results:
```
sudo apt-get update
```

---

### Post by techvish81 on 2012-02-15
the result of apt-get update.


```
Fetched 368 kB in 5s (65.6 kB/s)
Reading package lists... Done
W: GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://in.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://in.archive.ubuntu.com oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

---

### Post by techvish81 on 2012-02-15
actually i updated using synaptic but it also prints "NOT AUTHENTICATED" above all the downloads. still it allows me to update. so i updated , but how to remove this "not authenticated" thing!!

---

### Post by Toz on 2012-02-15
> **techvish81 said:**
> but how to remove this "not authenticated" thing!!

Try the following commands in a terminal window:
```

sudo apt-get clean 
cd /var/lib/apt 
sudo mv lists lists.old 
sudo mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update

```

---

### Post by techvish81 on 2012-02-17
> **Toz said:**
> Try the following commands in a terminal window:
```

sudo apt-get clean 
cd /var/lib/apt 
sudo mv lists lists.old 
sudo mkdir -p lists/partial 
sudo apt-get clean 
sudo apt-get update

```

thank you!! it solved the problem.

---

