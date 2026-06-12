---
title: "GetDeb updates not working"
date: 2012-09-21
forum: General Help
---

### Post by sienile on 2012-09-21
I get the following error when trying to update GetDeb programs from the Update Manager.

> Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

I have the keys installed from the GetDeb site, even reinstalled them to make sure they were done right, but still get the error.

---

### Post by raja.genupula on 2012-09-21
Open your terminal and type as 

```
sudo apt-get update
sudo apt-get upgrade
```

Then its going to ask you the same thing as you above and you can accept it by giving yes then it will install them .

---

### Post by sienile on 2012-09-21
Already tried those and it didn't work.

But I found a solution. I opened up the Software Sources program and deleted the key. Then I added it back using the manual method.
```
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
sudo apt-get update
```

It appears that they changed the key recently. The one I had before started with an F, the new one starts with a number.

---

