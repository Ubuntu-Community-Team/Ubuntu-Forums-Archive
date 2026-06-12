---
title: "What does this error mean? I'm trying to install 'lives'"
date: 2010-05-27
forum: General Help
---

### Post by tjw09003 on 2010-05-27
when running :sudo apt-get install lives

This is the last three lines of output,

> 
After this operation, 74.1MB disk space will be freed.
Do you want to continue [Y/n]? y
E: Internal Error, Could not perform immediate configuration (2) on mountall



---

### Post by jerrrys on 2010-05-27
this may help

[http://www.google.com/search?client=ubuntu&channel=fs&q=Internal+Error%2C+Could+not+perform+immediate+configuration+%282%29+on+mountall&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=Internal+Error%2C+Could+not+perform+immediate+configuration+%282%29+on+mountall&ie=utf-8&oe=utf-8)

---

### Post by tjw09003 on 2010-05-27
funny... if you click any of the links, none of them have any useful advice. Like your asswipe of an answer.

---

### Post by jerrrys on 2010-05-27
thankyou :)

---

### Post by tjw09003 on 2010-05-27
lol, my bad. I'm bitchy today, updated to Lucid and nothing but problems...

One you might be able to help with. When I try to start thunderbird it tells me it can't open the file libmozjs.so because it doesn't exist

The problem is the file is in the directory, it does exist???

---

### Post by tjw09003 on 2010-05-27
> 
twalczak@twalczak-laptop:~/Downloads/thunderbird$ ./thunderbird-bin
./thunderbird-bin: error while loading shared libraries: libmozjs.so: cannot open shared object file: No such file or directory
twalczak@twalczak-laptop:~/Downloads/thunderbird$ 
But the file does exist
> twalczak@twalczak-laptop:~/Downloads/thunderbird$ ls libmoz*
libmozjs.so
twalczak@twalczak-laptop:~/Downloads/thunderbird$ 


---

### Post by plasticity on 2010-06-01
I had this error, and the reason was a different ubuntu version listed in my 
/etc/apt/sources.list

and my 
/etc/lsb-release

by changing the sources from "Lucid" to "Karmic" that fixed the problem and allowed a succesful install. You can probably tell that this could be caused by an incomplete upgrade, where only the release name was changed but not the actual distribution.

I used vi to open the sources, and the vi command:
:%s/lucid/karmic/

to replace all instances and then 
apt-get clean
apt-get update

---

### Post by plasticity on 2010-06-01
> **jerrrys said:**
> this may help

[http://www.google.com/search?client=ubuntu&channel=fs&q=Internal+Error%2C+Could+not+perform+immediate+configuration+%282%29+on+mountall&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=Internal+Error%2C+Could+not+perform+immediate+configuration+%282%29+on+mountall&ie=utf-8&oe=utf-8)
The reason this is not a good idea is because google links to these forums, so you're not only wasting the person asking's time, but also those that get here from google.

---

