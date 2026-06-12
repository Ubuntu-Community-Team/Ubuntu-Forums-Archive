---
title: "vim command :r"
date: 2012-02-01
forum: General Help
---

### Post by conradin on 2012-02-01
Hi Knowledgeable forum users!
I have had several files Ive tried to import into another document using the vim command :r /home/somefilename.py
and got an error:
E484: Can't open file '/home/somefilename.py'

To overcome this problem for the moment I have been using the vim command
:r !cat someFilename.py which does work. But Im still not sure why im getting an error.

---

### Post by Dangertux on 2012-02-01
My guess would be instead of trying to read the file in it's trying to execute it, try removing the executable bit and see if it will read it just a guess, I'm not actually sure why this happens though.

Hope this helps.

---

### Post by Khayyam on 2012-02-02
conradin ...

I can only reproduce this if I stipulate the wrong filename:

```
% vim --version |head -1 |awk '{print $5}'
7.2
% vim test
:0read test.py # success!
:!chmod u+x test.py # execuable bit shouldn't matter as :r is much like 'cat > buff'
:0read test.py # success!
:0read TEST.py
E484: Can't open file TEST.py
```Just to be sure are 'somefilename.py' and 'someFilename.py' used in your examples the same file (case sensitive OS and all that)? Does tab completion on the filename also lead to the same outcome?

I'm pretty sure you passing the wrong filename. I can't see why ':!cat' would work and :r not, all that vim requires is that it has read permission to the file. 

HTH ..

---

