---
title: "Slicing in Gimp errors"
date: 2012-04-02
forum: General Help
---

### Post by waldherrvonbirnbaum on 2012-04-02
looks like this:
```
Traceback (most recent call last):
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 692, in response
    dialog.res = run_script(params)
  File "/usr/lib/gimp/2.0/python/gimpfu.py", line 353, in run_script
    return apply(function, params)
  File "/usr/lib/gimp/2.0/plug-ins/py-slice.py", line 117, in pyslice
    left, right, top, bottom, i, j, ""))
  File "/usr/lib/gimp/2.0/plug-ins/py-slice.py", line 172, in slice
    temp_image.crop(right - left, bottom - top, left, top)
TypeError: integer argument expected, got float

```I am running Ubuntu 11.10 and the current Gimp. Any ideas? Thx!

---

### Post by raja.genupula on 2012-04-02
Hi , its actually a BUG and got fixed too 

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/767048](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/767048)

look at this

---

### Post by waldherrvonbirnbaum on 2012-04-02
Thank you very much!

> [Daniel M. Basso (dmbasso)]("https://launchpad.net/%7Edmbasso")             wrote             on 2011-12-04:                                                            [ #4]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/767048/comments/4")                                                  
[LIST]
[*]         [py-slice.patch]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/767048/+attachment/2619629/+files/py-slice.patch")                  (584 bytes,         text/plain)
[/LIST]
             The original of this duplicate bug doesn't exist anymore?
 Well, while this is sorted out, a simple workaround is to apply the attached patch to a user copy of the plug-in:
 cd .gimp-2.6/plug-ins/
cp /usr/lib/gimp/2.0/plug-ins/py-slice.py .
patch <py-slice.patch  # download the patch to the same folder prior to this command

              


---

### Post by raja.genupula on 2012-04-02
did you got solved then ?

---

### Post by waldherrvonbirnbaum on 2012-04-03
ja, works perfect now. 100 000 000 000 000 thanks to you!

---

