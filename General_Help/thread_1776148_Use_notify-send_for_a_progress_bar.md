---
title: "Use notify-send for a progress bar?"
date: 2011-06-05
forum: General Help
---

### Post by slooksterpsv on 2011-06-05
I've been able to do this before, sadly I didn't back-up the script, but I swear there was a way to use notify-send and have it show a progress bar

I thought it was something like:

notify-send -h int:value:*some_number* 

or something like that, but that doesn't work. I want to be able to make a script where it shows a certain percentage in a bar like

[==========________________]

And maybe after it looks like
[===============___________]

But not text based like that. I'm using Ubuntu 11.04 64-bit, I have libnotify-bin and notify-osd installed. Unless it's broke is the only thing I can figure.

---

### Post by sisco311 on 2011-06-06
Try:
```

notify-send " " -i $icon -h int:value:$number -h string:synchronous:volume
```

---

### Post by slooksterpsv on 2011-06-06
> **sisco311 said:**
> Try:
```

notify-send " " -i $icon -h int:value:$number -h string:synchronous:volume
```

Nope =( just shows white text and black background:
e.g.:

```

#a bash script
number=55
notify-send "test" -h int:value:$number -h string:synchronous:volume


```

See attached pic:

---

### Post by sisco311 on 2011-06-06
That looks like the standard notification bubble. Remove the notification-daemon package and make sure that notify-osd is installed. You also have to specify an icon.

---

### Post by slooksterpsv on 2011-06-07
> **sisco311 said:**
> That looks like the standard notification bubble. Remove the notification-daemon package and make sure that notify-osd is installed. You also have to specify an icon.

Removing notification-daemon worked - funny how if notification-daemon is installed you don't have to specify an icon, and when it's not installed you do. Weird.

---

### Post by slooksterpsv on 2011-06-07
Geeze, new issue, now the expire time doesn't work. If I set it to like 250 ms it stays up for 8-10 seconds; even if I do just 1 it stays up that mount, even trying to just set for 1000ms makes it set to 8-10 (some where around there). I take it it's bugged =( ??

Meh got a PPA to do it hehe

---

