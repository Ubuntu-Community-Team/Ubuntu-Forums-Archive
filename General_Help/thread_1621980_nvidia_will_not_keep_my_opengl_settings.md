---
title: "nvidia will not keep my opengl settings"
date: 2010-11-14
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-11-14
i set it to high performance and to sync to Vblank and it reverts on the next boot

---

### Post by nerdy_kid on 2010-11-14
"it reverts"?  as in, you run the nvidia-settings after a reboot all your settings are gone?

---

### Post by pqwoerituytrueiwoq on 2010-11-14
> **nerdy_kid said:**
> "it reverts"?  as in, you run the nvidia-settings after a reboot all your settings are gone?
yes

---

### Post by Frogs Hair on 2010-11-14
You may do this , but make sure to select quit when exiting X Server Settings to save or your settings or they will revert.

---

### Post by pqwoerituytrueiwoq on 2010-11-14
> **Frogs Hair said:**
> You may do this , but make sure to select quit when exiting X Server Settings to save or your settings or they will revert.
i do i am starting to think it hates me

---

### Post by Frogs Hair on 2010-11-14
This may help. [http://ubuntuforums.org/showthread.php?t=1518731&highlight=server+won%27t+save+settings](http://ubuntuforums.org/showthread.php?t=1518731&highlight=server+won%27t+save+settings)

---

### Post by pqwoerituytrueiwoq on 2010-11-15
Added this to startup
```
nvidia-settings --assign="SyncToVBlank=1" --assign="openGLImageSettings=3"
```

---

