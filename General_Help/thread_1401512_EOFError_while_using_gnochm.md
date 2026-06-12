---
title: "EOFError while using gnochm"
date: 2010-02-08
forum: General Help
---

### Post by kcode on 2010-02-08
Hi,

This is the error I get after executing gnochm : ```

Traceback (most recent call last):
  File "/usr/bin/gnochm", line 1914, in <module>
    recent_list = pickle.load(open(path_rec, 'r'))
  File "/usr/lib/python2.5/pickle.py", line 1370, in load
    return Unpickler(file).load()
  File "/usr/lib/python2.5/pickle.py", line 858, in load
    dispatch[key](self)
  File "/usr/lib/python2.5/pickle.py", line 880, in load_eof
    raise EOFError
EOFError
```
It was working properly until I issued this command : ```

gnochm book_name.chm 2>/dev/null &
```

Googling was of no use.

Thanks

---

### Post by kcode on 2010-03-07
Getting on with xchm now.This is still unsolved.

---

