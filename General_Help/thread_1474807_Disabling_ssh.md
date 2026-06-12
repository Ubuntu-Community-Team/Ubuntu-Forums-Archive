---
title: "Disabling ssh"
date: 2010-05-06
forum: General Help
---

### Post by Edwinem on 2010-05-06
I want to be able to disable my computers ssh server without having to uninstall the program. The method I saw to use would be to go to System>Administration>Services and the just disable. However in 10.04 the Services menu does not seem to exist anymore. So I am wondering how I can easily disable the ssh server and if I want to start it back up again.

---

### Post by CharlesA on 2010-05-06
Run this in a terminial:

```
sudo service ssh stop
```

To start it back up:

```
sudo service ssh start
```

---

### Post by Edwinem on 2010-05-06
thanks a lot.

---

