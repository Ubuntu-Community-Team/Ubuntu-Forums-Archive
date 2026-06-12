---
title: "moving and renaming multiple pictures"
date: 2010-07-02
forum: General Help
---

### Post by Psycho.mario on 2010-07-02
I have a large collection of pictures, that are arranged in lots of directories such as pictures/june/001.jpg, pictures/july/005.jpg
I was wondering if it would be possible to move these pictures around so that they are also renamed to their parent folders name, such as moving picture/june/001.jpg to picture/june_001.jpg 
Is there an easy way to do this or will i just have to write a shell script?

Thanks

---

### Post by Psycho.mario on 2010-07-02
I did it, i wrote a small python script to do it:

```
#!/usr/bin/python
import sys
import os
import shutil
if len(sys.argv) < 2:
        print "Usage: %s [DIRECTORY]" % sys.argv[0]
        sys.exit()
args=sys.argv
cwd=""
for i in args[1:]:
    cwd+=i+" "
cwd=cwd.rstrip()
os.chdir(cwd)
dirs=os.listdir(os.getcwd())
for sub in dirs:
    fname=sub.replace(" ", "_")
    if "." in sub: continue
    for pic in os.listdir(sub):
        src=cwd+sub+"\x2f"+pic
        dst=cwd+fname+"_"+pic
        shutil.move(src, dst)
    os.rmdir(sub)

```

---

