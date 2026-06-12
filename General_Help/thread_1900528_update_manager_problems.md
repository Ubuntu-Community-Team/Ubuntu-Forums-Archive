---
title: "update manager problems"
date: 2011-12-26
forum: General Help
---

### Post by flyingfisch on 2011-12-26
For the past week I've been getting this error from update manager:

```

Failed to download repository information
Check your Internet connection.

W:Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```

I know that I have internet access, so what could be causing this?

---

### Post by sirkeith on 2011-12-26
I get that now and then and the problem is at their end. Try again later, I have never found it to be a big problem.

---

### Post by wolfen69 on 2011-12-26
It could be that the ppa is no longer valid. If you have already downloaded what you need from the ppa, you could just disable it and do *sudo apt-get update*. 

What was the original reason for the ppa?

---

### Post by flyingfisch on 2011-12-26
So those ppa's aren't official Ubuntu ppa's? they're just ppa's that I must have installed stuff with in the past? If so, I'll just delete them.

EDIT: 

Oh, its crebs. OK. I'll just delete the PPA. I never use the program. Thanks everyone! :)

---

### Post by plucky on 2011-12-26
> I know that I have internet access, so what could be causing this? 

See [Here](http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/)

There is no PPA for Oneiric.

---

