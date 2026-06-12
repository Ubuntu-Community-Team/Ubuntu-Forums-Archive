---
title: "Ubuntu Updates Won't Install 11.04"
date: 2011-06-16
forum: General Help
---

### Post by vonk88 on 2011-06-16
Hey there, I'm semi-new to Ubuntu, but I've been able to fix all my problems except for this one.  Everything ran fine till a few days ago.  Update manager will download updates, but it is unable to install them.  This is the error that pops-up.


installArchives() failed: 
Extracting templates from packages: 83%%
Extracting templates from packages: 100%%
Preconfiguring packages ...

Extracting templates from packages: 83%%
Extracting templates from packages: 100%%
Preconfiguring packages ...

Extracting templates from packages: 83%%
Extracting templates from packages: 100%%
Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 5508 package 'perl-modules':
 `Replaces' field, invalid package name `

what do I do?

PS. I've been using Bleachbit. Could it have bleached something important?

---

### Post by plucky on 2011-06-16
> dpkg: error: parsing file '/var/lib/dpkg/status' near line 5508 package 'perl-modules':
`Replaces' field, invalid package name `


Try from a terminal ```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-broken
sudo mv /var/lib/dpkg/status-old /var/lib/dpkg/status
```

What that does is move the status file to a file called status-broken and them moves the file status-old to status.

Now see if apt-get works with ```
sudo apt-get update && sudo apt-get upgrade
```

Post any errors.

Good luck

---

### Post by vonk88 on 2011-06-16
Thank you very much. Works like a charm. It added the "replacement" versions of a bunch of files I guess?  Could Bleachbit have caused my problem?

Thanks again.

---

