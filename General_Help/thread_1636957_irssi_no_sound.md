---
title: "irssi no sound"
date: 2010-12-03
forum: General Help
---

### Post by fiskenslakt on 2010-12-03
I can't get irssi to notify me when channels/windows are active with a beep. i've set all the bell beeps settings correct as far as i know: 
beep_msg_level = MSGS NOTICES DCC DCCMSGS HILIGHT
beep_when_away = ON
beep_when_window_active = ON
bell_beeps = ON

i thought the problem might have been that i didn't have beep installed. So i installed it but still nothing.

i've googled the problem for weeks to no avail. help?

---

### Post by andrew.46 on 2010-12-05
Hi fiskenslat,

Perhaps have a look at the solution that I have used:

[http://ubuntuforums.org/showpost.php?p=8720989&postcount=4](http://ubuntuforums.org/showpost.php?p=8720989&postcount=4)

I am still using this without problem and I suspect it will meet your needs as well.

Andrew

---

### Post by fiskenslakt on 2010-12-08
> **andrew.46 said:**
> Hi fiskenslat,

Perhaps have a look at the solution that I have used:

[http://ubuntuforums.org/showpost.php?p=8720989&postcount=4](http://ubuntuforums.org/showpost.php?p=8720989&postcount=4)

I am still using this without problem and I suspect it will meet your needs as well.

Andrew

Unfortunately i have already read that post and tried it. Instead of working, it created a problem where weird error messages would take over my terminal while private messaging people. I fixed it by getting rid of the line:

beep_cmd play -q ~/.irssi/scripts/ding_dong.wav &
Perhaps i screwed something up, but i don't know, i've tried a lot of things and nothing is working.

---

### Post by andrew.46 on 2010-12-09
Hi fiskenslakt,

I suspect another device or application is using your sound system. Try the script without anything else using sound.

Andrew

---

