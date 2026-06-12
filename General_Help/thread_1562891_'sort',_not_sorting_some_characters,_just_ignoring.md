---
title: "'sort', not sorting some characters, just ignoring"
date: 2010-08-28
forum: General Help
---

### Post by Dayofswords on 2010-08-28
i used 'sort' to sort a 160k line file and looked though it and noticed this 

RS:HALP
RS HD
RSHD
RS:HELP
RS:HISTORY

File:Bovistrangler_tree.png
File:'bow_detail.png
File:Bow_emote_icon.PNG


not sure what you call it, but its like space and colons and apostrophe (maybe others) aren't being sorted, just skipped over to the next letter to sort. any ideas how to sort the colons and spaces?

also, how do i sort with lower case and capital in mind(lower first, capital after), the man page mentioned "-f, --ignore-case" to ignore the case, but it seems to be doing that already.

---

### Post by Vaphell on 2010-08-28
sort --help mentions that variable LC_ALL=C makes sort command sort by byte value, check that out

---

### Post by Dayofswords on 2010-08-28
tried that, output near the beginning changed some (like 15 blank new lines, which there should have been none in the file), but that parts i gave as an example stayed the same

---

