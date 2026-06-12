---
title: "Pidgin chat history"
date: 2011-05-09
forum: General Help
---

### Post by tekal on 2011-05-09
hello,
i've recently installed pidgin via the Ubuntu Software Center. Unfortunnately it is lacking a "chat history" just like for example "Trillian" on Windows. Is there any IM-prog on Ubuntu which saves all conversations with any contact into files? (Just like Trillian on windows)

---

### Post by Krytarik on 2011-05-09
Maybe I don't get exactly what you are meaning, but Pidgin *does* save conversations into "~/.purple/logs", into the respective subdirectories for the protocols/contacts, with one log file per conversation session.

Greetings.

---

### Post by Rasa1111 on 2011-05-09
Yep, Pidgin does save them, unless you tell it not to.

---

### Post by tekal on 2011-05-10
nice that's exactly what i was looking for.

---

### Post by curtissthompson on 2011-05-11
> **Krytarik said:**
> Maybe I don't get exactly what you are meaning, but Pidgin *does* save conversations into "~/.purple/logs", into the respective subdirectories for the protocols/contacts, with one log file per conversation session.

Greetings.

It no longer seems to put a log folder in the ~/.purple directory.  I can't seem to find the log directory either (and I do have it set to save my Pidgin chat logs).

Any help would be greatly appreciated, thanks!

---

### Post by Krytarik on 2011-05-11
> **curtissthompson said:**
> It no longer seems to put a log folder in the ~/.purple directory.  I can't seem to find the log directory either (and I do have it set to save my Pidgin chat logs).
Can you access the logs through Pidgin's GUI then?
Are there any logs saved so far?

I'm not running Natty, so I can't check it for myself. But if the answer to the above stated questions is 'Yes', do a date/time-based search after the next logged conversation.

---

### Post by curtissthompson on 2011-05-11
> **Krytarik said:**
> Can you access the logs through Pidgin's GUI then?
Are there any logs saved so far?

I'm not running Natty, so I can't check it for myself. But if the answer to the above stated questions is 'Yes', do a date/time-based search after the next logged conversation.

The answer is yes. I'm able to see the logs through Pidgin's log viewer, just not able to find the actual directory.

By date/time-based search, do you mean a search of the file system? If so, how do I search by recency?

---

### Post by Krytarik on 2011-05-11
> **curtissthompson said:**
> 
By date/time-based search, do you mean a search of the file system? If so, how do I search by recency?
Exactly. You can use the tool "Search for Files..." for that, choose "Select more options" there. But the search is a bit rough since the least possible time frame is 1 day.

I use the Windows tool "Total Commander" to search more precisely. (If someone know of a native Gnome tool for exact those feature, I'd be glad. GUI, please.)

---

