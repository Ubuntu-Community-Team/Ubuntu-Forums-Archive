---
title: "Script to open files on second monitor with mouse"
date: 2009-08-04
forum: General Help
---

### Post by yonexFactory on 2009-08-04
Hi all...

I've got my TV connected to my computer and set up as a separate X screen. If I try to open VLC, Nautilus, etc. on the TV, the program will start on the computer monitor instead. I have found a way around this will the following script. 
```

#!/bin/bash
export DISPLAY=:0.1 && nautilus
export DISPLAY=:0.1 && vlc

```

So I have that set up as a launcher, and then I can open VLC's playlist and drag the file over from nautilus on the TV screen. However, I figure a more convenient way to do this would be to write a different script which will allow me to just right-click on the file and say "Open with [script]" and have VLC open with the file playing on the TV.

Any help with adding to the script above, or making another one altogether would be much appreciated.

Thanks.

---

### Post by yonexFactory on 2009-08-04
Solved.
```

#!/bin/bash
export DISPLAY=:0.1 && vlc "$1"

```

Simple as that. #-o

---

