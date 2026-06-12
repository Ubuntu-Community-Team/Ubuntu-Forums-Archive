---
title: "Is Ubuntu usable on laptop after &quot;Suspend&quot;?"
date: 2011-12-17
forum: General Help
---

### Post by alexei_ on 2011-12-17
I already mentioned my problems in other posts. Here is [my hardware/system info]("http://ubuntuforums.org/showpost.php?p=11519464&postcount=9")

I did not see similar problem on desktop with Ubuntu, even with older hardware. Here is what is happening. After several "suspend"s system becomes less responsive. I have timer with seconds and can see how seconds freezes for 40 and more seconds. I observe that hard drive is in use... but still ... Why time is freezing? Well, freezes the whole system. I can usually move mouse cursor ... and that is it. None of applications are working during this freeze time. For example from 5 minutes I had to wait 3 minutes total... The system is unusable for 60% of the time -- this horrible. Never had similar issues with Windows XP Home during 4 years of usage.

I use mostly Browsers: firefox, google-chrome, byoby and vim. Specifics of usage -- I put my laptop on "suspend" 2 of more times a day.

---

### Post by pretty_whistle on 2011-12-17
Are you saying that after your computer is on suspend it doesn't reach the desktop?  If so, this was reported as a bug in unity.  Here's a workaround for it:

  	 	 	 	 	 	   [SIZE=3]

[SIZE=2]Here's an askubuntu about it:
[http://askubuntu.com/questions/14289/laptop-does-not-wake-up-after-sleep](http://askubuntu.com/questions/14289/laptop-does-not-wake-up-after-sleep)

Workaround:[/SIZE][/SIZE]
[SIZE=2] [/SIZE][SIZE=2]
[/SIZE] 
[SIZE=2] [/SIZE][SIZE=2]You can resume ok if you enter your password in as though you got the login screen (even if you have automatic login enabled).

Apparently the login in screen is there but is "out of view".  Just treat the screen you're seeing as a click-through by assuming the cursor is in the password field.  Put the password in and it'll resume.

Solves the problem of having to do a hard shutdown and startup to reach the desktop.[/SIZE]
[SIZE=2] [/SIZE][SIZE=2]
[/SIZE] 
[SIZE=2]  [/SIZE]

---

### Post by alexei_ on 2011-12-17
[pretty_whistle]("http://ubuntuforums.org/member.php?u=1224514"), no my problem is HUGE DEGRADATION IN PERFORMANCE after suspend.

---

### Post by pretty_whistle on 2011-12-17
> **alexei_ said:**
> [pretty_whistle]("http://ubuntuforums.org/member.php?u=1224514"), no my problem is HUGE DEGRADATION IN PERFORMANCE after suspend.
Oh, ok.  I misunderstood the problem.

---

