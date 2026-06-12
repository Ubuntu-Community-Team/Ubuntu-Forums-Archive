---
title: "Err http://ppa.launchpad.net lucid/main Packages"
date: 2012-02-23
forum: General Help
---

### Post by mikodo on 2012-02-23
Hi.

I have been getting this error, while trying to update my Lucid system for 2-3 days now. Should it be reported; or would the people responsible for the server be fully aware of it, and I am just wasting everyones' time reading this?

```
Get:6 http://us.archive.ubuntu.com lucid-updates/main Packages [566kB]      
Hit http://ppa.launchpad.net lucid/main Packages                                
Hit http://ppa.launchpad.net lucid/main Sources                                 
Hit http://ppa.launchpad.net lucid/main Packages            
Hit http://ppa.launchpad.net lucid/main Packages            
Hit http://ppa.launchpad.net lucid/main Sources             
Ign http://ppa.launchpad.net lucid/main Packages             
Err http://ppa.launchpad.net lucid/main Packages             
  404  Not Found

```

Thanks.

---

### Post by dcstar on 2012-02-24
> **mikodo said:**
> Hi.

I have been getting this error, while trying to update my Lucid system for 2-3 days now. Should it be reported; or would the people responsible for the server be fully aware of it, and I am just wasting everyones' time reading this?


Remove that bogus PPA entry from your Repositories list or select another local repository.

---

### Post by mikodo on 2012-02-24
> **dcstar said:**
> Remove that bogus PPA entry from you Repositories list or select another local repository.
Trial and error showed, I had erroneously added a PPA, that was only for Oneiric and I use Lucid... that was dumb... wasn't paying attention.

Removed it, and all is fine.

Thanks.

---

