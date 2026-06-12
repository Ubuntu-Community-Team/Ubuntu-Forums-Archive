---
title: "Open Office 1.9"
date: 2006-05-04
forum: General Help
---

### Post by rcarring on 2006-05-04
1.9 was the beta release of Open Office 2.0. It has not yet been updated in the repositories to release 2.01. Any idea when this event is scheduled to occur? I know that Mozilla was upgraded to 1.7.13 within the last few days.

---

### Post by iball on 2006-05-04
Presumably the latest version will be in the Dapper Repositories.

You might find there is some reason why the beta version has not been updated yet.  If you really need the latest version, you can always download it from [www.openoffice.org](www.openoffice.org), and install it manually.

--Ian

---

### Post by ajgreeny on 2006-05-04
You can also add the following to your /ertc/apt/sources.list file and use this version.  It has a few minor bugs but otherwise works well.

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

As I understand it there is unlikely to be an update of OOo in the official repo's of Breezy, you will need to get Dapper to have the new version.

---

### Post by rcarring on 2006-05-04
Thanks for your help. I typed in the new repository and ran sudo apt-get update, a little while later the Update Manager told me I had 91.2 mb of updates to install, including the revision to Open Office.

---

### Post by pracslipkerm on 2006-05-14
I have been trying to update OOo from the beta version and kept having problems. I updated the repositry as 'ajgreeny' said and I too got the update manager telling me moments later that I have updates to install!
Thanks heaps guys!!! :-D

---

