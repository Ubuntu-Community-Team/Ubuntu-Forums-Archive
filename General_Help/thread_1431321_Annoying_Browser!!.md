---
title: "Annoying Browser!!"
date: 2010-03-16
forum: General Help
---

### Post by harivittal.hk on 2010-03-16
I am receiving a notification which reads "ur browser has been updated and needs to be restarted".....
Its poping up again and again,am not able to stop it...Why is this happening?? Pl help...
Am using Firefox browser....

---

### Post by _h_ on 2010-03-16
Does the notification say exactly that, or does it say something like "restart firefox to complete your changes", etc..?

If you update firefox, it should only notify you once and only once. If you have plugins that get updated, removed, or added it will also supply a notification to restart your browser.

---

### Post by Serpher on 2010-03-16
This sounds like a Firefox error rather than the OS, try reinstalling it. Go into a terminal and type in the following:

```
sudo apt-get remove firefox
sudo apt-get install firefox
sudo apt-get update
```

You might get it one time after that, but after that it'll probably go away.

---

