---
title: "unavailable enviroment variable ATISTREAMSDKROOT"
date: 2011-01-25
forum: General Help
---

### Post by ~Middle on 2011-01-25
Hello, 

I am trying to install a program with not much documentation. When i try to build it i get this error:

sudo ./setup.py build
[sudo] password for middle: 
unavailable enviroment variable ATISTREAMSDKROOT
Traceback (most recent call last):
  File "./setup.py", line 35, in <module>
    CALPP_INC_DIR = os.environ['ATISTREAMSDKROOT']
  File "/usr/lib/python2.6/UserDict.py", line 22, in __getitem__
    raise KeyError(key)
KeyError: 'ATISTREAMSDKROOT'


I have tried hard to solve this but i am really desperate!

Thanks

---

### Post by Smart Viking on 2011-01-25
We would need to know what program it is, so we can try it.

---

### Post by ~Middle on 2011-01-25
Well it is a program called Pyrit - It is designed for the wireless pentester to use their GPU to aide in the speed of cracking WPA keys - however it is rather experimental i think. I didn't mention it as i was unsure of the forums attitudes to this type of software. 

[http://www.backtrack-linux.org/forums/tutorial-ed-howto/31742-ati-driver-stream-opencl.html](http://www.backtrack-linux.org/forums/tutorial-ed-howto/31742-ati-driver-stream-opencl.html)

^ This is a guide relating to what i am trying to do (Install the cal++ add on)

And here is about Pyrit:

[http://code.google.com/p/pyrit/](http://code.google.com/p/pyrit/)

Thanks a million!

---

### Post by ~Middle on 2011-01-25
bump, this is really important!

---

