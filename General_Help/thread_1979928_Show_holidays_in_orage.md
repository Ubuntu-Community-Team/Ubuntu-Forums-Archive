---
title: "Show holidays in orage"
date: 2012-05-14
forum: General Help
---

### Post by alfh on 2012-05-14
Is there a way to import and show holidays in Orage calendar?

I noticed this feature when trying out kubuntu (which was painfully slow on my machine, though looking pretty!). I'm on xubuntu now and want this feature. Do I have to install the kde calendar (I hope not!)?

Thankful for any and all input!

---

### Post by mike555 on 2012-05-14
You can go here;
[http://www.calendarlabs.com/ical-calendar-holidays.php](http://www.calendarlabs.com/ical-calendar-holidays.php)
 and download the .ics file , then click on it to open in orage.......

---

### Post by LewisTM on 2012-05-14
Deleted

---

### Post by JKyleOKC on 2012-05-14
After you download the ICS file from the link that mike555 posted above, open the Orage calendar, pull down the File menu, and select Exchange Files. That gets you a dialog with three tabs; select the Foreign Files tab. Click its Browse button to find and select the downloaded ICS file, then click the Add button. The holidays will now appear as scheduled events -- it's just that simple!

Thanks a lot to Mike for posting the link; I just installed the holidays to improve my calendar, which is why I'm posting this step-by-step tip since I had a bit of searching to do to find out how it's done...

---

### Post by alfh on 2012-05-15
mike555 and JKyleOKC, thanks a lot!

Just a bummer that there are no Norwegian holidays on the site :(

Will keep looking and eventually post my solution here.

---

### Post by alfh on 2012-05-15
Well, I'm finding the Norwegian holidays at [http://icalshare.com/calendars/2023]("http://icalshare.com/calendars/2023"), but firefox insists I open the .ics file with an application. Right-click - > save link as... doesn't let me download to disk.

Just having firefox open orage doesn't help as the .ics file seemingly isn't read.

Again I feel like missing something obvious :confused:

Still thankful for input!

---

### Post by LewisTM on 2012-05-15
That's because it's a webcal:// address.
I found if you just replace it with http:// it will download
[http://ical.mac.com/bjorkheim/Norske%20helligdager.ics](http://ical.mac.com/bjorkheim/Norske%20helligdager.ics)

Cheers!

---

### Post by alfh on 2012-05-18
Thank you, LewisTM! On to next challenge:

It looks like Orage is duplicating "all day"-entries. The Norwegians are celebrating Constitution Day on may 17th, this event show up on the 18th as well.

I've tried with a number of .ics's I found here and there, and each is giving the same (annoying!) result

---

### Post by alfh on 2012-05-18
I tried importing the data to see if it made any difference, kind of against the advice from JKyleOKC (use the foreign files tab, he said!).

Now my calendar is full of duplicate entries and I wonder if I have to delete them manually? Actually I'd rather reset the entire calendar and re-enter my few events...

Thankful for your input, folks!

---

### Post by Vaphell on 2012-05-18
look for a hidden directory with program settings, programs usually store their config in home or in .config. Wiping it should restore default settings.

edit: it's in $HOME/.config/orage

---

### Post by JKyleOKC on 2012-05-18
Here's what is in the U.S. holidays file for New Year's Day:
```
BEGIN:VEVENT
DTSTART;VALUE=DATE:20110101
DTEND;VALUE=DATE:20110102
DTSTAMP:20111213T124028Z
UID:7a6db67f3edff4729956c47ec@calendarlabs.com
CREATED:20111213T123901Z
DESCRIPTION:Visit http://www.calendarlabs.com/holidays/ to know more about New Year's Day and for any other calendar needs.
LAST-MODIFIED:20111213T123901Z
LOCATION:
SEQUENCE:0
STATUS:CONFIRMED
SUMMARY:New Year's Day
TRANSP:TRANSPARENT
END:VEVENT

```Note that the "DTEND" value is January 2. However in my installation, it shows only for January 1. You might try editing the file with any text editor (mousepad is what I use here but I believe that 12.04 uses leafpad instead) to change the DTEND to be the same day as the start, and see whether that changes things...

I also discovered that each of these "VEVENT" entries in the ICS file is for a single day; they do not recur the next year. My file has the holidays for 2011 and 2012 but none for 2013 or later years. This is the best reason I know **NOT** to import the file, but rather to treat it as a foreign file. Importing it will make it difficult to erase obsolete entries in the main calendar file; a foreign file can be replaced and the old data will vanish.

---

### Post by Vaphell on 2012-05-18
i looked at the file mentioned earlier and recurring holidays seem to have additional field

```
BEGIN:VEVENT
SEQUENCE:8
DESCRIPTION:Arbeidsdag
UID:024C68EE-AD93-48F7-942A-F97B48389CAE
TRANSP:OPAQUE
DTSTART;VALUE=DATE:20070508
DTSTAMP:20070520T181604Z
SUMMARY:*Frigjøringsdag 1945
CREATED:20080916T121403Z
DTEND;VALUE=DATE:20070509
**RRULE:FREQ=YEARLY;INTERVAL=1**
END:VEVENT
```

---

### Post by alfh on 2012-05-21
> **JKyleOKC said:**
> Here's what is in the U.S. holidays file for New Year's Day:
```
BEGIN:VEVENT
DTSTART;VALUE=DATE:20110101
DTEND;VALUE=DATE:20110102
DTSTAMP:20111213T124028Z
UID:7a6db67f3edff4729956c47ec@calendarlabs.com
CREATED:20111213T123901Z
DESCRIPTION:Visit http://www.calendarlabs.com/holidays/ to know more about New Year's Day and for any other calendar needs.
LAST-MODIFIED:20111213T123901Z
LOCATION:
SEQUENCE:0
STATUS:CONFIRMED
SUMMARY:New Year's Day
TRANSP:TRANSPARENT
END:VEVENT

```Note that the "DTEND" value is January 2. However in my installation, it shows only for January 1. You might try editing the file with any text editor (mousepad is what I use here but I believe that 12.04 uses leafpad instead) to change the DTEND to be the same day as the start, and see whether that changes things...

I also discovered that each of these "VEVENT" entries in the ICS file is for a single day; they do not recur the next year. My file has the holidays for 2011 and 2012 but none for 2013 or later years. This is the best reason I know **NOT** to import the file, but rather to treat it as a foreign file. Importing it will make it difficult to erase obsolete entries in the main calendar file; a foreign file can be replaced and the old data will vanish.

I'm still struggling to determine if this problem has to do with my specific setup, or if the problem resides with Orage, or if the culprit is the ics file.

You say that in your installation "it shows only for January 1" while in mine it also shows for January 2. And, the preview of the calendar at [http://icalshare.com/calendars/2023]("http://icalshare.com/calendars/2023") shows events spanning 2 days. It indicates maybe the ics file?

---

### Post by JKyleOKC on 2012-05-21
You may find the page at [http://en.wikipedia.org/wiki/ICalendar](http://en.wikipedia.org/wiki/ICalendar) helpful; it describes the format of the calendar files and shows how to set the start and end dates to include specific minutes in addition to days. Setting the start to time 000000 and the end to 235959 of the same day, with your local timezone value, should force the display to just a single day...

---

### Post by alfh on 2012-05-22
Thanks again for replying.

So it looks like the fault lies, at least partly, with ics files I've found. Those DTSTART and DTEND tags should have the same date.

But if I try to edit one of those events with Orage, it shows the event as a one day, starting and ending on the same date. Yet the event will show up over two days. :-k  I guess that means there's something fishy with my orage installation as well.

Anyway, for now I'm just gonna let the subject rest for a while. Thanks for all the input, folks!

---

### Post by jcoles on 2012-06-02
> **alfh said:**
> Thank you, LewisTM! On to next challenge:

It looks like Orage is duplicating "all day"-entries. The Norwegians are celebrating Constitution Day on may 17th, this event show up on the 18th as well.

I've tried with a number of .ics's I found here and there, and each is giving the same (annoying!) result

The duplication of All Day entries is a bug. It is fixed in version 4.8.3.

---

### Post by jcoles on 2012-06-02
> **Vaphell said:**
> look for a hidden directory with program settings, programs usually store their config in home or in .config. Wiping it should restore default settings.

edit: it's in $HOME/.config/orage

Some Orage files are stored in ~/.local/share/orage
The main calendar file, orage.ics, is there by default.

---

### Post by alfh on 2012-06-04
> **jcoles said:**
> The duplication of All Day entries is a bug. It is fixed in version 4.8.3.

Thanks a lot for this piece of info!

Would you also know where it's possible to find 4.8.3? I have currently 4.8.1 installed, it's the one I can find in software center. And a few searches provides me only with older links, like here: [http://www.kolumbus.fi/~w408237/orage/]("http://www.kolumbus.fi/~w408237/orage/") the latest download is 4.7.5 or pages with no links, like here: [http://www.xfce.org/projects]("http://www.xfce.org/projects")

All the best!

---

