---
title: "Can't find InRelease in security.ubuntu.com"
date: 2012-05-30
forum: General Help
---

### Post by supremedalek on 2012-05-30
So I have a machine running oneric/11.10 and I was going to do a routine update. During the process to check for updates, I got the following message:

```
Err http://security.ubuntu.com oneiric-security InRelease
  
Err http://security.ubuntu.com oneiric-security Release.gpg
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Reading package lists... Done
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release.gpg  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

which makes sense since I do not see that file in [http://security.ubuntu.com/ubuntu/dists/oneiric-security/](http://security.ubuntu.com/ubuntu/dists/oneiric-security/). Was that file in there before? Should I care?

---

### Post by raja.genupula on 2012-05-30
have you gone through **update manager > settings > download from : choosing a best server** and try again ?

---

### Post by supremedalek on 2012-05-30
How to do that through the command line? Machine in question has no gui.

---

### Post by Frogs Hair on 2012-05-30
Looks like a fail to connect problem which is usually temporary. I would try again later . You can also try from the terminal with the following. ```
sudo apt-get update
``````
sudo apt-get upgrade
```

---

### Post by raja.genupula on 2012-05-30
> **Frogs Hair said:**
> Looks like a fail to connect problem which is usually temporary. I would try again later . You can also try from the terminal with the following. ```
sudo apt-get update
``````
sudo apt-get upgrade
```

+1 Here , try again after some time , if even still error is there we can go with change server

---

