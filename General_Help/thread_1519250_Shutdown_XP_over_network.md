---
title: "Shutdown XP over network"
date: 2010-06-27
forum: General Help
---

### Post by hackerseraph on 2010-06-27
I was wondering what the ubuntu version of shutdown -i would be because I sometimes leave my DVR on recording shows and if I want to shut it down from the bedroom with my laptop instead of getting up and going into the living room, I used to be able to do so over the network through command prompt and I was just wondering what the command to send the network signal would be.

Thanks

---

### Post by psusi on 2010-06-27
You might try the net rpc shutdown command.

---

### Post by hackerseraph on 2010-06-27
aha this one

```
net rpc shutdown -I ipAddressOfWindowsPC -U username%password
```

---

