---
title: "personal task manager with recurring tasks?"
date: 2011-04-28
forum: General Help
---

### Post by sweetleaf on 2011-04-28
I'm looking for software recommendations for personal task management (todo lists).

**Requirements**

[LIST=1][*]Support recurring tasks. For example, I need to put out the recycling every other Thursday, and I need to pay bills on certain days of the month. This rules out [_[COLOR="DarkRed"]Evolution[/COLOR]_]("https://bugzilla.gnome.org/show_bug.cgi?id=200907").

[*]Support overdue tasks. If I forget to pay my bill on the right day, I need to be reminded. AFAIK, this rules out using calendar "events" to keep track of tasks--which is unfortunate, since events usually have good support for recurrence. 

[*]Privacy. I don't want to give all my family name & birthdate data to a cloud provider. This rules out [COLOR="DarkRed"]Google[/COLOR] and [COLOR="DarkRed"]Remember The Milk[/COLOR]. 

[*]GUI or ncurses management. Menu-driven interfaces like alpine and aptitude are fine. A simple, well-documented text file format (ala crontab or calendar) would be great. But I'm put off by pure CLI apps like [COLOR="DarkRed"]task(warrior)[/COLOR] that appear to require learning and remembering whole new command sets. 

[*]GUI notification. Something that runs in the background and pops up a tray icon or notification window when tasks come due, and then nags until they've been completed. (If the app has sufficiently rich CLI support, I suppose I could piece this together...)

[*]Import/export. Naturally.

[*]Light weight. [COLOR="DarkRed"]Lightning[/COLOR] sounds good, but it would require running Thunderbird all the time, which seems like overkill(?). [COLOR="DarkRed"]KDE's PIM[/COLOR] also sounds nice, but for better or for worse, I'm now using GNOME.[/LIST]

So far, I've found only one candidate: [COLOR="DarkRed"]osmo[/COLOR]. And maybe osmo is the best choice. But surely it isn't the only option out there! 

How do you manage your tasks? I'd love to hear any suggestions. Thanks!

---

### Post by nomnex on 2011-05-02
Yeah, that's far (by my standard) the best GUI PIM available, and it is Gnome dependency free. You want might look at Orage too, that's the Xfce PIM, while Osmo if the PIM commonly found on LXDE DE.

[http://www.kolumbus.fi/~w408237/orage/index.html]("http://www.kolumbus.fi/%7Ew408237/orage/index.html")

There's other CLI options (your post says GUI only), but they make sens if you start to use a CLI email client such as mutt.

[http://calcurse.org/](http://calcurse.org/)
or
[http://taskwarrior.org/projects/show/taskwarrior/](http://taskwarrior.org/projects/show/taskwarrior/)

---

### Post by tersogar on 2011-11-04
[FONT=Tahoma]Osmo Personal Organizer is just what I was looking for. :popcorn:

[/FONT]

---

### Post by nomnex on 2011-11-05
> **tersogar said:**
> [FONT=Tahoma]Osmo Personal Organizer is just what I was looking for. :popcorn:

[/FONT]
Do you know how to set recurring tasks in Osmo? it's not really intuitive. e.g. you have to mark to task as completed and click on the blue arrow icon to show the recurrence on the next due date.

---

### Post by tersogar on 2011-11-06
> **nomnex said:**
> Do you know how to set recurring tasks in Osmo? it's not really intuitive. e.g. you have to mark to task as completed and click on the blue arrow icon to show the recurrence on the next due date.
I don´t know what blue arrow you refer to, but when you set recurrent task  monthly for example: days - 30 / month - 0 and repeat 24 if 2 years are  needed,  you would get a warning that you can configure to your  preference.
 As soon as you complete that task, all that is require is  to mark done next time you see the warning or click done directly on  the task menu. After that, the next due dated will appear on the next  month and so on.

---

### Post by nomnex on 2011-11-06
> **tersogar said:**
> the next due dated will appear on the next  month and so on.

you got it right. all the recurring tasks won't show up in the calendar, and launching the next recurrence is a manual process.

---

### Post by tersogar on 2011-11-06
I´m happy with the fact that the task of the current month will be there  until is completed and only them the task will automatically appear on  the next due date. I pay my bills with osmo and is flawless

---

