---
title: "scp autocompletion is broken in Karmic"
date: 2009-11-12
forum: General Help
---

### Post by MartinEve on 2009-11-12
Hi all,

On my Jaunty setups I have scp autocompleting using public keys.

On Karmic, I cannot get this to work.

For instance, in a bash shell I can do:

```
ssh theoria
```

and the login works, indicating that the key setup is working.

However, when I type:

```

scp theoria:~/ [TAB]
```

Instead of trying to connect to get a remote listing, the shell performs a *local* completion.

I'd really appreciate some help with this as it is really crucial to my setup!

Martin

---

### Post by zecg on 2009-11-26
Yes, I can confirm this. Have you submitted a bug report?

---

### Post by MartinEve on 2009-11-26
Better than that; submitted a patch and workaround at [https://bugs.launchpad.net/ubuntu/karmic/+source/bash-completion/+bug/449349](https://bugs.launchpad.net/ubuntu/karmic/+source/bash-completion/+bug/449349)

---

### Post by zecg on 2009-11-26
You, Sir, are a gentleman and a scholar.

---

### Post by MartinEve on 2009-11-26
Haha; thanks - hopefully it will get a sponsorship review soon for incorporation in updates.

---

