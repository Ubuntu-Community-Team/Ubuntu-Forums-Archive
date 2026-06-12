---
title: "update to Thunderbird 10"
date: 2012-02-11
forum: General Help
---

### Post by Captain Apollo on 2012-02-11
How do I upgrade to Thunderbird 10? I am still at version 9 and no update is available when I run software update.

---

### Post by wolfen69 on 2012-02-11
Open a terminal and copy and paste the following:

```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
```
then
```
sudo apt-get update
```
then
```
sudo apt-get upgrade thunderbird
```

---

### Post by jamesisin on 2012-02-12
I wrote this article on the subject:

[http://jamesisin.com/a_high-tech_blech/index.php/2011/07/keep-stable-thunderbird-current-on-64bit-ubuntu/](http://jamesisin.com/a_high-tech_blech/index.php/2011/07/keep-stable-thunderbird-current-on-64bit-ubuntu/)

It's essentially the same process wolfen69 offers but there is explanation and maybe a joke as well.  (I wrote it about 64 bit but it will work the same for 32 bit systems.)

---

### Post by Captain Apollo on 2012-02-12
> **wolfen69 said:**
> Open a terminal and copy and paste the following:

```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
```
then
```
sudo apt-get update
```
then
```
sudo apt-get upgrade thunderbird
```
Thanks.

Just curious though. How come software up to date doesn't do this automatically?

---

### Post by Frogs Hair on 2012-02-12
Firefox will now update via the update manager on newer versions of Ubuntu . I have proposed updates enabled , so I received Tbird 10 update as a proposed update right after release . I would expect Tbird 10 will come via recommended updates soon .

---

### Post by jamesisin on 2012-02-12
Ubuntu doesn't necessarily provide all updates to various pieces of software.  Presumably this is to prevent untested conflicts from arising, but that's just my guess.  You will occasionally find that you would like to keep some piece of software more up to date than Canonical in which case you will want to seek out a repository (best option as is the case with Thunderbird here) or locate the new version and install it manually.  (For most users this would likely never be an issue as they would likely be content using whatever version Canonical hands down to the Ubuntu update stream.)

---

