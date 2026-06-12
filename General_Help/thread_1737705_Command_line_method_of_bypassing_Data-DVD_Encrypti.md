---
title: "Command line method of bypassing Data-DVD Encryption?"
date: 2011-04-23
forum: General Help
---

### Post by Alaric on 2011-04-23
Hey guys,

I'm trying to backup my old PC games so that I can finally banish their CDs to the attic once and for all.  I've just been using the DD command to grab iso's of my games so far, while keeping their keys in a text file (see the DD command below).  However, I just hit my C&C collection and I'm having some problems with some of the newer games like Renegade and Yuri's Revenge.  I think they must be copy protected or something.  4 of my last discs have stopped copying at exactly 1.7MB (3 seperate DVD drives, 2 IDE, 1 USB enclosed). Can you guys think of anything else that will cause DD to fail at this location?  Any ideas?  I'd prefer it to be a command line option, as I'm trying to make things go as quickly as possible.  Here's the command I've been using.  

```
for x in 0 1 2; do 
[INDENT]name=$(volname /dev/sr$x | sed 's/ *//g');
echo $name ;
dd if="/dev/sr$x" of="./${name/ /}.iso" && eject "/dev/sr$x" &[/INDENT]
done
```

---

### Post by Alaric on 2011-04-23
Bump

---

