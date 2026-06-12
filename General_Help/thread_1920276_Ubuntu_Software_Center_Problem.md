---
title: "Ubuntu Software Center Problem"
date: 2012-02-04
forum: General Help
---

### Post by aeonsv on 2012-02-04
Hallo
After update on Ubuntu, i can't download from Ubuntu Software Center.
When i click "Install" i reserve error - " Filed to Download package files - Check your internet connection "
but i have internet.

Sorry for my bad english but i come from Bulgaria

---

### Post by raja.genupula on 2012-02-04
Hi open your terminal and type

```
sudo apt-get update
```

paste the output here and place it on CODE tags by click at # in this window .

All the best.

---

### Post by aeonsv on 2012-02-04
> &#1048;&#1079;&#1090;&#1077;&#1075;&#1083;&#1077;&#1085;&#1080; 591 kB &#1079;&#1072; 2s (244 kB/&#1089;&#1077;&#1082;)                    
Reading package lists... Done
W: GPG error: [http://bg.archive.ubuntu.com]("http://bg.archive.ubuntu.com/") oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://bg.archive.ubuntu.com]("http://bg.archive.ubuntu.com/") oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com]("http://extras.ubuntu.com/") oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.canonical.com]("http://archive.canonical.com/") oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://bg.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release](http://bg.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

This ?

---

### Post by westie457 on 2012-02-04
Take a look at this. [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

It is a couple of years old but it might work for you.

---

### Post by aeonsv on 2012-02-04
Dosn't work ! :(

---

### Post by raja.genupula on 2012-02-04
```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update
```
what it gives , please paste the output of terminal .

---

### Post by aeonsv on 2012-02-04
> **raja.genupula said:**
> ```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update
```what it gives , please paste the output of terminal .

Now it's work :)

Thank you for the helping 

[COLOR=Red]UBUNTU - THE BEST[/COLOR]

---

### Post by raja.genupula on 2012-02-04
hi man , you'e welcome . please mark your thread as solved and remember this for every time , marking as solved after solving your issue .

Thank you very much.

cheers

raja

---

