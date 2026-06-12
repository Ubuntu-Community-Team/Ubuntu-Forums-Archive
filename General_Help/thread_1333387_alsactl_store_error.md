---
title: "alsactl store error"
date: 2009-11-21
forum: General Help
---

### Post by Treeh on 2009-11-21
Hello,

After configuring the output of my sound card, and attempting to save my settings using:

```
 alsactl store 
```

I get the following error:

```
 alsactl: get_control:249: Cannot read control '2,0,0,Mic Capture Volume,0': Invalid argument

```

Does anyone know how to approach/fix this problem?

Thanks.

EDIT: I simply unplugged my microphone.

---

### Post by SuperSonic4 on 2009-11-21
You may need to be root ```
sudo alsactl store
```

---

### Post by Treeh on 2009-11-21
> **SuperSonic4 said:**
> You may need to be root ```
sudo alsactl store
```

I tried that as well, same error.

---

### Post by Treeh on 2009-11-21
Bumpidy!

---

### Post by Treeh on 2009-11-21
And....bump again.

---

