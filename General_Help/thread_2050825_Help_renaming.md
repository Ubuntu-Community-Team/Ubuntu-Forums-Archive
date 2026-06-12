---
title: "Help renaming?"
date: 2012-08-31
forum: General Help
---

### Post by Manhi40 on 2012-08-31
I recently downloaded a few nes roms, 3538 to be exact, and they came labeled as "nesgame.nes;1" and 
I can't play the games on my emulator with ;1 at the end. 
Anyone now how to rename them? or I can sit down, and rename 3580 files...

---

### Post by Futant on 2012-08-31
Try [http://thunar.xfce.org/](http://thunar.xfce.org/) not used it myself...

---

### Post by evilsoup on 2012-08-31
If you're OK with the command line, there is a little program included by default called *rename*. In your case, to remove ';1' from the end of a bunch of files, cd into the directory they're in and

rename 's/\;1//' *\;1

should do it. For more information on how to use rename, use

man rename

To be on the safe side, you should run rename using the -n flag first. This will show you  what changes will be made without doing anything.

rename -n 's/\;1//' *\;1

---

### Post by Manhi40 on 2012-08-31
Can't rename *;1 *: No such file or directory
thanks for the rename thing tho, the more i know!

---

### Post by drmrgd on 2012-08-31
That should work.  Are you sure that you typed it correctly?  I tested it here and if the file names are as you suggest, it works ok for me:

```
drmrgd@CygnusX1:~/sandbox/tmp $ ls
game1.nes;1  game2.nes;1  game3.nes;1  game4.nes;1  game5.nes;1
drmrgd@CygnusX1:~/sandbox/tmp $ rename -n 's/\;1//' *\;1
game1.nes;1 renamed as game1.nes
game2.nes;1 renamed as game2.nes
game3.nes;1 renamed as game3.nes
game4.nes;1 renamed as game4.nes
game5.nes;1 renamed as game5.nes
drmrgd@CygnusX1:~/sandbox/tmp $ rename 's/\;1//' *\;1
drmrgd@CygnusX1:~/sandbox/tmp $ ls
game1.nes  game2.nes  game3.nes  game4.nes  game5.nes
```

Try copying and pasting the command that evilsoup posted.

---

