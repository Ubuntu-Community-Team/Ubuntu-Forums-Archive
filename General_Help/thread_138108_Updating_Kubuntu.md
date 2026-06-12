---
title: "Updating Kubuntu"
date: 2006-03-01
forum: General Help
---

### Post by Optiker on 2006-03-01
I'm currently running Kubuntu 5.10. Probably trivial, and probably covered someplace in some previous thread, but, how do update 5.10 to the current version of Kubuntu? 

Thanks!
Optiker

---

### Post by Optiker on 2006-03-01
As I looked elsewhere, I happened onto the answer, so please disregard this question.

For the benefit of others, here's what I found...

[http://kubuntuforums.net/forums/index.php?topic=3697.0](http://kubuntuforums.net/forums/index.php?topic=3697.0)

Optiker

---

### Post by eMuNiX on 2006-03-01
sudo apt-get update
sudo apt-get upgrade

will make sure that you have the latest packages, 5.10 is the latest version of Breezy Badger the next version will be 6.04 Dapper Drake but this is still in testing.  When it does get released it should be as simple as changing your sources list with all instances of breezy becoming dapper then a sudo apt-get dist-upgrade from a command line should upgrade to Dapper.  I wouldn't do it yet unless you are prepared to carry out remedial work as things break.

---

