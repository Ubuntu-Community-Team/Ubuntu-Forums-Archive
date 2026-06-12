---
title: "Apt authentification issue with GPG and CRAN"
date: 2011-02-24
forum: General Help
---

### Post by valugi on 2011-02-24
Starting a couple of days ago I get this on startup. CRAN repository was working well so far. Should I change anything?

```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://cran.uib.no](http://cran.uib.no) lucid/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 51716619E084DAB9

W: GPG error: [http://cran.uib.no](http://cran.uib.no) lenny-cran/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 06F90DE5381BA480
W: Failed to fetch [http://cran.uib.no/bin/linux/ubuntu/lucid/Release](http://cran.uib.no/bin/linux/ubuntu/lucid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by miguelastico on 2011-02-24
It's happening to me as well

---

### Post by fsando on 2011-02-26
So any solution? This has been happening for more than a week

---

### Post by Old_Grey_Wolf on 2011-02-26
Enter these commands in a terminal. Then try to update again,
```
gpg --keyserver keyserver.ubuntu.com --recv 06F90DE5381BA480
gpg --export --armor 06F90DE5381BA480  | sudo apt-key add -
```

---

### Post by valugi on 2011-02-28
This did not work, I still get an error on apt-get update.

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://cran.uib.no lucid/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 51716619E084DAB9

```

I find the new key in the $ gpg --list-key but not the 517... to delete it. 

> **Old_Gray_Wolf said:**
> Enter these commands in a terminal. Then try to update again,
```
gpg --keyserver keyserver.ubuntu.com --recv 06F90DE5381BA480
gpg --export --armor 06F90DE5381BA480  | sudo apt-key add -
```

---

### Post by valugi on 2011-02-28
It did work thought with this key:


```

 gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
 gpg -a --export E084DAB9 | sudo apt-key add -
```

---

### Post by Old_Grey_Wolf on 2011-02-28
> **valugi said:**
> It did work thought with this key:


```

 gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
 gpg -a --export E084DAB9 | sudo apt-key add -
```

Now that you figured out that you need to substitute the key in the error message for the key in the two command I provided, you can help the dozen or so people posting every week that have the same problem.:)

It could be your way of contributing to the FOSS community.

---

