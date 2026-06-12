---
title: "control compiz from panel?"
date: 2010-09-19
forum: General Help
---

### Post by joesnose on 2010-09-19
Hello all,

had a search around but couldnt find anything, sorry if this has been posted already.

I want to find a way to control compiz from my panel, basically have some custom launchers that would say rotate cube or bring up expo, i have been unable to find commands to do this, does anyone know if this is possible. even if it were a link to a bash script.

thanks.

---

### Post by RJ12 on 2010-09-19
I would be interested in this too!
:)

---

### Post by themusicalduck on 2010-09-19
Here's a post about making a script to rotate the cube - [http://ubuntuforums.org/showpost.php?p=8001765&postcount=3](http://ubuntuforums.org/showpost.php?p=8001765&postcount=3)

Not sure about controlling other things though.

---

### Post by joesnose on 2010-09-20
Thanks themusical duck, that is a nice link, although i think you are right just uses wmctrl and i believe that can control windows but not compiz itself.

Anyone else able to shed some light on this one?

---

### Post by joesnose on 2010-09-21
Fouund a solution.

install xautomation, this allows for creating scripts that send key presses.

make a script, here is an example:

```
#!/bin/bash

xte 'keydown Shift_L' 'keydown Alt_L' 'key s' 'keyup Shift_L' 'keyup Alt_L'
```

if you need help with the xte command type "xte man" in a terminal, it will show the manual.

This script sends the key presses associated with my shift switcher in compiz, i had to change the super key as i was unable to get it to work with the xte command.

i then made a launcher that points to this script.

works for me. thanks to the community.

EDIT, how do i mark this thread as solved???

---

