---
title: "updates failing"
date: 2012-06-03
forum: General Help
---

### Post by rjackson1969 on 2012-06-03
I have 101 updates and my updates fail. I've had successful updates since 12.04 release. I installed it on day 1 of the release. This is the response I get when I try:
[INDENT]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_5.2.2.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_5.2.2.1_all.deb) 404  Not Found [IP: 91.189.91.24 80]


[/INDENT]This just started happening today. Any help in fixing this would be appreciated.

Thanks all!

---

### Post by drs305 on 2012-06-03
The problem is that your system is trying to fetch a software-center version which no longer is in the repository ...2.2.1  It's been updated to 2.2.2

Try running the first command to clear the list of available packages, then update/upgrade:
```
sudo dpkg --clear-avail
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by rjackson1969 on 2012-06-04
> **drs305 said:**
> The problem is that your system is trying to fetch a software-center version which no longer is in the repository ...2.2.1  It's been updated to 2.2.2

Try running the first command to clear the list of available packages, then update/upgrade:
```
sudo dpkg --clear-avail
sudo apt-get update
sudo apt-get upgrade
```


Ok...

Just did this and now my system says there are no new updates. Prior to doing this it said I had 101 updates to do. So I'm assuming the "sudo apt-get update" updated everything after the "sudo dpkg --clear-avail" reset me to the correct url?


btw... Thanks a bunch for all the help!

---

### Post by drs305 on 2012-06-04
> **rjackson1969 said:**
> Ok...

Just did this and now my system says there are no new updates. Prior to doing this it said I had 101 updates to do. So I'm assuming the "sudo apt-get update" updated everything after the "sudo dpkg --clear-avail" reset me to the correct url?


It was actually an update to the list of one of the available packages. It couldn't retrieve the one of the packages because it had already been replaced in the repository with a newer version.

When you now run "sudo apt-get update" you should see a message such as:
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
As long as they are all 0's and none are reported as being 'kept back' your system should be up-to-date.

If you don't have any other questions you can mark the thread SOLVED via the Thread Tools link near the top right of the first post (it's also reversible should something come up).

Happy Ubuntu-ing !

---

### Post by rjackson1969 on 2012-06-05
> **drs305 said:**
> It was actually an update to the list of one of the available packages. It couldn't retrieve the one of the packages because it had already been replaced in the repository with a newer version.

When you now run "sudo apt-get update" you should see a message such as:
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```As long as they are all 0's and none are reported as being 'kept back' your system should be up-to-date.

If you don't have any other questions you can mark the thread SOLVED via the Thread Tools link near the top right of the first post (it's also reversible should something come up).

Happy Ubuntu-ing !

Done and done. Thanks again. My ubuntu-ing has been happy for many years now due to being an awesome OS and the fact that info and help abound in people like you who make living the ubuntu life so easy.

---

