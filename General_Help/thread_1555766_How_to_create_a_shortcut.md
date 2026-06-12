---
title: "How to create a shortcut"
date: 2010-08-18
forum: General Help
---

### Post by satimis on 2010-08-18
Hi folks,


Ubuntu 10.04

How to create a short-cut starting a program.


Each time I have to perform follow on terminal:-

$ cd /home/satimis/RedR/usr/lib/python2.6/dist-packages/Red-R/canvas/
$ python red-RCanvas.pyw

Please advise.  TIA


B.R.
satimis

---

### Post by inameiname on 2010-08-18
I suggest a script:

```

#!/bin/bash
cd /home/satimis/RedR/usr/lib/python2.6/dist-packages/Red-R/canvas/
python red-RCanvas.py

```...and then every time you click this script it will run the above. You could also make a launcher for the script too, such as right clicking on the desktop and selecting 'Create new launcher' and directing where the script itself is located. Then every time you click the launcher icon it will run the script, ie, what you must write in the terminal all the time.

---

### Post by satimis on 2010-08-18
> **inameiname said:**
> I suggest a script:

```

#!/bin/bash
cd /home/satimis/RedR/usr/lib/python2.6/dist-packages/Red-R/canvas/
python red-RCanvas.py

```...and then every time you click this script it will run the above. You could also make a launcher for the script too, such as right clicking on the desktop and selecting 'Create new launcher' and directing where the script itself is located. Then every time you click the launcher icon it will run the script, ie, what you must write in the terminal all the time.

Hi,

Thanks for your advice.

I have the shortcut created on desktop

B.R.
satimis

---

### Post by inameiname on 2010-08-18
Sure. Oh, and if you hadn't noticed, I changed this line:

python red-RCanvas.pyw

to

python red-RCanvas.py

as I'm guessing it was a typo, as I've never seen that file extension. If I'm wrong, of course remember to change it back.

---

### Post by satimis on 2010-08-18
> **inameiname said:**
> Sure. Oh, and if you hadn't noticed, I changed this line:

python red-RCanvas.pyw

to

python red-RCanvas.py

as I'm guessing it was a typo, as I've never seen that file extension. If I'm wrong, of course remember to change it back.

Hi,

I already changed it back.  That file doesn't exist.  No problem.  Thanks

satimis

---

