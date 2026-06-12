---
title: "Two questions on Skype"
date: 2012-04-20
forum: General Help
---

### Post by rex303 on 2012-04-20
Hello, is there a way to start skype at boot as minimized in unity (not in the system tray)?

it's for an installation on a pc used by old people and I wanted to simplify the situation in a way that is similar on what they had under windows so that skype starts on boot so they are reachable and if they click on the icon they get the contact list and not a new session asking for a password and giving errors

at the same time I would not want them not to be automatically logged in because they would forget to loh in every time but want to be reachable anyways.

that is why the second question is: is there a way to nake skype close upon clicking on the red X (closing the window) instead of simply minimizing in the system tray? an alternative would be getting it to minimize in unity or removing the close window button entirely.

this is to avoid the situation where skype is still running and you get a duplicate asking for a password upon relaunching it from unity.

thanks in advance for any help.

---

### Post by mastablasta on 2012-04-20
> **rex303 said:**
> Hello, is there a way to start skype at boot as minimized in unity (not in the system tray)?
 
it's for an installation on a pc used by old people and I wanted to simplify the situation in a way that is similar on what they had under windows so that skype starts on boot so they are reachable and if they click on the icon they get the contact list and not a new session asking for a password and giving errors
 
at the same time I would not want them not to be automatically logged in because they would forget to loh in every time but want to be reachable anyways.
 
.
 
 
first i believe skype in windows launches into system tray (thogh i haven't used autolaunch in a while).
 
second you sound confusing - first you say you don't want them to type in any password (this is done by autologin to skype on startup), but then you say you don't want them to have autologin. so which is it now?
 
additonally have you considered of using another DE for them that is more flexible?

---

### Post by ki4jgt on 2012-04-20
> **rex303 said:**
> Hello, is there a way to start skype at boot as minimized in unity (not in the system tray)?

it's for an installation on a pc used by old people and I wanted to simplify the situation in a way that is similar on what they had under windows so that skype starts on boot so they are reachable and if they click on the icon they get the contact list and not a new session asking for a password and giving errors

at the same time I would not want them not to be automatically logged in because they would forget to loh in every time but want to be reachable anyways.

that is why the second question is: is there a way to nake skype close upon clicking on the red X (closing the window) instead of simply minimizing in the system tray? an alternative would be getting it to minimize in unity or removing the close window button entirely.

this is to avoid the situation where skype is still running and you get a duplicate asking for a password upon relaunching it from unity.

thanks in advance for any help.

That was a tough one to make out but there should be a way to configure it to do some of that.

On your first sign-in, click sign me in when skype starts.

Also, add skype to your list of startup programs.

Make sure the desktop is set to auto login.

As for closing it, you're on your own there. Old dogs have to learn new tricks. That's a part of life. You could probably get someone to write you a script which checks if skype is running before starting a new session (if you ask nicely LOL) but it's unlikely. You would then place the skype icon on the script and add the script to your unity side menu.

---

### Post by More or Less on 2012-04-20
I think they want Skype to auto log in when launching, and when they "X" out the program they want it to log the user out.  This way they don't have to look for a "log out" option.

Another user might go to the computer and load Skype up forcing them to log out of the previous user's account and then log in since if they log out it won't automatically log in again.

---

### Post by rex303 on 2012-04-20
yes, in windows skype launches as minimized in tray, but "launching" it again by clicking on the icon doesn't actually start a new skype but simply opens the minimized one.

that is the behavior I was aiming to mimick.

I'm sorry if the original post wasnt' very clear.

actually a script that checks if skype is already executed would be a very good solution. would it be possible to write one in bash? if so I could try wrinting one myself looking up the commands on the wiki.

as for the launch as minimized, I wanted to check if there is a terminal command to do so that I could add to the startup programs list instead of just launching skype.

I don't want the window to just pop up for them unless they ask for it as they would probably just close it minimizing in tray and posing the login problem all over again (they are both over eighty years old and started using a pc just recently).

as for the autologin, I do want it, but I don't want to have the issue where skype is already running and a new session starts asking for login credentials instead of reopening the old (already logged in) sesssion.

---

### Post by ajgreeny on 2012-04-20
> **rex303 said:**
> yes, in windows skype launches as minimized in tray, but "launching" it again by clicking on the icon doesn't actually start a new skype but simply opens the minimized one.

that is the behavior I was aiming to mimick.

I'm sorry if the original post wasnt' very clear.

actually a script that checks if skype is already executed would be a very good solution. would it be possible to write one in bash? if so I could try wrinting one myself looking up the commands on the wiki.

as for the launch as minimized, I wanted to check if there is a terminal command to do so that I could add to the startup programs list instead of just launching skype.

I don't want the window to just pop up for them unless they ask for it as they would probably just close it minimizing in tray and posing the login problem all over again (they are both over eighty years old and started using a pc just recently).

as for the autologin, I do want it, but I don't want to have the issue where skype is already running and a new session starts asking for login credentials instead of reopening the old (already logged in) sesssion.

I am still confused by your comments and requirements.  I think what you want is already the default way, as long as you put a tick in two boxes when first starting the application after installing it.

I have skype set up on my machine, not unity but gnome classic in 10.04.  In that, the application is in my startup applications list and starts at session start, and is automatically logged in as my skype username, minimized to the system tray, and with no intervention on my part.

I think you must be missing something in your original configuration of skype; either you missed the "Start skype minimized to system tray" tick box in the skype options, or you missed the "log me in at startup" option the first time you logged in with username and password.

---

### Post by More or Less on 2012-04-20
Here's an idea.  I wasn't able to get Skype working in Pidgin to try this, but you could try using Pidgin to launch Skype.  There are check boxes in the connections area.  All they would have to do is uncheck their account.  At least that is what I am thinking.  There would be several Skype accounts added.  This is assuming you could just add all into Skype initially.

---

### Post by tmaranets on 2012-04-20
1st,if they just are going to use one account, change your settings so Skype automatically logs you in with that account. 2nd, if you want to do this in Windows, I believe you can have your account to be logged in after the startup, but the window doesn't appear. You will have to manually click the icon.

---

### Post by rex303 on 2012-04-20
I'm sorry if I'm not clear, English isn't my main language.

replicating the issue I have is easy: launch skype from unity -> close the window thus minimizing it in the systray -> relaunch skype from unity.

in windows this reopens the original (logged in) skype session, in ubuntu it opens a new skype and autologin doesn't work because "another session might be open".

to solve this I might have found a solution, I found this script:

#!/bin/bash
killall skype > /dev/null
sleep 5
skype&disown

I might use it to substitute the regular launcher so that it kills the old process before launching the new one. it's not the best solution but it seems the easiest (I don't know how to script myself).

a better way would be a script that checks if skype is running and opens the old session if it is or starts a new one if it isn't.

edit: I had in mind trying something like:

#!/bin/bash
killall skype
./skype

as a luncher with the skype icon in unity.

---

### Post by ki4jgt on 2012-04-20
> **rex303 said:**
> I'm sorry if I'm not clear, English isn't my main language.

replicating the issue I have is easy: launch skype from unity -> close the window thus minimizing it in the systray -> relaunch skype from unity.

in windows this reopens the original (logged in) skype session, in ubuntu it opens a new skype and autologin doesn't work because "another session might be open".

to solve this I might have found a solution, I found this script:

#!/bin/bash
killall skype > /dev/null
sleep 5
skype&disown

I might use it to substitute the regular launcher so that it kills the old process before launching the new one. it's not the best solution but it seems the easiest (I don't know how to script myself).

a better way would be a script that checks if skype is running and opens the old session if it is or starts a new one if it isn't.

edit: I had in mind trying something like:

#!/bin/bash
killall skype
./skype

as a luncher with the skype icon in unity.

Ideally you'd want it to check and see if skype is in the running processes as not to close the program while it's performing processes of it's own (if skype does any weird things of that nature) but this should safice until you find out how to do so. Something in my gut just screams at the idea of killing programs (especially GUI ones).

---

