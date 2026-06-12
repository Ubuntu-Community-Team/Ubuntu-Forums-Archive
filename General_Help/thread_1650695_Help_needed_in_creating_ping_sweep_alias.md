---
title: "Help needed in creating ping sweep alias"
date: 2010-12-22
forum: General Help
---

### Post by veldhanas on 2010-12-22
Hi all,
         I am a linux newbie. i wanted to do a ping sweep in my network using a single command line. 

This is what i have tried.

1. Extracted the first 3 octets of my ip. Then tried to use that extracted info in a perl command to cycle upto 254 then piped that into fping command.

```
1. ifconfig -a | grep inet | head -1 | awk -F: ' { print $2 } ' | awk ' { print $1 } ' | awk -F. ' { printf "%d.%d.%d.",$1,$2,$3 } '

2. perl -e ' for (1..254) { print "10.108.32.$_\n" } ' | fing -q -a 2>/dev/null
```Here i want to use command 1 or the result of command 1 in the place of 3 octets of ip specified in command 2. I tried using alias for command 1 and tried to write a shell function to return the result. But because of improper quoting i couldn't complete this in a single command. 

Any help or suggestions highly appreciated.

---

