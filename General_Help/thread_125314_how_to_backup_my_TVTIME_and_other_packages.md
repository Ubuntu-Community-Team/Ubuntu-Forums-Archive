---
title: "how to backup my TVTIME and other packages?"
date: 2006-02-03
forum: General Help
---

### Post by medya on 2006-02-03
hey something happend to my ubuntu that I have to re-install it (my firefox dones work I tried to re-isntall but doenst with yet...)

I have downloaded several packages using "add program" ,things like , TV TIME , ZAP TV , ... Blah Blah 

my modem is 14.4 KB and it takes like 2 days for me to download those programs [If I be lucky and dont get discounnected during these 2 days]

so I wont be able to re-download them, is there any way to copy these TV TIME and ZAP TV to a CD or a USB drive and install it on my new ubuntu ?

---

### Post by GeneralZod on 2006-02-03
All installed packages should be cached in

```

/var/cache/apt/archives

```

Back up all of the .deb files there and you should be good to go.  I'd also suggest starting up Firefox with an empty profile to make sure that whatevevr problem you're having is not profile-related - if it is, then re-installing Ubuntu won't help :)

---

### Post by medya on 2006-02-03
"starting up Firefox with an empty profile" means what ?

---

