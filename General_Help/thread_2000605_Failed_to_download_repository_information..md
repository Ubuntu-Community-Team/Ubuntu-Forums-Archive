---
title: "Failed to download repository information."
date: 2012-06-09
forum: General Help
---

### Post by AndrewC312 on 2012-06-09
Hello, I'm sorry if this issue has been posted before but I looked through a couple of similar threads and i wasn't sure if it was exactly the same issue, but I couldn't get my problem fixed. I am not very knowledgeable about these things. 

Anyway, some time after I upgraded to 12.04, my software updates stopped working. I keep getting this same error: 

Failed to download repository information

Check your internet connection.


This is shown in the details:

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.


I have now unchecked every source but the main one and I am using the United States server. I don't know whats going on here :( I would really appreciate some help!

---

### Post by plucky on 2012-06-10
> **AndrewC312 said:**
> Hello, I'm sorry if this issue has been posted before but I looked through a couple of similar threads and i wasn't sure if it was exactly the same issue, but I couldn't get my problem fixed. I am not very knowledgeable about these things. 

Anyway, some time after I upgraded to 12.04, my software updates stopped working. I keep getting this same error: 

Failed to download repository information

Check your internet connection.


This is shown in the details:

W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release)  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-security/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-security/Release)  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)
, E:Some index files failed to download. They have been ignored, or old ones used instead.


I have now unchecked every source but the main one and I am using the United States server. I don't know whats going on here :( I would really appreciate some help!


Post the output from a terminal for```
cat /etc/apt/sources.list
```

For some reason the upgrade has added "independent" to the repositories for your sources.list. If you remove the word independent from your sources.list you should be able to update your system

See [Thread](http://ubuntuforums.org/showthread.php?t=1989088)

Good Luck

---

### Post by AndrewC312 on 2012-06-10
I believe this solved the problem. Thank you very much! Interesting though..how did those "independents" get in there anyway?

---

