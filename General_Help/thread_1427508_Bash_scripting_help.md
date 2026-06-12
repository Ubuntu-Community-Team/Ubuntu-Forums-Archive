---
title: "Bash scripting help"
date: 2010-03-11
forum: General Help
---

### Post by djbushido on 2010-03-11
Well, I'm working with some mp3 files that have a forwardslash - "/" in the tag, such that I can't create a directory with that in its name. Is there a way to replace that with sed? Like `sed s/\//|/g` which attempts to replace the "/" character with "|". Am I doing this the right way?

---

### Post by sisco311 on 2010-03-11
yes you can pipe the command which prints the tag in sed:
```
whatever | sed 's/\//-/g'
newname="$(whatever | sed 's/\//-/g')"
```
or if you store the tag in a variable you can try something like:
```
file=file/name/1.mp3
echo ${file//\//-}
```[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_10_03.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_10_03.html)

---

### Post by djbushido on 2010-03-11
That worked, thank you!

---

