---
title: "Can't find package, can't update"
date: 2012-06-23
forum: General Help
---

### Post by Wiking on 2012-06-23
Hi, I was trying to install machanger on my laptop running Xubuntu, but I keep getting this error.

```
E: unable to locate package macchanger
```I opened the source list to edit it, but everything looked good. All the components had the hash tag removed.

I then tried **sudo apt-get update** but once it gets at 88% it just stops downloading. I then tried using the GUI  (Synaptic Package Manager) and it too stopped around 90%.

One thing I noticed both in the the terminal, and in the Interface for Synaptic is that both updates stopped downloading when it got to "Translation-en_CA" or woruld slow down drastically once that line showed up.

As of now I can't update or get any other package as well.

---

### Post by oldos2er on 2012-06-24
Have you tried switching servers? In Synaptic, Settings, Repositories, Download from:, choose Main server.

---

### Post by Wiking on 2012-06-24
Thanks that solved it.

---

