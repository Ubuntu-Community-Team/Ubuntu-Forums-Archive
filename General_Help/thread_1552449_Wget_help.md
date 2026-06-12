---
title: "Wget help"
date: 2010-08-13
forum: General Help
---

### Post by Bobscrachy on 2010-08-13
How do you specify the directory wget is downloading to?

---

### Post by warddr on 2010-08-13
use the command cd (change directory) to navigate to the directory where you want the file to be downloaded to, if you did that you can use 
wget [http://awebsite.be/afile.zip](http://awebsite.be/afile.zip)

---

### Post by Bobscrachy on 2010-08-13
Nice, thank you.

---

### Post by Vgui on 2010-08-13
Also check out the **-P** (aka **--directory-prefix**) command line switch. For example you could run:

```

wget -P /home/batman/Desktop/savedjunk/ http://www.google.com/

```

To save the index page of google.com to the "savedjunk" folder on Batman's desktop.

---

