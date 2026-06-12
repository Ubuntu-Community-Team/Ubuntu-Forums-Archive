---
title: "write script to rename selected files to md5checksum of them"
date: 2010-06-09
forum: General Help
---

### Post by margemoosh on 2010-06-09
I want to write a nautilus script so when i select some files and use this script on them all of them renamed to md5checksunm of that file!
because when i download some files from the internet they have same name but they're not the same so renaming them to their md5checksum will make them unique so i can move them to my archive folder without problems.
but i have no idea what is nautilus scripts syntax and how should i do that.
i know c++ c# if it helps;)

---

### Post by arsenic23 on 2010-06-09
Never messed with it myself, but this may help:
[http://www.linux.com/archive/feature/114134](http://www.linux.com/archive/feature/114134)

---

### Post by lavinog on 2010-06-09
```

#! /usr/bin/env python
import hashlib
import sys
import os

def get_md5(file):
    m = hashlib.md5()
    m.update(open(file, 'rb').read())
    return m.hexdigest()


if len(sys.argv)==1:
	print "need filenames"
	
for file in sys.argv[1:]:
	if os.path.exists(file):
		md5=get_md5(file)
		print '%s : %s'%(file,md5)
		os.rename(file,md5)
		
	else:
		print '%s does not exist'%file

```
save it as a file: md5_filerenamer.py
chmod it to be executable
```

chmod 744 md5_filerenamer.py

```
then execute it:
```

./md5_filerenamer.py *.JPG

```

It will rename the files (not make copies)
```


$ ./md5_filenamer.py *.JPG
IMGP5559.JPG : 3e12185af7171c95f5348b4272d1469e
IMGP5560.JPG : 0616281df9db0b3189daddded355ef99
IMGP5561.JPG : 639a970d748614af61b9ebcfe5c293b3
IMGP5562.JPG : 498d21b70ba791049cdc168819efb4b8
IMGP5563.JPG : 569ec87ae0016dc40b642ba971b7ca85
IMGP5564.JPG : 48151dc6546995d33edc1f2a5a3c6848

$ ls
0616281df9db0b3189daddded355ef99  569ec87ae0016dc40b642ba971b7ca85
3e12185af7171c95f5348b4272d1469e  639a970d748614af61b9ebcfe5c293b3
48151dc6546995d33edc1f2a5a3c6848  md5_filenamer.py
498d21b70ba791049cdc168819efb4b8

```

---

### Post by margemoosh on 2010-06-09
> **lavinog said:**
> ```

#! /usr/bin/env python
import hashlib
import sys
import os

def get_md5(file):
    m = hashlib.md5()
    m.update(open(file, 'rb').read())
    return m.hexdigest()


if len(sys.argv)==1:
    print "need filenames"
    
for file in sys.argv[1:]:
    if os.path.exists(file):
        md5=get_md5(file)
        print '%s : %s'%(file,md5)
        os.rename(file,md5)
        
    else:
        print '%s does not exist'%file

```save it as a file: md5_filerenamer.py
chmod it to be executable
```

chmod 744 md5_filerenamer.py

```then execute it:
```

./md5_filerenamer.py *.JPG

```It will rename the files (not make copies)
```


$ ./md5_filenamer.py *.JPG
IMGP5559.JPG : 3e12185af7171c95f5348b4272d1469e
IMGP5560.JPG : 0616281df9db0b3189daddded355ef99
IMGP5561.JPG : 639a970d748614af61b9ebcfe5c293b3
IMGP5562.JPG : 498d21b70ba791049cdc168819efb4b8
IMGP5563.JPG : 569ec87ae0016dc40b642ba971b7ca85
IMGP5564.JPG : 48151dc6546995d33edc1f2a5a3c6848

$ ls
0616281df9db0b3189daddded355ef99  569ec87ae0016dc40b642ba971b7ca85
3e12185af7171c95f5348b4272d1469e  639a970d748614af61b9ebcfe5c293b3
48151dc6546995d33edc1f2a5a3c6848  md5_filenamer.py
498d21b70ba791049cdc168819efb4b8

```


thanks a lot.
looks like i should learn python:)

---

