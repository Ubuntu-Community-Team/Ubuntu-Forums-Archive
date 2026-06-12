---
title: "Disable GDM issue"
date: 2010-05-01
forum: General Help
---

### Post by Cardale on 2010-05-01
I was trying to disable GDM and I am getting

```
stop: Unknown instance: 
```

when I use this command

```
sudo service gdm stop
```

or this command 

```
sudo stop gdm
```

---

### Post by happyhamster on 2010-05-01
```
stop: Unknown instance: 
```
One way of getting this message is trying to stop gdm while it isn't running.

---

