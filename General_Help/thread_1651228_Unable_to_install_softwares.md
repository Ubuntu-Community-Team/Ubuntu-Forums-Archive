---
title: "Unable to install softwares"
date: 2010-12-22
forum: General Help
---

### Post by ron177 on 2010-12-22
Dear all,

I am getting an usual error message every time I try to install a  software from the Ubuntu Software Center. Is there anyway I can fix  this?

I am transcribing the complete error message:

"Requires installation of untrusted packages: The action would require  the installation of packages from not authenticated sources."
[COLOR=#888888]
Please help. I really need to download some softwares and I can't.

Ron
[/COLOR]

---

### Post by SbKhaan1 on 2010-12-22
I'm still new myself, but try this.. 

system>admin>software sources

Make sure "Download from" is set to "Main Server"

Close. If it asks you to update something, do it. 

In terminal:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Hope it helps!

---

