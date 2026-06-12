---
title: "Ubuntu 11.04, Chinese translation calendar/clock is broken"
date: 2011-10-02
forum: General Help
---

### Post by paopao on 2011-10-02
On a new laptop I installed Ubuntu 11.04, in English, and then made a separate account in which everything would be in Chinese.

However, I noticed something screwy with the clock and calendar

**First, the clock (this is minor)**
Normally, it might say, in English:
*Sun Oct 2 17:15:42*
but in Chinese it said:
*&#26085; 10&#26376; 2 17:15:42*

Why just &#26085;?  That's confusing.  It should say &#26143;&#26399;&#26085;, or at least give that as an option.  I remember earlier versions I could easily change this exact string because in English, I liked having *2011-10-02 17:15:42* instead, but they removed this option in 11.04 (or it's not done the same way before).

**Second, the calendar (this is major)**
When I click on the datetime, it'll display the calendar.  In English, it shows the long date:
*Sunday, 2 October 2011*
And then displays scroll options for the Month (*October*) then the year (*2011*).  It then shows a calendar with the days of the week abbreviated with Sunday as the first day of the week.

However, when I switch over to Chinese, it shows the long date as
*2011&#24180;10&#26376;2&#26085; Sunday*
Yes, Sunday, in English.
Then it shows the scroll options for the year (*2011*) and then the month (*October*).  At least it correctly gets that the year should be first and then the month; however, it spells out English months.  Additionally, when showing the days of the week it uses the abbreviations *in English* and starts the first day of the week as Sunday (which is not the case in Chinese, Monday is called &#26143;&#26399;&#19968;, or day one)

This is a serious flaw and probably a bug.  My only guess is that it had something to do with installing Ubuntu originally in English and then adding Chinese to add an account for a Chinese user.  That seems silly.

**Is there a way to manually define these fields?**  I'd also like to know that because I'd like to change the first day of the week to Monday, in English and also use ISO-8601 for the format for the clock, in English.

Thank you!

---

