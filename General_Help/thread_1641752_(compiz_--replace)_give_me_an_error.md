---
title: "(compiz --replace) give me an error"
date: 2010-12-09
forum: General Help
---

### Post by binarylife on 2010-12-09
GConf backend: There is an unsupported value at path /apps/compiz/plugins/expo/allscreens/options/distance. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

---

### Post by sikander3786 on 2010-12-09
Press Alt + F2 and type,

```
gconf-editor
```

Navigate to /apps/compiz/plugins/expo/allscreens/options/distance. I don't know what have you got in there for distance but it '0' on my system.

---

### Post by binarylife on 2010-12-09
> **sikander3786 said:**
> Press Alt + F2 and type,

```
gconf-editor
```

Navigate to /apps/compiz/plugins/expo/allscreens/options/distance. I don't know what have you got in there for distance but it '0' on my system.



Nah , It's the same .
But now it's solved . There was an error in one of the core packages I think and I fixed it .
Thanks a lot .: )

---

### Post by callie780 on 2011-05-02
I have the same error but my value is also 0. How did you fix yours, please let me know. If you help me you get a star: :KS

---

