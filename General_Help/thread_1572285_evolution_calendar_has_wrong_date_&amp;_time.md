---
title: "evolution calendar has wrong date &amp; time"
date: 2010-09-10
forum: General Help
---

### Post by edzell on 2010-09-10
Ubuntu 10.04:
- Computer displays correct date & time.
- Evolution calendar preferences set to "use locale date & time"
- Evolution view for "today" is wrong; at 6.03 on Fri 10th it displays 12.30am on Sat 11th.
- Recurring item inserted to take place every Mon & Fri 9.30 am.
- In "today" view the item shows as occurring on Saturday 11th.
- In 3-day Fri-Sat-Sun view it's only there on Friday
- In 3-day Sat-Sun-Mon view it's there wrongly on Saturday and correctly on Monday

Thought I'd try reporting a bug, which I've never done before. Just got a message "Bug buddy is not installed."

???????????????

---

### Post by dcstar on 2010-09-11
> **edzell said:**
> Ubuntu 10.04:
- Computer displays correct date & time.
- Evolution calendar preferences set to "use locale date & time"
.........

That is only a format selection. Set the Time Zone selection in General-Time.

---

### Post by edzell on 2010-09-11
> **dcstar said:**
> That is only a format selection. Set the Time Zone selection in General-Time.

Selection was & is set to "Use System Time Zone."
Since latest (not the first) closing & reopening, with no other changes, calendar now abruptly shows correct time & date. Why not before I wonder.
Now the recurring event is on all the correct days, but at the wrong time; 2.30 am instead of 9.30.
By that I mean, on the day view it occupies the 2.30 time slot, and displays start time as 2.30 - but when opened for editing the start time shown is still 9.30 as originally entered. (This is similar to behaviour it was also previously showing, that I didn't mention in my first post.)
On the day view I can drag & drop it to the proper slot, but to fully correct the fault I'd have to do that for every day on which it occurs - indefinitely into the future - and I can't trust that it won't move randomly again, next time I close & open the calendar.

This program seems to be seriously flawed, at least on my computer.

---

### Post by edzell on 2010-09-11
Partly solved;
Somehow without my intention or noticing, "View time zone" had been selected for the event dialogue box AND the time zone showing there was UTC. Why it hadn't defaulted to my local time zone - PDST - I don't know. Corrected that & things seem OK. (Compounding my confusion, I had typed "9.30" in the summary field and that was showing in the day view although it was in the 2.30 slot.)

BUT

The "forever recurring" event that I entered for Mondays & Fridays keeps showing up on a single Saturday as well, although only in some views! It appears to be a separate event (recurrence options are greyed out) but if I delete it all the others get deleted with it.

I'm very close to giving up on Evolution and reverting to Calendarscope for Windows. Not all of its functions work under Wine but I know which ones and can do without them. I have a very old version but it's still the best calendar program I've ever found - not free but more than worth what I paid. None of the Linux ones I've tried suits me as well.

---

### Post by dcstar on 2010-09-11
> **edzell said:**
> 
.........
The "forever recurring" event that I entered for Mondays & Fridays keeps showing up on a single Saturday as well, although only in some views! It appears to be a separate event (recurrence options are greyed out) but if I delete it all the others get deleted with it.


If the Evolution Calendar file was migrated from an earlier version or has been corrupted in some way then this sort of thing can happen.

You can open the Evolution Calendar file in a text editor and see the structure of the various entries, sometimes manually removing any suspicious looking ones can make all the difference.

---

### Post by edzell on 2010-09-14
Wow, that's a long file and apart from not understanding a lot of it I have trouble finding the offending parts. How much of it could I delete if I wanted to "start from scratch?" What if I delete the whole thing? I can find no way of just deleting a calendar and starting a new one. I wouldn't want to un-&-reinstall evolution & maybe lose all my email data (and/or finding the calendar problem persisting.) Maybe keeping email software separate from calendars etc isn't such a bad idea.

I had korganizer installed at one time and I'm not certain that evolution isn't somehow getting tangled up with its remnants.

Thanks for your responses.

> **dcstar said:**
> If the Evolution Calendar file was migrated from an earlier version or has been corrupted in some way then this sort of thing can happen.

You can open the Evolution Calendar file in a text editor and see the structure of the various entries, sometimes manually removing any suspicious looking ones can make all the difference.

---

### Post by joho68 on 2010-09-15
I've actually seen this happen too recently on a new 10.04 install I've been fiddling with. On the laptop and at work, it looks sweet as could be with exactly the same settings. OTOH, I'm not sure I paid much attention to how the Calendar entries were displayed on those two computers until a few days after I had set them up.

There are quite a few annyong things with Evolution, but in most cases, I think the Calendar handling works pretty good.

---

### Post by dcstar on 2010-09-15
> **edzell said:**
> Wow, that's a long file and apart from not understanding a lot of it I have trouble finding the offending parts. How much of it could I delete if I wanted to "start from scratch?" What if I delete the whole thing? I can find no way of just deleting a calendar and starting a new one.


Simply create a new Calendar and right-click to delete any unwanted ones. All of this is right there and I don't really understand the problem.

---

### Post by edzell on 2010-09-15
> **dcstar said:**
> Simply create a new Calendar and right-click to delete any unwanted ones. All of this is right there and I don't really understand the problem.

Thanks for the tip - you seem to have understood that part just fine. I was looking for delete calendar in the menus. Pity it's not there.

---

### Post by edzell on 2010-09-20
> **dcstar said:**
> Simply create a new Calendar and right-click to delete any unwanted ones. All of this is right there and I don't really understand the problem.

Sounded simple till I tried it. The default calendars called "Personal" and "Birthdays & Anniversaries" have the delete option greyed out. 

But under the Actions menu there's a "Purge" option. Won't let you delete a calendar but you can render it blank.

---

