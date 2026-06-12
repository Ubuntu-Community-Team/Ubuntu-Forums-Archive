---
title: "Odd Login Problem"
date: 2010-01-01
forum: General Help
---

### Post by MiamiDolphins13 on 2010-01-01
I recently installed Ubuntu on my sisters computer (Koala 9.10) and everything has been working fine. I would say it was installed christmas day, and since thing no problems at all. Just her getting used to Ubuntu from XP. 

Anywho, I had it set so that it would automatically login to her name, aside from that there are no other accounts on the system.

So now today i get a call "Pat, whats my password to login"

So i tell her, n she says it doesnt work. I told her make sure caps lock is off (she'd be one to not notice that! :P)

So i decided to take a drive over to her house and see what i can do.

Now here is the issue im facing and i do not know what to do or how to describe it!


At the login screen, i click her name, enter her password..and it starts to load normally with the Ubuntu words and the bar underneath it.

After about 3-5 seconds of doing so, the screen i guess "Clicks?" , it turns black for a second(not powering off) and turns right back on except the ubuntu words are off centered and zoomed in. As if the resolution changed for a split second. Then the screen "clicks" off again and the normal sized ubuntu words/loading bar appear. Just when you think its going to log you in, it takes me right back to the "Select User" to login screen.

Ive tried to login using "GNOME' "GNOME Failsafe" and neither work.

I can open the "Xterm" though and access a command prompt using that login.

any ideas guys? 


hope everyone had a great newyear:guitar:

---

### Post by Brandon Williams on 2010-01-01
After a failed login, press Ctrl+Alt+F1 to get a console login prompt and login there. View the contents of .xsession-errors with the command 'less ~/.xsession-errors'. Do you see anything in the file that indicates a catastrophic error?

Frequently, these sorts of problems are associated with the user config and/or file directory permissions in the user's home directory. You might also want to try creating a new user account with 'sudo adduser newuser' Now log in as that user. Do you have the same problem with the new user?

---

### Post by MiamiDolphins13 on 2010-01-01
About to  go try that right now...thanks for the reply. will let you know what happens ASAP

---

### Post by MiamiDolphins13 on 2010-01-01
ok so i typed in 

"less~/.xsession-errors" 

without the quotes..and it said not found.

so then i tried the sudo new user ..and that worked.

it allowed me to login to a new user account and i was able to get the desktop.

since dangerous is my middle name i decided to switch users and see if i could login using the original account..and for some weird reason..it let me!

i was able to login to the original account...maybe logging into a fresh account first helped with something.

but who knows how it was fixed, but all i know is its fixed!

thanks so much for the help! really appreciate it:KS

---

### Post by Brandon Williams on 2010-01-03
Glad you got it working.

Just for future reference:

> **MiamiDolphins13 said:**
> ok so i typed in 

"less~/.xsession-errors" 

without the quotes..and it said not found.


There should be a space in between 'less' and '~/.xsession-errors'. less is the command and ~/.xsession-errors is an argument to that command.

---

