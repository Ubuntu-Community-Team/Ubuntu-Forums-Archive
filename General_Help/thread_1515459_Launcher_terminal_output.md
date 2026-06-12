---
title: "Launcher terminal output"
date: 2010-06-22
forum: General Help
---

### Post by ionmich on 2010-06-22
Version 10.04 - Gnome - Custom Application Launcher

The command is...

bash -c "pal >pal.out; cat pal.out addon > result; more result"

...and I expected the result to show in a terminal. But it doesn't. How do I start a terminal from inside this command and make it active on the screen?

Thanks.

---

### Post by meoow on 2010-06-22
I used to look for the method which you are looking for,but it seems not existed.

---

### Post by ionmich on 2010-06-23
> **meoow said:**
> I used to look for the method which you are looking for,but it seems not existed.

Here is a solution. Construct a shell script with your editor. Make it executable with your file browser permissions. Then the launcher command could read...

gnome-terminal -e "your_script"

...BUT make sure the output length exceeds the height of the terminal that opens otherwise it will display in a flash and the terminal will disappear. You can do that with "more" and a series of lines ending with carriage returns.

Here is an example that works for me.

#!/bin/bash

pal >pal.out; cat pal.out addon > result; more result

...where "addon" is a text file that looks like this to use up terminal lines...

"*
*
*
*
*
*
*"
....etc.

---

