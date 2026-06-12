---
title: "firefox badly broken for additional users"
date: 2009-09-08
forum: General Help
---

### Post by harrismh777 on 2009-09-08
Firefox runs great on my primary account... flash, video, audio.. all or it.

However, if I create additional users on the system, when they login and try to run firefox, the panels are badly broken. The ubuntu help panels work, but most other sites do not. Primary account works, secondary accounts do not... Please Help.   What is going on here?

:(

---

### Post by Vaphell on 2009-09-08
i assume we are talking only about firefox and how it displays webpages.
are you sure your working configuration is done system wide? maybe you have some stuff done in your home dir which is inaccessible to other users.

---

### Post by harrismh777 on 2009-09-08
> **Vaphell said:**
> i assume we are talking only about firefox and how it displays webpages.
are you sure your working configuration is done system wide? maybe you have some stuff done in your home dir which is inaccessible to other users.

Yes, just firefox and the way it displays webpages.  The pages are very badly terribly broken... most fields are lines, many photos don't display, most java stuff doesn't work, that page is kind-of exploded...  never seen this before...nor from firefox, not from linux, not from ubuntu.

What in the world could be setup for (*just*) my primary account that would not be system wide?  where do I look..?

thanks

---

### Post by Vaphell on 2009-09-08
for example you can have flash plugin in your home/.mozilla dir and only your account will use it, but what you describe sounds nothing like it. I have no idea what can cause such disaster.

maybe try copying your ff config ( .mozilla ) to new user's account and see if it still explodes.

---

### Post by harrismh777 on 2009-09-08
> **Vaphell said:**
> for example you can have flash plugin in your home/.mozilla dir and only your account will use it, but what you describe sounds nothing like it. I have no idea what can cause such disaster.

Just for fun I moved my .mozilla dir to the new account... no good.

I renamed my primary .mozilla dir to .mozillaold and reran firefox... it 
correctly rebuilt .mozilla dir and ran fine.  

No new user account can run firefox!   what  ?   :confused:

Help help... what is going on here?

---

### Post by Vaphell on 2009-09-08
it doesn't say anything interesting when run from terminal?

btw when you copied your ff profile... did you change owner? it won't be readable by another user if permissions are not set

---

### Post by harrismh777 on 2009-09-08
> **Vaphell said:**
> it doesn't say anything interesting when run from terminal?

btw when you copied your ff profile... did you change owner? it won't be readable by another user if permissions are not set

Yes yes... I'm getting closer... if I make the second user an administrator and then start firefox from the terminal with sudo:
    sudo /usr/bin/firefox

then firefox runs normally!!   So, its an authority problem.  The thing that completely baffles me is how it got messed up like this...  I don't remember doing *anything* differently on this machine setup from the other four... but, obviously, some critical components are missing because the second and third users don't have permission to run them... but I don't now what, and I don't know how... any thoughts for how I unscrew this mess short of reloading the silly thing?

thanks

---

### Post by Vaphell on 2009-09-08
check if the ff profile directories/files have proper ownership and rights
sudoing firefox is clearly an overkill :D

you could also install other versions of FF (3.5/3.6a/3.7a) and see if their profiles are messed up too.

---

### Post by harrismh777 on 2009-09-09
> **Vaphell said:**
> check if the ff profile directories/files have proper ownership and rights
sudoing firefox is clearly an overkill 

Yes. but which ones... specifically?  I am really stumped here...

I can not find a single file or directory "permission" ownership, or groupship problem... I am missing something here... 

Can you list which directories/files might be the culprit?

---

### Post by harrismh777 on 2009-09-09
Resolved.

After carefully sleeping on this, and waking to a beautiful sunny morning with nothing better to do...  I reloaded the little beasty...

All is well.


\\:D/

PS.  On the reload I did not try to use any of the desktop until the 
update process was complete, and I had created the user accounts I needed. Then I tried firefox for the first time... runs great across all accounts.

---

