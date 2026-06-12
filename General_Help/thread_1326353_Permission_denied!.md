---
title: "Permission denied!"
date: 2009-11-14
forum: General Help
---

### Post by tarchy on 2009-11-14
```
sh: /home/daniel/.conky/conkyparts/conkytemplate.sh: Permission denied
sh: /home/daniel/.conky/conkyparts/conkyheader.sh: Permission denied
sh: /home/daniel/.conky/conkyparts/conkycalender.sh: Permission denied
sh: /home/daniel/.conky/conkyparts/conkycore.sh: Permission denied
sh: /home/daniel/.conky/conkyparts/conkymemory.sh: Permission denied
sh: /home/daniel/.conky/conkyparts/conkygraphics.sh: Permission denied
sh: /home/daniel/.conky/conkyparts/conkydevices.sh: Permission denied
sh: /home/daniel/.conky/conkyparts/conkynetwork.sh: Permission denied
sh: /home/daniel/.conky/conkyparts/conkyTV.sh: Permission denied
sh: /home/daniel/.conky/conkyparts/conkycore.sh: Permission denied
sh: /home/daniel/.conky/conkyparts/conkymemory.sh: Permission denied
sh: /home/daniel/.conky/conkyparts/conkydevices.sh: Permission denied

```




I am trying to run a cool conky script [http://conky.linux-hardcore.com/?page_id=764](http://conky.linux-hardcore.com/?page_id=764)

and when I saved the scripts it needs there and type conky into terminal to start it up, it gives me this. I tried running 'sudo conky' but still the same error... please help D:

---

### Post by emigrant on 2009-11-14
i think you should give the script execution permission:

```

sudo chmod 755 <filename>

```

---

### Post by tarchy on 2009-11-14
> **emigrant said:**
> i think you should give the script execution permission:

```

sudo chmod 755 <filename>

```

Thanks buddy :)

---

