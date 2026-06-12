---
title: "Problem with repositories"
date: 2010-11-25
forum: General Help
---

### Post by madmax.santana on 2010-11-25
Running:
```
sudo apt-get update
```
Gives:
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Using Ubuntu Maverick (10.10)... Working behind a proxy server. Freshly installed... Architecture is amd64

---

### Post by wojox on 2010-11-25
Run these three commands in the terminal

```
gpg –keyserver keyserver.ubuntu.com –recv 3E5C1192
gpg –export –armor 3E5C1192 | sudo apt-key add -
sudo apt-get update
```

---

### Post by tajiknomi on 2010-11-25
[SIZE=2]Go to repository and **uncheck **[/SIZE]

```
[http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  
```


[SIZE=2]and then try again[/SIZE]:p

---

### Post by john77eipe on 2010-11-25
I have a similar problem. Tried the commands you gave. But it's not working. :(

```

eipe@eipe-john:~$ gpg –keyserver keyserver.ubuntu.com –recv 3E5C1192
usage: gpg [options] [filename]
eipe@eipe-john:~$ gpg –export –armor 3E5C1192 | sudo apt-key add -
usage: gpg [options] [filename]
gpg: no valid OpenPGP data found.

```

---

### Post by plucky on 2010-11-25
> **john77eipe said:**
> I have a similar problem. Tried the commands you gave. But it's not working. :(

```

eipe@eipe-john:~$ gpg –keyserver keyserver.ubuntu.com –recv 3E5C1192
usage: gpg [options] [filename]
eipe@eipe-john:~$ gpg –export –armor 3E5C1192 | sudo apt-key add -
usage: gpg [options] [filename]
gpg: no valid OpenPGP data found.

```


The command is incorrect as it uses – instead of --

From the terminal ```
gpg --keyserver keyserver.ubuntu.com --recv 3E5C1192
gpg --export --armor 3E5C1192 | sudo apt-key add -
sudo apt-get update
```

Good Luck

@wojox Please fix you commands

---

### Post by john77eipe on 2010-11-25
```

$ gpg --keyserver keyserver.ubuntu.com --recv 3E5C1192
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
$ gpg --export --armor 3E5C1192 | sudo apt-key add -
OK

```

Still get the below response:
```


Fetched 317B in 2s (111B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  
W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by a2020vision on 2010-11-25
I'm having the same problem (including the fact that the work-around isn't working). I believe the problem might be here (in the error message):
```
NO_PUBKEY DB141E2302FDF932
```
Work-arounds I've seen so far have cited, in their error message, instead:
```
NO_PUBKEY 16126D3A3E5C1192
```

I'm not sure quite what this means, but if I figure it out I'll post it here.

---

### Post by a2020vision on 2010-11-25
I believe you will find the solution in this thread: [http://ubuntuforums.org/showthread.php?p=10159236]("http://ubuntuforums.org/showthread.php?p=10159236")
Specifically, this post:

> **philinux said:**
> Open a terminal and use copy and paste for the command below.

You needed to change the command to your key value.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932

```
This worked for me; hopefully it works for you as well!

---

### Post by plucky on 2010-11-25
a2020vision is correct,do the same commands but change the key from 3E5C1192
 to 02FDF932.

Good Luck

---

### Post by Autowrench on 2010-11-25
> **a2020vision said:**
> I believe you will find the solution in this thread: [http://ubuntuforums.org/showthread.php?p=10159236](http://ubuntuforums.org/showthread.php?p=10159236)
Specifically, this post:


This worked for me; hopefully it works for you as well!


Worked for me also. Thanks a bunch!

---

### Post by john77eipe on 2010-11-25
Thanks a ton guys!!! :D

---

### Post by madmax.santana on 2010-11-25
> **wojox said:**
> Run these three commands in the terminal

```
gpg –keyserver keyserver.ubuntu.com –recv 3E5C1192
gpg –export –armor 3E5C1192 | sudo apt-key add -
sudo apt-get update
```

> **plucky said:**
> The command is incorrect as it uses – instead of --

From the terminal ```
gpg --keyserver keyserver.ubuntu.com --recv 3E5C1192
gpg --export --armor 3E5C1192 | sudo apt-key add -
sudo apt-get update
```Good Luck

@wojox Please fix you commands


> **plucky said:**
> a2020vision is correct,do the same commands but change the key from 3E5C1192
 to 02FDF932.

Good Luck

Thanks a lot! It worked as the three posts above direct. Thanks wojox & plucky. :)

---

### Post by dO_om on 2010-11-26
Thanks a lot, thanks a lot... None of you even asked "why?" "who to hang?". Ubuntu way?

---

### Post by madmax.santana on 2010-11-27
> **dO_om said:**
> Thanks a lot, thanks a lot... None of you even asked "why?" "who to hang?". Ubuntu way?
Strangely, YOU ARE ABSOLUTELY RIGHT !!!

Hey thanks for pointing out... This thread IS NOT solved yet... Someone mind telling me what the heck did I just do to my system??? :p

EDIT: Actually, I have an idea what might be happening here... I guess all repositories are registered with Ubuntu and to make their registration authentic, Ubuntu assigns each repository a unique digital key. Only once we have downloaded and installed the specific key from the Ubuntu key server, we can connect to and download software from the repository using the aptitude software manager... That's all I think I know... Is that right?

---

### Post by plucky on 2010-11-27
> **madmax.santana said:**
> Strangely, YOU ARE ABSOLUTELY RIGHT !!!

Hey thanks for pointing out... This thread IS NOT solved yet... Someone mind telling me what the heck did I just do to my system??? :p

EDIT: Actually, I have an idea what might be happening here... I guess all repositories are registered with Ubuntu and to make their registration authentic, Ubuntu assigns each repository a unique digital key. Only once we have downloaded and installed the specific key from the Ubuntu key server, we can connect to and download software from the repository using the aptitude software manager... That's all I think I know... Is that right?

See [Link](https://help.ubuntu.com/community/SecureApt)

Good Luck

---

### Post by madmax.santana on 2010-12-01
Thanks... :)
*Now* it is solved...

---

