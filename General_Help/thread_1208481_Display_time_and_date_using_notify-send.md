---
title: "Display time and date using notify-send"
date: 2009-07-09
forum: General Help
---

### Post by ninopolis on 2009-07-09
Im still quite new to command line... 
But im wondering if there is a way that i could get the notify-send command to display the current time and/or date.
I have been playing around with the command already, but haven't figured out how to display anything other than static text.
Thank you! :)

---

### Post by sisco311 on 2009-07-09
```
#!/bin/bash

icon="/path/to/icon/file.png"
title="$(date +%H:%M)"
text="$(date +%d). $(date +%B) $(date +%Y), $(date +%A)"

notify-send -i $icon "$title" "$text"

```

[IMG]http://img216.imageshack.us/img216/4277/clock.png[/IMG]

---

### Post by VCoolio on 2009-07-09
I just figured that out this week :). You can also include the "date" commands between `  `  to have them executed before showing the notification, like this:

```
#!/bin/sh

notify-send -t 5000 -i /path/to/icon.png "`date +%H:%M`" "`date +%A` `date +%d`. `date +%B`       (`date +%Y` - Week `date +%U`)"
```

---

### Post by ninopolis on 2009-07-09
Thank you so much!!

---

