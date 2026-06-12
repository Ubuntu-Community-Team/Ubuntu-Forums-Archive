---
title: "install error &quot;no root file system...&quot;"
date: 2006-02-10
forum: General Help
---

### Post by mervg on 2006-02-10
during ubuntu install,  after setting partition parameters, and selecting the write to disk, etc., i get "no root file system defined please correct from partitioning menu."
When going back to that menu, I don't find any place to set up a "root file system"
Any one know what im missing?

---

### Post by psusi on 2006-02-10
You did not assign any partition to be mounted as root ( / ).  Either do that, or just choose the automated partitioning option and let it use the defaults.

---

### Post by mervg on 2006-02-10
Okay, where do make that assignment and/or where is the automated partitioning that doesn't erase the entire disk?  I'm keeping a minimum part. for Windows, until I get linux fully installed.

---

### Post by carlosqueso on 2006-02-10
Choose "manually edit partition table" when you get to the menu with the different partitioning options.  [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/) is helpful.

---

