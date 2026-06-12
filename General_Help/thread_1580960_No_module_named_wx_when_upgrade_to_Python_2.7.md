---
title: "No module named wx when upgrade to Python 2.7"
date: 2010-09-24
forum: General Help
---

### Post by acrocephalus on 2010-09-24
Hello,
I've just upgraded to Python 2.7 but when I try to run a program that imports the wx I get this error
```
Import error: No module named wx
```
I guess it has an easy solution, but I cannot figure it out. Can anyone help?
Cheers!

Dani

---

### Post by vinnie1 on 2011-05-19
I'd like to know this as well.

I found a simple video tutorial on Python, and as usual there's a problem at the start .

This is my code:

```

#!/usr/bin/python
import wx
app = wx.PySimpleApp()
frame = wx.Frame(none,-1,"Hello World")
frameShow(1)
app.MainLoop()

```


The error i Get
Traceback (most recent call last):
  File "H:/Python/helloWorld.pyw", line 2, in <module>
    import wx
ImportError: No module named wx

Probably something simple.

---

