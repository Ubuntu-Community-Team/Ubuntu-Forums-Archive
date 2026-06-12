---
title: "cookie woe's"
date: 2011-12-13
forum: General Help
---

### Post by Smilax on 2011-12-13
hi, i'm tryin to remove all cookies from my system.

i have firefox, 

so  far i try cookie culler, cookie monster, plus firefox menu it's self.

but every time i restart firefox, all the cookie remain. )edit-pref-showcookies(

does anyone have any hints on how i can do this?

regards.

---

### Post by oldtimer7777 on 2011-12-13
You want bleachbit:

sudo apt-get install bleachbit
gksu bleachbit

Careful that it doesn't delete your passwords.  Schedule it to work on shutdown, and you will be very happy with the result. 

> **Smilax said:**
> hi, i'm tryin to remove all cookies from my system.

i have firefox, 

so  far i try cookie culler, cookie monster, plus firefox menu it's self.

but every time i restart firefox, all the cookie remain. )edit-pref-showcookies(

does anyone have any hints on how i can do this?

regards.

---

### Post by Smilax on 2011-12-13
ok i've got it running but i have a big list with main headers

Bash.
deep scan
KDE
system

which should i choose (all are unticked)
to wipe the cookies>

cheers

---

### Post by oldtimer7777 on 2011-12-13
> **Smilax said:**
> ok i've got it running but i have a big list with main headers

Bash.
deep scan
KDE
system

which should i choose (all are unticked)
to wipe the cookies>

cheers

No problem. Here is how you configure it:

[https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/](https://debianhelp.wordpress.com/2011/08/02/how-to-maximize-system-performance-in-ubuntu/)

---

### Post by Smilax on 2011-12-13
thanks for the link old timer,

but alas, no joy.

i'm sure i did it right cause it told me to shut down firefox so it could delete the stuff, the only option in firefox menu section of bleachbit i left unchecked was passwords.


umm.  i keep tring, 

what you think??

---

### Post by oldtimer7777 on 2011-12-13
> **Smilax said:**
> thanks for the link old timer,

but alas, no joy.

i'm sure i did it right cause it told me to shut down firefox so it could delete the stuff, the only option in firefox menu section of bleachbit i left unchecked was passwords.


umm.  i keep tring, 

what you think??

  I'm wondering now if it actually deleted your caches..  Try it without the gksu command this time.  

just run in terminal:

bleachbit

not 

gksu bleachbit

and click delete.

Reboot your system when you are done.

And try Firefox or Chrome.

---

### Post by Smilax on 2011-12-13
hi, when i you the sudo one it deletes the firefox which is with the root user,
with just bleachbit it deletes the firefox with my user, 

but still the cookies remain.?

i just ran it then restarted before i opened firefox but still no joy>

---

### Post by Smilax on 2011-12-13
maybe if i could find the file they are in i could rm them myself?

---

### Post by Smilax on 2011-12-13
hi oldtimer.

i've fixed it

a addon for firefox was responable.

i disabled it and now the cookies are gone.](*,)

but thank you so much for taking the time to help out,

i think i'll get that bleach bit running at logout now.

:p

take care

---

### Post by oldtimer7777 on 2011-12-13
I set bleachbit so it cleans at shutdown..  Helps keep the browser running much faster too..

Don't forget to mark this thread as solved with thread tools above.

You are definitely welcome.

> **Smilax said:**
> hi oldtimer.

i've fixed it

a addon for firefox was responable.

i disabled it and now the cookies are gone.](*,)

but thank you so much for taking the time to help out,

i think i'll get that bleach bit running at logout now.

:p

take care

---

### Post by Smilax on 2011-12-13
solved.

cheers old timer.

---

