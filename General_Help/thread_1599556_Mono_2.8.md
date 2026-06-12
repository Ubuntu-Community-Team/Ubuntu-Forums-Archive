---
title: "Mono 2.8"
date: 2010-10-17
forum: General Help
---

### Post by Ishpeck on 2010-10-17
How much will I ruin if I try compiling/installing Mono 2.8 on top of Lucid Lynx? 

I just really want to play with C# 4.0

---

### Post by directhex on 2010-10-18
> **Ishpeck said:**
> How much will I ruin if I try compiling/installing Mono 2.8 on top of Lucid Lynx? 

I just really want to play with C# 4.0

Use --prefix=/opt/mono28 and you should be reasonably safe.

---

### Post by Ishpeck on 2010-10-18
Only reason I ask is because Mono's site says the following:

> Mono is considered a "core framework" in Ubuntu, meaning it has many applications depending upon it (roughly 40 applications). Due to this, the chance of one of those applications breaking due to unexpected changes in their underlying framework is considered too high to risk an update.

Right here: [http://mono-project.com/DistroPackages/Ubuntu](http://mono-project.com/DistroPackages/Ubuntu)

---

### Post by directhex on 2010-10-18
> **Ishpeck said:**
> Only reason I ask is because Mono's site says the following:



Right here: [http://mono-project.com/DistroPackages/Ubuntu](http://mono-project.com/DistroPackages/Ubuntu)

I know what it says; I wrote it.

---

### Post by bprins on 2010-10-24
Is the only way to get 2.8 on ubuntu by manually compiling it?

And, if I don't want to manually compile it (simply because I don't understand the consequences of that action) do I have to wait until Ubuntu 11.04?

Thanks a lot.

bas

---

### Post by directhex on 2010-10-24
> **bprins said:**
> Is the only way to get 2.8 on ubuntu by manually compiling it?

And, if I don't want to manually compile it (simply because I don't understand the consequences of that action) do I have to wait until Ubuntu 11.04?

Thanks a lot.

bas

Not necessarily until 11.04, but certainly until it's properly packaged.

Currently chasing some problems with ARM support.

---

