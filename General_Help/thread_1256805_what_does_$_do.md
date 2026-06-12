---
title: "what does $? do"
date: 2009-09-03
forum: General Help
---

### Post by divinequran on 2009-09-03
Hi,

I have written a script to ping IP's and store the result in a file. the script works fine and i cant understand What does( $? != ) means in the script. Please help.

```
ping -c 3 $i
if [[ [COLOR="Red"]$? ![/COLOR]= 0 ]]; then
```
 echo "Unavailable";

I want to know what[COLOR="Red"] $?[/COLOR] variable means

---

### Post by ManDay on 2009-09-03
Flame me if I'm wrong, I don't have much of a clue of bash scripting myself, but I think $? contains the result from the last operation.

---

### Post by DaithiF on 2009-09-03
it contains the exit status from the preceding command.  typically $? of 0 indicates success, while a non-zero value means a failure or error of some kind.  In this case, a failure to get a response to the ping.

---

### Post by divinequran on 2009-09-12
Hi,

  Thanks, where I can find or learn about such operations, I searched it but I cant find. Any tutorial which explains more about it?

---

### Post by yabbadabbadont on 2009-09-12
Advanced bash shell scripting guide: [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
Beginning shell scripting guide: [http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)
Beginning bash shell scripting guide: [http://www.linuxconfig.org/Bash_scripting_Tutorial](http://www.linuxconfig.org/Bash_scripting_Tutorial)

---

### Post by divinequran on 2009-09-13
Hi,

  Thanks a lot, really some of the some of the useful links. Thanks again.

---

### Post by geirha on 2009-09-14
I recommend this guide. [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

