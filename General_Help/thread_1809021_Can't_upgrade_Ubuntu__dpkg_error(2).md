---
title: "Can't upgrade Ubuntu  dpkg error(2)"
date: 2011-07-21
forum: General Help
---

### Post by hacker_at_linux on 2011-07-21
I tried to upgrade ubuntu , downloaded everything that was needed but I am not able to install anything.
It gives an error
```
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 7174 package 'python-egenix-mxdatetime':
 missing description
dpkg: error: parsing file '/var/lib/dpkg/available' near line 7175:
 field name `Package(' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

since then I am not able to install anything on my aptdaemon fails for anything that I try to install
How to deal with it

---

### Post by plucky on 2011-07-21
> **hacker_at_linux said:**
> I tried to upgrade ubuntu , downloaded everything that was needed but I am not able to install anything.
It gives an error
```
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 7174 package 'python-egenix-mxdatetime':
 missing description
dpkg: error: parsing file '/var/lib/dpkg/available' near line 7175:
 field name `Package(' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

since then I am not able to install anything on my aptdaemon fails for anything that I try to install
How to deal with it

You can try from a terminal ```
sudo mv /var/lib/dpkg/available /var/lib/dpkg/available-broken
sudo mv /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo apt-get update
```

and see if it now works.

Good Luck

---

### Post by hacker_at_linux on 2011-07-21
Hey thanx the thing worked ... But I don't understand this 
Can you please tell me what I just did
Looks like a copy command 
but what exactly is this

---

### Post by CatKiller on 2011-07-21
> **hacker_at_linux said:**
> Can you please tell me what I just did

The list of available packages was broken (hence the error). You renamed the broken one to something else and used a backup instead. You renamed rather than deleting in case it all went pear-shaped.

---

