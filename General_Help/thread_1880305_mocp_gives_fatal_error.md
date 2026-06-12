---
title: "mocp gives fatal error"
date: 2011-11-13
forum: General Help
---

### Post by lazylew on 2011-11-13
In Xubuntu 10.04 when starting mocp I get this:
FATAL ERROR Can't send () int to the server

I suppose downgrading mocp might solve this, but I don't know how to do this.
In Synaptic the only version I see is the alpha; how do I downgrade it to the stable version?

---

### Post by Jose Catre-Vandis on 2011-11-13
Will it run as root?
```
sudo mocp
```

If so you might need to add yourself or moc to a group.

Otherwise its wait for a response from the moc forum ;)

---

### Post by lazylew on 2011-11-14
> **Jose Catre-Vandis said:**
> Will it run as root?
```
sudo mocp
```If so you might need to add yourself or moc to a group.

Otherwise its wait for a response from the moc forum ;)
With sudo I get the same error. The moc-forum is usualy quite slow in responding :neutral:

---

### Post by lazylew on 2011-11-14
> **lazylew said:**
> With sudo I get the same error. The moc-forum is usualy quite slow in responding :neutral:found it :) 
googling I came on a Polish discussion with the same problem. 
With google translate I found out what they were saying: delete moc's cache folder ~/.moc/cache ```
rm -rf cache
```

---

