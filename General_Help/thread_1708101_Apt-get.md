---
title: "Apt-get"
date: 2011-03-16
forum: General Help
---

### Post by antaios256 on 2011-03-16
Starting this week im finding that my computer will randomly start to run high CPU and using TOP  i find that its the apt-get process thats running it up at 100% (please note that top will show processes up to 800% i7quad with turbo-boost show as 8 cores)

whenever i catch this i do let it run for a reasonable amount of time 10-15 mins to allow for updates or whatever its trying. however, i do end up having to kill -9 it as just don't understand why its running so hot.
[IMG]http://ubuntuforums.org/picture.php?albumid=2211&pictureid=7468[/IMG]

if anyone has any suggestions on this i would appreciate them


----

I realize this is a really early bump but its not inteded as so, i was browsing the forums and realized i left the title as apt-get.... and would be better if i gave a more descriptive title. hense the edit. i really hope im not breaking any forum rules here as i really am not intent on bumping so soon.

---

### Post by antaios256 on 2011-03-16
**BUMP** 

also this problem seems to be reoccurring about every 6 hours.

---

### Post by antaios256 on 2011-03-17
Under software manager the ubuntu cd-rom option was checked causing the daily apt-get update to hang waiting for cd input and no terminal way to bypass the background process. disabling this option fixed the issue.

---

### Post by josvanr on 2011-03-28
thnx I was having the same problem here, now solved!

josvanr

---

### Post by antaios256 on 2011-03-28
> **josvanr said:**
> thnx I was having the same problem here, now solved!

josvanr

No problem, just remember that if you have an issue that gets solved post it as solved so it can help others as well  :P

---

