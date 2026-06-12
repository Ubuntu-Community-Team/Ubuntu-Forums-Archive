---
title: "404 errors on update"
date: 2012-01-14
forum: General Help
---

### Post by ryadav on 2012-01-14
Hello I seem to be getting a lot of 404 error when I do a, 'sudo apt-get update' ?

I am using Kubuntu x64 11.04

Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 2,293 B in 2s (842 B/s)
W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


How do I fix or update my list?

Thanks

---

### Post by bluexrider on 2012-01-14
Try changing the server mirror first:

Go to > software sources > the first tab where it says 'Download From' click the dropdown and chang it to "other" then choose best server. Let it update it may take a couple of minutes then choose and you will get a reload panel. Let it update. 

Then in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ryadav on 2012-01-14
thanks i did some clean up, where can i get a list of the new package sources?

have things changed for ubuntu/kubunut with the recent new release of 11.10?

where can i get the latest source for 3rd party like: java, flash

---

### Post by bluexrider on 2012-01-14
I guess for you now it would be

```
ksudo apt-get install sun-java6-jdk
```

you should be able to use Muon to find the required packages.

---

### Post by ryadav on 2012-01-14
thanks, what i was asking about is the package sources, the list of the server urls, have any changed, old one deleted or new one added?

i would like to know where i can find the latest server list

if you look at my original post you can tell that the following package source doesn't exist:

W: Failed to fetch [http://ppa.launchpad.net/sun-java-co...source/Sources]("http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources")  404  Not Found

i just need to know where to find the latest source list

---

### Post by bluexrider on 2012-01-14
[http://www.kubuntuguide.info/index.php/Natty](http://www.kubuntuguide.info/index.php/Natty)


Try this

---

### Post by ryadav on 2012-01-14
that link is awesome, packed full of details, thanks!

---

### Post by bluexrider on 2012-01-15
glad to be of help, please mark this 

(SOLVED)

---

