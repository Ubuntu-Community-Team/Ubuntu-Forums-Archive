---
title: "Python may not be configured for Tk"
date: 2012-10-03
forum: General Help
---

### Post by kaurie on 2012-10-03
I am using Ubuntu 12.04 64 bit version as a new install. (The upgrade from 11.10 crashed so I had to start again)

I am very puzzled I wanted to learn to use tkinter in Python and so used a simple code from
 [http://www.pythonware.com/library/tkinter/introduction/hello-tkinter.htm](http://www.pythonware.com/library/tkinter/introduction/hello-tkinter.htm)
```
# File: hello1.py
from Tkinter import *
root = Tk()
w = Label(root, text="Hello, world!")
w.pack()
root.mainloop()
```

when running this I got the error message [HTML]File "hello1.py", line 2, in <module>
    from Tkinter import *
  File "/usr/local/lib/python2.5/lib-tk/Tkinter.py", line 38, in <module>
    import _tkinter # If this fails your Python may not be configured for Tk[/HTML]

I have package tk python-tk 2.7.3-1ubuntu1 intalled
but my python is Python 2.5.4.

Obviously I have done somethink very stupid - Does anyone know what I have done

---

### Post by kaurie on 2012-10-03
More info

I have virtual box running a virtual machine. ubuntostudio-12.04-dvd_amd64.iso

I have just tested the process by usding this box and 
[LIST=1]
[*]I intalled python-tk 
[*]I used the same program Hello.py
[/LIST]

It worked BUT the python was Python 2.7.3 (default Aug 1 2012 05:14:39)

So I guess the question is how do I install this python on my main box. I gather that this is dangerous as the machine uses python for the operating system.

---

### Post by kaurie on 2012-10-03
OK I think that I have almost found the problem.

I was actually trying to install a package that had Python 2.5.4 and my guess is that I somehow compiled this package and that now I am linked to the wrong Python.

Any advice on how to unscramble the egg would be greatly appreciated

---

### Post by Favux on 2012-10-03
Have you checked in /usr/bin/python to see where your python links are pointing?
```
ls -l /usr/bin/python*
```
In your Hello.py just change the 'python' in the shebang line to point to the correct python version symlink.  Which you might have to make.  Should be able to then coexist with 'python' pointing to 'python2.7'.

---

### Post by kaurie on 2012-10-05
Thanks very much for the reply. It was very much appreciated but I am still failing to understand my stupidity.

I ran ls -l /usr/bin/python*

```
lrwxrwxrwx 1 root root       9 Jul 10 07:39 /usr/bin/python -> python2.7
lrwxrwxrwx 1 root root       9 Jul 10 07:39 /usr/bin/python2 -> python2.7
-rwxr-xr-x 1 root root 2989480 Aug  1 15:40 /usr/bin/python2.7
-rwxr-xr-x 1 root root    1652 Aug  1 15:40 /usr/bin/python2.7-config
-rwxr-xr-x 1 root root 6317954 Aug  1 14:55 /usr/bin/python2.7-dbg
-rwxr-xr-x 1 root root    1656 Aug  1 15:40 /usr/bin/python2.7-dbg-config
lrwxrwxrwx 1 root root      16 Apr 18 03:20 /usr/bin/python2-config -> python2.7-config
lrwxrwxrwx 1 root root      13 Apr 18 03:20 /usr/bin/python2-dbg -> python2.7-dbg
lrwxrwxrwx 1 root root      20 Apr 18 03:20 /usr/bin/python2-dbg-config -> python2.7-dbg-config
lrwxrwxrwx 1 root root      16 Apr 18 03:20 /usr/bin/python-config -> python2.7-config
lrwxrwxrwx 1 root root      13 Apr 18 03:20 /usr/bin/python-dbg -> python2.7-dbg
lrwxrwxrwx 1 root root      20 Apr 18 03:20 /usr/bin/python-dbg-config -> python2.7-dbg-config
``` 

so far so good and then modified hello.py to hello1.py
```
#!/usr/bin/python2.7
# This is the shebang line 
# File: hello1.py
from Tkinter import *
root = Tk()
w = Label(root, text="Hello, world!")
w.pack()
root.mainloop()
```

So far so good but then when I ran it

```
lpa@CLINO:~/SWORK/Src/Python/Tkinter$ python hello1.py 
Traceback (most recent call last):
  File "hello1.py", line 5, in <module>
    from Tkinter import *
  File "/usr/local/lib/python2.5/lib-tk/Tkinter.py", line 38, in <module>
    import _tkinter # If this fails your Python may not be configured for Tk
ImportError: No module named _tkinter
lpa@CLINO:~/SWORK/Src/Python/Tkinter$ 
```

---

### Post by Favux on 2012-10-05
Since you installed Python 2.5.4 where is the binary?  According to your /usr/bin there is no Python 2.5.  The Tkinter module for it should have been installed when you installed 2.5 and seeing /usr/local/lib/python2.5 seems to confirm that.  You should be able to use **locate** to find it if you don't know.  Given where its Tkinter is I'll guess /usr/local/bin.  If so check that location for the symlinks that are there.

So what you want to do is modify your shebang line to say python2.5 not python or python2.7.  And if need be add a symlink in /usr/bin or /usr/local/bin or both to point to the correct executable.
```
sudo ln -s /path/to/python2.5.4 binary /usr/bin/python2.5
```

When you run **locate lib-tk** do you also see **/usr/lib/python2.7/lib-tk**?

---

