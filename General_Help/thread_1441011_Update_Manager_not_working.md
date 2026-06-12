---
title: "Update Manager not working"
date: 2010-03-28
forum: General Help
---

### Post by angellika on 2010-03-28
Hi Folks,

My Update Manager stopped working for last three weeks. When I press button INSTALL UPDATES in Update Manager, nothing happens just Reading packing information is executed and when it is finished nothing continues,so nothing I chosen is installed. I have tried to fix broken packages in Synaptic Manager, but no change. I have no idea where can problem lay, so will be really glad when you help me. 

I have Karmic 64.

Cheers,

Jaro

---

### Post by llamabr on 2010-03-28
in terminal, can you do an 

```
sudo apt-get update
```

and 

```
sudo apt-get upgrade
```

---

### Post by angellika on 2010-03-28
> **llamabr said:**
> in terminal, can you do an 

```
sudo apt-get update
```

and 

```
sudo apt-get upgrade
```

Thanks. This one worked for me. But is there any way how to fix GUI Update Manager? I prefer use it from terminal.

---

