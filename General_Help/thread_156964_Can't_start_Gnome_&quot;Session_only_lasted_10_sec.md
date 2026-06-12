---
title: "Can't start Gnome &quot;Session only lasted 10 seconds&quot;"
date: 2006-04-08
forum: General Help
---

### Post by colinkingswood on 2006-04-08
I have a partition with Mandriva setup, but it has started crashing a lot recently, so I have installed Hoary (I has a disk with that on it - I know I am out of date, I was going to upgrade it  when it was installed). 

I wanted to share the /home partition with Mandriva and use my same username colin, so that I can use the same desktop and folders. Anyway, I have set all that up with the installer,  but when I try and log on I get the following error...

"Your session only lasted less than 10 seconds. If you have not logged out yourself this may mean there is some installation problem......"

clicking the view details it gives me some lines about stating up X, then....

[FONT="Courier New"]Could not set mode 0700 on private per user gnome configuration directory ''/home/colin/.gnome2_private' : operation not permitted[/FONT]


Am I right in guessing that this is because the colin account has a different user id set between Ubuntu and Mandriva? Or am I way off?

And more importantly how do I fix it...?

---

### Post by matthewv on 2006-04-08
Welcome to ubuntu :)

I am pretty sure that you are right... to fix it, change your session from the login screen to 'failsafe' and then log in. Once logged in, try running ```
sudo chown -R colin /home/colin/
``` Then run the command 'exit' to get back to login screen. Log in to gnome and hopefully its all fixed :)

---

### Post by colinkingswood on 2006-04-08
:)

Thanks, for such a quick reply.......
That was even easier than I expected......

Does anyone know of any good tutorials about this sort of stuff? I can see that username and userid are different,and Ubuntu seems to have set it up with a different one from Mandriva. I couldnt find anything good when browsing about, trying to fix this. (I think I have had simlar problems before trying to access things from Knoppix.)

---

