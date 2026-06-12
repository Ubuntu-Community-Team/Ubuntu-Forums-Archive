---
title: "Adding DJL to the Main Menu!"
date: 2010-06-13
forum: General Help
---

### Post by Rytron on 2010-06-13
Hi.
I run DJL by doing this:
```
cd ~/Documents/Games/DJL\ 1.2.20/
./djl.sh
```

However I want to add this to the Games menu. As in the attached picture, I am stuck. Can someone help?

I was also thinking of using a command similar to this:
```
cd ~/Documents/Games/DJL\ 1.2.20/./djl.sh; ./djl.sh
```

---

### Post by colorlessprism on 2010-06-13
you should be able to just do the path so there is no need to "cd", try and copy this and paste as the command:

"sh ~/Documents/Games/DJL\ 1.2.20/./djl.sh"

this is how i make my custom launchers

---

### Post by Rytron on 2010-06-13
> **colorlessprism said:**
> you should be able to just do the path so there is no need to "cd", try and copy this and paste as the command:

"sh ~/Documents/Games/DJL\ 1.2.20/./djl.sh"

this is how i make my custom launchers


Hey colorlessprism. Done! I needed the full path. Also I got rid of the space to simplify things.
```
sh /home/rytron/Documents/Games/DJL/djl.sh
```

---

