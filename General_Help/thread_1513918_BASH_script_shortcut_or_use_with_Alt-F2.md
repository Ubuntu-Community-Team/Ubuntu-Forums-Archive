---
title: "BASH script shortcut or use with Alt-F2"
date: 2010-06-20
forum: General Help
---

### Post by sparcxl on 2010-06-20
I have a simple bash script rd.sh

```

#!/bin/bash
rdesktop -g 1279x757 ${1} &

```
This is setting a specific resolution at which time devilspie moves it to the workspace I want.

I am trying to run this in the run command dialog (alt-f2) as rd.sh <servername> but it does not work. My goal is to be able to create a desktop menu item/shortcut in gnome to some specific servers and/or run this from the Run Application dialog.  I can run this without issue from the terminal.  Any better suggestions?

Thanks!

---

### Post by bruno9779 on 2010-06-20
Put the script somewhere in your PATH.

I advise you to put it in /home/user/bin, with an unique name.

If /home/user/bin in not in your path then:
> 
To append to the PATH variable and make it permanent all you need to do is enter the following in your .bashrc file in your home directory (~/.bashrc).
Code:

```
export PATH=$PATH:<add new path here>
```

IMPORTANT! -make sure you include the '$PATH' portion as that simply completes to all of the directories you already have in your path.

So if you leave out '$PATH' and just enter the one you want, all others will be gone (not the directories...just their inclusion in PATH).

After that all new entries you want need to be separated by a colon (without any spaces between colons and entries).

If you don't want it to be permanent, instead of adding it in ~/.bashrc, simply enter it in a terminal (it'll only take effect in that current subshell).



After doing this, you will be able to call your script from ALT+F2 and the terminal, just by writing the script unique name (you won't need to specify the path to it)

---

### Post by sparcxl on 2010-06-20
Thank you for the response, however the script is in my path. It does not pass the ${1} from the Run Application box. I can create a separate script for each of the servers I connect to, I guess that would work. I was just curious if there was a way to use one script for multiple hosts.

---

### Post by bruno9779 on 2010-06-20
How about making the script to run:

```
gnome-terminal -e rdesktop -g 1279x757 ${1} &
```

---

