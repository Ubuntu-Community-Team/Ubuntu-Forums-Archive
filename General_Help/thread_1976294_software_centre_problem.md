---
title: "software centre problem"
date: 2012-05-08
forum: General Help
---

### Post by Sammax on 2012-05-08
opening software centre....gives following error(ubuntu 12.04)

'E:Encountered a section with no Package: header, E: problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


software centre not workin...tried apt-get update and upgrade at terminal...pls help....

---

### Post by Sammax on 2012-05-08
As no one has replied i just removed the line in error using sudo rm..

software centre workin now.....will it lead to problems???

---

### Post by cortman on 2012-05-08
Although sudo rm'ing things that give errors is an extremely bad practice as a whole, in this case it is actually the suitable fix. The files in /var/apt/lists are the text files downloaded when you run

```
sudo apt-get update
```

Removing them means that you'll just need to run the update again to get new package lists.
But remember, DON'T use rm with sudo unless you're absolutely sure of what you're doing, and what the consequences will be.
Good luck!

---

### Post by Sammax on 2012-05-09
Everthing working fine now.....no problem...thanx!!!....marking as solved...

---

