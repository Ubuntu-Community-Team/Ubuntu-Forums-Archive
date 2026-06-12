---
title: "Sound doesn't work with other users"
date: 2009-11-02
forum: General Help
---

### Post by guedesav on 2009-11-02
This is a problem that's around since I upgraded to Intrepid, and I've been delaying it long enough. Simply putting, no other user beyond the  one which is currently logged on can play sounds or anything else. Including root. This seems to be related with other strange problem that doesn't let me adjust GNOME configurations... as root!

For instance, when I run totem as root, it gives me this message(in Portuguese):

```
Ocorreu um erro ao carregar ou salvar as configurações para totem. Algumas de suas configurações podem não funcionar corretamente.
```

Which means it can't load or save configurations for totem. This same message appears for firefox and even gnome-settings-daemon. Alsamixer, on the other hand, just says "no mixer elems found", while my normal user has no trouble mixing whatever I want.

I believe this has to do with dbus, but I have no idea how to config dbus so it'll work with any other user besides the one who's logged on X.

---

