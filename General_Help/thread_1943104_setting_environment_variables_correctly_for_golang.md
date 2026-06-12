---
title: "setting environment variables correctly for golang-go"
date: 2012-03-18
forum: General Help
---

### Post by acarchau on 2012-03-18
I installed the golang-go package. How do I set GOROOT? I am setting GOBIN to /usr/bin because that is where 6g is installed, but I can't figure out how to set GOROOT.

---

### Post by saphil on 2012-08-19
I was trying to walk through the Go Language site to get that information, and my path info (set as they suggest, did not show the Go language as being installed, but in the Universe repository there is a package called golang-go, so since I have all repositories turned on (un-commented) I just did
```
sudo aptitude install golang-go
```
and it took care of the path questions for me.  In March, when you asked, there was no stable Precise version available.  Now there is and I am not running any earlier version on a desktop to check it out.  So sorry I cannot tell you about availability on those versions.

I am looking at how easy it would be to get the Go-developers to add the note about Ubuntu to their main page or their documentation somewhere, so you don't have to go through all the annoyance of setting path and recompiling gcc.

Wolf

---

