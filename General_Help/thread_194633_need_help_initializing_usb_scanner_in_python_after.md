---
title: "need help initializing usb scanner in python after upgrade to dapper"
date: 2006-06-11
forum: General Help
---

### Post by henry.tx on 2006-06-11
I have a python script that scans documents that I was using in Breezy (with no problems), but has stopped working after I upgraded to Dapper.  The problem is with the initialization of the scanner, specifically:

scanner = sane.open(sane.get_devices()[0][0])

causes a segmentation fault.  "sane.get_devices()" returns "[('plustek:libusb:001:003', 'Canon', 'N1240U/LiDE30', 'USB flatbed scanner')]".  So the sane module seems to be seeing the scanner just fine.  Also, the scanner works fine with XSane.

Thanks in advance for any help.

---

### Post by mmarshall on 2006-06-15
Are you sure you are calling sane.init() first?  I had that problem not too long ago.

MWM

---

### Post by henry.tx on 2006-06-15
Thanks for the reply.  Yes, I'm definitely doing sane.init().  (I think that sane.get_devices() would not work otherwise?)

A helpful person over at python-forums.org suggests that I recompile the .so file that python is importing.  I see that sane.py imports _sane.so (found in /usr/lib/python2.4/site-packages), but I don't know where the source code for this file would be, or even what it is (C or C++, perhaps?).  For example, there is no "python2.4-imaging-sane-dev" package.

Any ideas?

---

### Post by mmarshall on 2006-06-15
It's included in the Sane/ directory in the PIL source distribution, which you can get here:
[http://effbot.org/downloads/Imaging-1.1.5.tar.gz](http://effbot.org/downloads/Imaging-1.1.5.tar.gz)
(Note that it has it's own setup.py, separate from PIL.)

You're right about get_devices not working before init.  Now that I think of it, I can't remember how I was getting segfaults.  I think is was something with the order that I was calling functions or some other side-effect.  Can you open the interactive interpreter and do "import sane; sane.init(); sane.open(sane.get_devices()[0][0])" ?

BTW, I ended up just calling the scanimage program as a subprocess.  That way I could get scan progress information, as well as ADF support.  I can post the twisted protocol class I wrote if you want.  

Or if your program is non-interactive just use something from the subprocess module.

MWM

---

### Post by henry.tx on 2006-06-15
> **mmarshall]Can you open the interactive interpreter and do "import sane said:**
> [0])" ?
Yes - issuing the script's commands step-by-step in the interactive interpreter is how I figured out that I was getting a seg fault.  Everything goes fine with that sequence of commands until the sane.open(sane.get_devices()[0][0]) command, which results in the seg fault.

[QUOTE=mmarshall]BTW, I ended up just calling the scanimage program as a subprocess.  That way I could get scan progress information, as well as ADF support.  I can post the twisted protocol class I wrote if you want.[/QUOTE]
Well, thanks, but I not sure it would do me much good.  I don't really know the meaning of what your are describing, as I'm strictly an amature at this stuff.  But I guess there is some chance that I would be able to figure it out and use it someday...

[QUOTE=mmarshall]It's included in the Sane/ directory in the PIL source distribution, which you can get here:
[http://effbot.org/downloads/Imaging-1.1.5.tar.gz](http://effbot.org/downloads/Imaging-1.1.5.tar.gz)
(Note that it has it's own setup.py, separate from PIL.)[/QUOTE]
Thanks!  Now hopefully I can figure out how to do the recompiling.

---

### Post by mmarshall on 2006-06-15
Here, I'll write you a quick example.

For scanning an image and saving it directly to a file:
```
import subprocess
result_code = subprocess.call('scanimage > file.pnm', shell=True)
```

That will run 'scanimage > file.pnm' just as if you ran it in a shell.

I don't think that this would work under Windows, but who cares? ;)

MWM

---

