---
title: "Installing Mozilla Thunderbird, error (libstdc++.so.5"
date: 2009-11-05
forum: General Help
---

### Post by IBuntu.biz on 2009-11-05
koala@Karmic-Kola:/usr/local/lib/thunderbird$ ./thunderbird
./thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Running Ubuntu 9.10 Karmic-Koala (however you spell that, haha) 64bit

I ran the tar.gz in my own directory and then read on here that it would only work if it was in /usr/local/lib  ... somebody please help? I'd like to install it without the install script that is going around.

Also, do you always have to use sudo to unpack a tar in a new directory? EX. tar -xvzf thunderbird-2.0.tar.gz -C /usr/local/lib 

and what is the -C in that command.. couldn't get it to work without '-C' 

I'm getting more used to the terminal but still confused about some things! Thanks for the help!

Nick

---

### Post by IBuntu.biz on 2009-11-05
Frustrated so I'm just going to go use Evolution, but if somebody could still answer my questions that would be great ):P


also, using the mv command, does that mv a file completely, or does it rename/copy it to new directory

---

### Post by [r4] on 2009-11-25
Why won't you use [a tutrial](http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000)? It comes pretty handy, just verified that myself.

Regarding your qestion about mv command: it moves files physically between partitions and just re-links them (their names or i-nodes if you wish) if the move is to be made in the same partition.

---

