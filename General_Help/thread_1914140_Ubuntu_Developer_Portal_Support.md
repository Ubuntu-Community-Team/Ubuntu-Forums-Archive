---
title: "Ubuntu Developer Portal Support?"
date: 2012-01-23
forum: General Help
---

### Post by interfect on 2012-01-23
I submitted a commercial application (called "Spaltform") through the "Ubuntu App Developer" portal at [http://developer.ubuntu.com/](http://developer.ubuntu.com/). The application is written in Python, and, as one of the features of the App Developer portal is that someone at Canonical will do your packaging for you, I just submitted a tarball of the app's root directory. My app made it through the approval process OK, and is now listed as published (and even has one sale!). However, I can't see it in the Software Center.

I think this is because my system is amd64. The "Technical Details" from my app's page are as follows:
```
Technical details

Archive identifier:
    commercial-ppa-uploaders/splatform
Archive signing key:
    XXXXXXXXXXXXX
Series and architectures:

        Ubuntu Oneiric (11.10) for i386


```
I think this means that Canonical only packaged my Python app for i386, and it thus does not show in the Software Center of an amd64 system.

My question has two parts:
[LIST=1]
[*]Can anyone confirm that "Spaltform" shows up as a paid application on the i386 platform?
[*]As the app was originally developed on an amd64 Ubuntu system, I know that it works perfectly well on that platform. Who should I contact at Canonical about having my app packaged for both i386 and amd64? Is it necessary to submit my own debs to allow the app to install on both platforms? Or is Canonical supposed to generate both and they just didn't in this instance?
[/LIST]

---

