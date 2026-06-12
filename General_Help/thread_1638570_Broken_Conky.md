---
title: "Broken Conky"
date: 2010-12-05
forum: General Help
---

### Post by robbiemacg on 2010-12-05
After a couple of recent updates, I was disappointed to note that a piece of my conky had broken. Not sure exactly what I did, but I busted it.

I did a bit of experimenting and determined that my problem related to the script I was running to return information about my drives. 
This line of my .conkyrc ...
```
${execpi 30 ~/.conkycolors/bin/conkyHD1}
```Calls up a python script that looks like this ...
```
#!/usr/bin/env python
import sys
import os
import subprocess

# root filesystem
print "${voffset -2}${color0}${font Poky:size=15}y${font}${color}${offset 6}${voffset -7}Root: ${font Liberation Sans:style=Bold:size=8}${color1}${fs_used_perc /}%${color}${font}"
print "${voffset 2}${color0}${fs_bar 4,20 /}${color}${offset 8}${voffset -2}Free:${color2}${fs_free /}${color} In Use:${color2}${fs_used /}${color}"

# /home folder (if its a separate mount point)
if os.path.ismount("/home"):
    print "${voffset -2}${color0}${font Poky:size=15}y${font}${color}${offset 6}${voffset -7}Home: ${font Liberation Sans:style=Bold:size=8}${color1}${fs_used_perc /home}%${color}${font}"
    print "${voffset 2}${color0}${fs_bar 4,20 /home}${color}${offset 8}${voffset -2}Free:${color2}${fs_free /home}${color} In Use:${color2}${fs_used /home}${color}"

# folder in /media
for device in os.listdir("/media/"):
    if (not device.startswith("cdrom")) and (os.path.ismount('/media/'+device)):
        print "${voffset -2}${color0}${font Poky:size=15}y${font}${color}${offset 6}${voffset -7}"+device.capitalize()+": ${font Liberation Sans:style=Bold:size=8}${color1}${fs_used_perc /media/"+device+"}%${color}${font}"
        print "${voffset 2}${color0}${fs_bar 4,20 /media/"+device+"}${color}${offset 8}${voffset -2}Free:${color2}${fs_free /media/"+device+"}${color} In Use:${color2}${fs_used /media/"+device+"}${color}"
```If I comment out the line that sets that script running, everything else runs as expected. If I leave it untouched all the code the follows breaks (fonts/spacing get screwed up, etc.)

So, any thoughts about what might be the matter? I'm thinking that the issue relates to the version of Python I'm running or something? Maybe there's a problem importing modules?

I'm open to suggestions.

---

### Post by robbiemacg on 2010-12-06
Happy Monday!
Perhaps the screenshots below will lend some important clue?

---

### Post by TeoBigusGeekus on 2010-12-06
Does anything happen when you change the first line to
```
#!/usr/bin/env python2
```
?
I don't know if ubuntu has made the transition to python 3 yet, just guessing.

---

### Post by robbiemacg on 2010-12-06
Good thought, [TeoBigusGeekus]("http://ubuntuforums.org/member.php?u=504094")!
Your reasoning is good, unfortunately, altering the script in the way you suggested did not result in any change. The issue persists.

Are their any libraries or anything that might have been cleaned up or removed following an update that could be resulting in the problem I'm experiencing?

---

### Post by TeoBigusGeekus on 2010-12-06
Hmm...
What errors do you get when you run the script from terminal?
i.e.
```
python ~/.conkycolors/bin/conkyHD1
```

---

### Post by robbiemacg on 2010-12-06
Calling up the script from the Terminal does not return an error.
The follow code prints to screen:
```
${voffset -2}${color0}${font Poky:size=15}y${font}${color}${offset 6}${voffset -7}Root: ${font Liberation Sans:style=Bold:size=8}${color1}${fs_used_perc /}%${color}${font}
${voffset 2}${color0}${fs_bar 4,20 /}${color}${offset 8}${voffset -2}Free:${color2}${fs_free /}${color} In Use:${color2}${fs_used /}${color}
```That looks pretty sensible to me at a glance. See anything that appears out of the ordinary?

---

### Post by TeoBigusGeekus on 2010-12-06
Try to change this
```
${execpi 30 ~/.conkycolors/bin/conkyHD1}
```

to this
```
${execpi 30 python2 ~/.conkycolors/bin/conkyHD1}
```

---

### Post by robbiemacg on 2010-12-06
Having made the suggested change, I launched my Conky from the Terminal.
The script which monitors mounted drives failed to run, all other aspects of the Conky displayed as normal.
I also noted the following error message:
```
sh: python2: not found
```

---

### Post by TeoBigusGeekus on 2010-12-06
Change it to plain python.

---

### Post by robbiemacg on 2010-12-06
Hmmm. This proving to be a tricky problem.
The second change returned the following error message:
```
SyntaxError: invalid syntax
```

---

### Post by robbiemacg on 2010-12-06
So, I did a little more experimenting after work today.
If I edit my .conkyrc, replace the line that reads:
```
${execpi 30 ~/.conkycolors/bin/conkyHD1}
```with this piece of code:
```
${voffset -2}${color0}${font Poky:size=15}y${font}${color}${offset 6}${voffset -7}Root: ${font Liberation Sans:style=Bold:size=8}${color1}${fs_used_perc /}%${color}${font}
${voffset 2}${color0}${fs_bar 4,20 /}${color}${offset 8}${voffset -2}Free:${color2}${fs_free /}${color} In Use:${color2}${fs_used /}${color}
```(that's what the command **python ~/.conkycolors/scripts/conkyHD1.py** returns) then my Conky appears as I'm accustomed to seeing it.

My question is, could the problem maybe be with the shell script that's get the ball rolling? 
Here's what that looks like:
```
#! /bin/sh
cd ~/.conkycolors/scripts
$PYTHONPATH /usr/bin/python ~/.conkycolors/scripts/conkyHD1.py "$@"
```

---

### Post by robbiemacg on 2010-12-08
I'm seriously so stumped.
I get the same result when **~/.conkycolors/bin/conkyHD1 **and **python ****~/.conkycolors/scripts/conkyHD1.py **in the Terminal. (Redirected output and compared just to be certain.)
In either case the code that prints to screen looks like this:
```
${voffset -2}${color0}${font Poky:size=15}y${font}${color}${offset 6}${voffset -7}Root: ${font Liberation Sans:style=Bold:size=8}${color1}${fs_used_perc /}%${color}${font}
${voffset 2}${color0}${fs_bar 4,20 /}${color}${offset 8}${voffset -2}Free:${color2}${fs_free /}${color} In Use:${color2}${fs_used /}${color}
```
If I paste that into my .conkyrc in place of the line that's supposed to call the function that returns that code, it prints info and images correctly. 
What am I missing? There's a hole in my logic somewhere. I know that the Shell script is calling the Python script, is returning information that Conky can interpret correctly... yet it's not. Something is broken, but I can't figure out what that something is.

---

### Post by TeoBigusGeekus on 2010-12-08
What if you use execi instead of execpi?
```
${execi 30 ~/.conkycolors/bin/conkyHD1}
```

---

### Post by robbiemacg on 2010-12-25
UPDATE: It seems like the issue I experienced was directly related to upgrading to Conky 1.8.1. I'm marking this thread solved, though some might say I'm throwing up my hands.

---

