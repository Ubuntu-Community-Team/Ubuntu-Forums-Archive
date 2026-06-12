---
title: "Copy cp errors to a log file"
date: 2010-10-29
forum: General Help
---

### Post by seventyeights on 2010-10-29
I'm trying to restore a corrupt windows disk. When I try to copy the user's folder, the huge amount of errors exceeds the terminal's buffer and are lost. I would like to send cp errors to a file so that I have a list of the corrupt files. (hopefully the user will decide they are not important)

I'm presently using
```
sudo cp -rp (badfolder) (newfolder)
```

Thanks

---

### Post by dcstar on 2010-10-29
> **seventyeights said:**
> I'm trying to restore a corrupt windows disk. When I try to copy the user's folder, the huge amount of errors exceeds the terminal's buffer and are lost. I would like to send cp errors to a file so that I have a list of the corrupt files. (hopefully the user will decide they are not important)

I'm presently using
```
*sudo cp -rp (badfolder) (newfolder)*
```

Thanks

```
*command* 2> error.output.file
```

---

