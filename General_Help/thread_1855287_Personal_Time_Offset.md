---
title: "Personal Time Offset"
date: 2011-10-05
forum: General Help
---

### Post by hwttdz on 2011-10-05
On a machine on which I am not root the clock is pretty seriously off.  I'd like to set a time offset for me (i.e. add or subtract a given number of seconds from the system clock, but only for my user).  Is this possible?

---

### Post by ubudog on 2011-10-05
Can you do this?

Click on the time applet.  Select locations.  Select edit.  Add your location, select your time.

That should do it!  :)

---

### Post by hwttdz on 2011-10-07
That only gives you the possibility of setting the system time which is a root protected command (though it may be rigged on desktop ubuntu to allow the user to do it).  Anyways, safe to assume I can't change the system time on the server.  I am looking for a way to make my personal timezone offset be something like 5 hours (time zone offset) + 4787 seconds (error in the system clock), but only affecting my user.

---

### Post by hwttdz on 2011-10-18
Thought of a solution, but found a different workaround.

I'm actually using PROMPT_COMMAND="touch ~/.timefile" and
"date --reference="~/.timefile"", because apparently the fileserver has the correct date.

The other way would be to use 
date --date="now + $personal_offset seconds"
instead of date, so then the only question would be getting the initial time offset which isn't that bad.

---

