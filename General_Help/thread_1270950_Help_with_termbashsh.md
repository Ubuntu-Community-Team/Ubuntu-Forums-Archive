---
title: "Help with term/bash/sh"
date: 2009-09-20
forum: General Help
---

### Post by renkinjutsu on 2009-09-20
i currently have this running in the terminal

```
while true
do find Music/ -type f -name '*mp3' -exec mplayer -ao alsa '{}' \;
done
```

it's working well but.. is there any way to make the play order random?

---

### Post by unutbu on 2009-09-20
There must be a way to do with with bash, but I don't know it.
Here is a way to do it with python:

Save this to ~/bin/play_random.py:
[PHP]
#!/usr/bin/env python
import os
import random
import sys
from subprocess import Popen,PIPE,STDOUT
music_dir=sys.argv[1]
music=[]
for root, dirs, files in os.walk(music_dir,topdown=False):
    for afile in files:
        if afile.endswith('.mp3'):
            music.append(os.path.join(root,afile))
os.chdir(music_dir)
while True:
    song=random.choice(music)
    cmd="mplayer -ao alsa '%s'"%song
    print(cmd)
    proc=Popen(cmd, shell=True, stdout=PIPE, ).communicate()
[/PHP]
Make it executable:
```

chmod +x ~/bin/play_random.py
```

Run it like this:
```

play_random.py ~/Music
```

---

### Post by renkinjutsu on 2009-09-20
thanks for your speedy reply!

i actually just stuck with bash and made a little alias.. i stumbled upon linuxcommand.org .. and they had the "sort" command listed on one of their pages, and i looked at `man sort` and discovered i can use it to sort randomly!

so: find .. | sort -R | xargs --replace=+ mplayer -ao alsa '+'
thanks though.. and your script is good study material

---

### Post by unutbu on 2009-09-20
Thanks for the information... I didn't know about sort -R !

---

