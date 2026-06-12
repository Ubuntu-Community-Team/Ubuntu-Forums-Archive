---
title: "Deluge ppa"
date: 2011-04-28
forum: General Help
---

### Post by mdhollis on 2011-04-28
I added the deluge ppa to my repository,

```
sudo add-apt-repository ppa:deluge-team/ppa
```

I get an error that states "404 Not Found" when I update.  I'm just wondering the reason why if anyone knows.  Thanks.

---

### Post by hwttdz on 2011-04-28
They/launchpad probably don't have an 11.04 repo up yet.  You can either edit /etc/apt/sources.list.d/ ?delugeteamorwhatever? and change the "natty" to "lucid" and get the lucid versions which should work find and change it back in a few days.  Or you can just let it be for a few days and they should have a natty one up any time.

---

### Post by mdhollis on 2011-04-28
Thanks for the help.  That did the trick.  I hate error messages, lol.

---

