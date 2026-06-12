---
title: "tar options challenge!"
date: 2011-02-26
forum: General Help
---

### Post by ex_isp on 2011-02-26
[FONT=Verdana][COLOR=#333333]Can anyone think of a better way to recursively find and tar image files than the below method?
[/COLOR][/FONT][B][SIZE=2]
[/SIZE][/B]

[FONT=Verdana][COLOR=#333333]find /path/to/images/ -type f \( -iname "*.jpg" -o -iname "*.gif" -o -iname "*.png" \) -print0 | xargs -0 tar rvf jpg-gif-png.tar &>find.log[/COLOR][/FONT]

---

### Post by ex_isp on 2011-02-26
Bump...come on gurus.  Lean this one out a little   :popcorn:

---

### Post by ex_isp on 2011-02-26
One more try,  can anyone improve on this command?

---

### Post by adduds on 2011-02-26
side not lol

is that Bjarne Stroustrup in ur pic :p

---

### Post by Diametric on 2011-02-26
No answer, but as I'm learning thus schtuff now, I'd love an answer with explanation, if you're keen to give it.

Cheers!

---

### Post by gmargo on 2011-02-26
Instead of using **xargs(1)**, you can tell **tar(1)** to read the list of files from the standard input:
```

[FONT=Verdana][COLOR=#333333]find /path/to/images/ -type f  \( -iname "*.jpg" -o -iname "*.gif" -o -iname "*.png" \) -print |  \
    tar cfv jpg-gif-png.tar -T - > find.log 2>&1
[/COLOR][/FONT]
```[FONT=Verdana][COLOR=#333333]
[/COLOR][/FONT]

---

### Post by ex_isp on 2011-02-26
> **adduds said:**
> side not lol

is that Bjarne Stroustrup in ur pic :p

Nope, just little 'ole me!

---

### Post by ex_isp on 2011-02-26
> **gmargo said:**
> Instead of using **xargs(1)**, you can tell **tar(1)** to read the list of files from the standard input:
```

[FONT=Verdana][COLOR=#333333]find /path/to/images/ -type f  \( -iname "*.jpg" -o -iname "*.gif" -o -iname "*.png" \) -print |  \
    tar cfv jpg-gif-png.tar -T - > find.log 2>&1
[/COLOR][/FONT]
```[FONT=Verdana][COLOR=#333333]
[/COLOR][/FONT]
Gmargo, that's an interesting solution!  Hadn't thought of that.  Nice!   :P

---

### Post by Diametric on 2011-02-26
> **ex_isp said:**
> Gmargo, that's an interesting solution!  Hadn't thought of that.  Nice!   :P

What would you have used?

---

### Post by ex_isp on 2011-02-26
> **Diametric said:**
> What would you have used?
The one at the top that I posed the original question with...using xargs

---

### Post by ex_isp on 2011-02-26
> **Diametric said:**
> No answer, but as I'm learning thus schtuff now, I'd love an answer with explanation, if you're keen to give it.

Cheers!

This might explain some of it
[http://ss64.com/bash/xargs.html](http://ss64.com/bash/xargs.html)

---

### Post by ex_isp on 2011-02-27
> **gmargo said:**
> Instead of using **xargs(1)**, you can tell **tar(1)** to read the list of files from the standard input:
```

[FONT=Verdana][COLOR=#333333]find /path/to/images/ -type f  \( -iname "*.jpg" -o -iname "*.gif" -o -iname "*.png" \) -print |  \
    tar cfv jpg-gif-png.tar -T - > find.log 2>&1
[/COLOR][/FONT]
```[FONT=Verdana][COLOR=#333333]
[/COLOR][/FONT]

Will you still need to do tar 'rvf' though to append the files within  the tar file you're generating?  Will it handle filenames with spaces?

---

### Post by gmargo on 2011-02-27
> 
Will you still need to do tar 'rvf' though to append the files within   the tar file you're generating?
You only need the "append" mode if you use **xargs(1)**, since **tar(1)** might be invoked more than once.

> 
Will it handle filenames with spaces?     
Of course.

---

