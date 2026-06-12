---
title: "Dell vostro 1000"
date: 2012-03-03
forum: General Help
---

### Post by makre007 on 2012-03-03
I just installed ubuntu 11.10 on my Dell Vostro 1000 and i did the installing without internet and thats why i think i dont have any drivers and i dont know how to fix this i went to additional drivers and i get " Downloading package indexes failed, please check your network status.Most drivers wont be available" and i cant connect my internet also. Can someone please help me with this.

---

### Post by raja.genupula on 2012-03-03
please open your terminal and type

```
sudo apt-get update 
```

and paste the output here and place it between code tags .

---

### Post by makre007 on 2012-03-03
Err [http://mk.archive.ubuntu.com](http://mk.archive.ubuntu.com) oneiric InRelease 
   
Err [http://mk.archive.ubuntu.com](http://mk.archive.ubuntu.com) oneiric-updates InRelease 
   
Err [http://mk.archive.ubuntu.com](http://mk.archive.ubuntu.com) oneiric-backports InRelease 
   
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease 
   
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg 
  Could not resolve 'security.ubuntu.com' 
Err [http://mk.archive.ubuntu.com](http://mk.archive.ubuntu.com) oneiric Release.gpg 
  Could not resolve 'mk.archive.ubuntu.com' 
Err [http://mk.archive.ubuntu.com](http://mk.archive.ubuntu.com) oneiric-updates Release.gpg 
  Could not resolve 'mk.archive.ubuntu.com' 
Err [http://mk.archive.ubuntu.com](http://mk.archive.ubuntu.com) oneiric-backports Release.gpg 
  Could not resolve 'mk.archive.ubuntu.com' 
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease 
   
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg 
  Could not resolve 'extras.ubuntu.com' 
Reading package lists... Done 
W: Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://mk.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease)   

W: Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease](http://mk.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease)   

W: Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease](http://mk.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease)   

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease](http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease)   

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease](http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease)   

W: Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://mk.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'mk.archive.ubuntu.com' 

W: Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg](http://mk.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg)  Could not resolve 'mk.archive.ubuntu.com' 

W: Failed to fetch [http://mk.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg](http://mk.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg)  Could not resolve 'mk.archive.ubuntu.com' 

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg)  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg)  Could not resolve 'extras.ubuntu.com' 

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by makre007 on 2012-03-03
this is what i get

---

### Post by makre007 on 2012-03-03
> **raja.genupula said:**
> please open your terminal and type

```
sudo apt-get update 
```

and paste the output here and place it between code tags .
```
Err http://mk.archive.ubuntu.com oneiric InRelease 
   
Err http://mk.archive.ubuntu.com oneiric-updates InRelease 
   
Err http://mk.archive.ubuntu.com oneiric-backports InRelease 
   
Err http://security.ubuntu.com oneiric-security InRelease 
   
Err http://security.ubuntu.com oneiric-security Release.gpg 
  Could not resolve 'security.ubuntu.com' 
Err http://mk.archive.ubuntu.com oneiric Release.gpg 
  Could not resolve 'mk.archive.ubuntu.com' 
Err http://mk.archive.ubuntu.com oneiric-updates Release.gpg 
  Could not resolve 'mk.archive.ubuntu.com' 
Err http://mk.archive.ubuntu.com oneiric-backports Release.gpg 
  Could not resolve 'mk.archive.ubuntu.com' 
Err http://extras.ubuntu.com oneiric InRelease 
   
Err http://extras.ubuntu.com oneiric Release.gpg 
  Could not resolve 'extras.ubuntu.com' 
Reading package lists... Done 
W: Failed to fetch http://mk.archive.ubuntu.com/ubuntu/dists/oneiric/InRelease   

W: Failed to fetch http://mk.archive.ubuntu.com/ubuntu/dists/oneiric-updates/InRelease   

W: Failed to fetch http://mk.archive.ubuntu.com/ubuntu/dists/oneiric-backports/InRelease   

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease   

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/InRelease   

W: Failed to fetch http://mk.archive.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Could not resolve 'mk.archive.ubuntu.com' 

W: Failed to fetch http://mk.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release.gpg  Could not resolve 'mk.archive.ubuntu.com' 

W: Failed to fetch http://mk.archive.ubuntu.com/ubuntu/dists/oneiric-backports/Release.gpg  Could not resolve 'mk.archive.ubuntu.com' 

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg  Could not resolve 'security.ubuntu.com' 

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release.gpg  Could not resolve 'extras.ubuntu.com' 

W: Some index files failed to download. They have been ignored, or old ones used instead. 
```

---

### Post by raja.genupula on 2012-03-03
[http://www.turnkeylinux.org/forum/support/20090724/fix-apt-get-could-not-resolve-archiveubuntucom](http://www.turnkeylinux.org/forum/support/20090724/fix-apt-get-could-not-resolve-archiveubuntucom)

EDIT:hey small suggestion , please dont post same thing two times , if you did any mistake in older post , you can edit that .

---

