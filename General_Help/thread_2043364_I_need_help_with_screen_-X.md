---
title: "I need help with screen -X"
date: 2012-08-16
forum: General Help
---

### Post by Zukaro on 2012-08-16
How do I make a command given with "screen -S name -p 0 -X stuff 'command'" put an enter after command in a shell script?

I've tried putting a \r and a \n after it, and also inside the brackets (but that doesn't work.  I've also tried ^M (which I'm told to use for this command to make it enter it rather than just leaving it typed) but that doesn't work unless this command is made through a terminal.

---

### Post by Zukaro on 2012-08-16
Nevermind; I was able to do ```
cat << eof > file
``` and enter my code there to make a shell script that could do what I needed.

---

