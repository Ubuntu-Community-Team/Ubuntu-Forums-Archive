---
title: "I want to mount a drive in 2 folders"
date: 2010-08-08
forum: General Help
---

### Post by cackles on 2010-08-08
I mounted a hard drive and its working ok. But I want to expand on it. I'd like to make it accessible via another folder, like make it look like /home/cackles/added as well as simply just /added. Is it just like when you mount the drive and add the line to fstab? Im asking before I do it in case I break something ... yea call me paranoid :) Im just not sure.

---

### Post by Bachstelze on 2010-08-08
```
sudo mount -o bind /added /home/cackles/added
```

As a fstab line it looks like

```
/added /home/cackles/added auto bind 0 0
```

---

### Post by cackles on 2010-08-08
That is excellent, thank you.

---

