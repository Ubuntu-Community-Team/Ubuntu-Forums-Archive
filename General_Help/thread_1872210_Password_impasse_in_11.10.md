---
title: "Password impasse in 11.10"
date: 2011-10-30
forum: General Help
---

### Post by tonewheelkev on 2011-10-30
Password problems persist...have not been able to understand/follow any of the fixes offered so far by other members
......sorry....I'm thick!!

Is there a step-by-step guide out there...this is really infuriating.....

Can't update.....can't access terminal.....was fine in 11.04

Kev

---

### Post by Gremlinzzz on 2011-10-30
> **tonewheelkev said:**
> Password problems persist...have not been able to understand/follow any of the fixes offered so far by other members
......sorry....I'm thick!!

Is there a step-by-step guide out there...this is really infuriating.....

Can't update.....can't access terminal.....was fine in 11.04

Kev

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by tonewheelkev on 2011-10-30
> **Gremlinzzz said:**
> [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Thanks Gremlinzzz....will try this....then perhaps I can follow your earlier advice relating to Epson printing....:D

---

### Post by tonewheelkev on 2011-10-30
....now totally immersed in the thick brown smelly stuff......:confused:

tried following instructions at [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

..now I have had to boot from a 10.04 disc in order to get back on-line

When I entered 

ls /home

....I didn't get a list of users....my only option was to switch off machine...:confused:

Am now CAREFULLY re-reading instructions

Kev

---

### Post by Rhizoid on 2011-10-30
Where are you in the World tonewheelkev ?

---

### Post by tonewheelkev on 2011-10-30
> **Rhizoid said:**
> Where are you in the World tonewheelkev ?

...in good 'ole Leeds.....but from Sunderland
(but that was a LONG time ago!!)

---

### Post by tonewheelkev on 2011-10-30
> **tonewheelkev said:**
> ....now totally immersed in the thick brown smelly stuff......:confused:

.....Am now CAREFULLY re-reading instructions
Kev

Realised that as the ONLY user...didn't need to enter

ls /home

...so entered

passwd kev    (....that's me!!)

entered new password, and confirmation....then received:

[B]passwd: Authentication token manipulation error
passwd: unchanged[/B]

aaaaaagggghhhhhhhh!!!!!!!!!!!

---

### Post by Rhizoid on 2011-10-30
> **tonewheelkev said:**
> Realised that as the ONLY user...didn't need to enter

ls /home

...so entered

passwd kev    (....that's me!!)

entered new password, and confirmation....then received:

[B]passwd: Authentication token manipulation error
passwd: unchanged[/B]

aaaaaagggghhhhhhhh!!!!!!!!!!!

Have you tried ```
sudo passwd kev
``` ?

---

### Post by tonewheelkev on 2011-10-30
> **Rhizoid said:**
> Have you tried ```
sudo passwd kev
``` ?

...says
sorry, try again


What should happen?

---

### Post by OlympicSoftworks on 2011-10-30
There is no need to use sudo when you are already ROOT.  Using the "drop to root" from the recovery menu places you as the admin...there should be no need for admin to request admin status.

---

### Post by tonewheelkev on 2011-10-31
> **OlympicSoftworks said:**
> There is no need to use sudo when you are already ROOT.  Using the "drop to root" from the recovery menu places you as the admin...there should be no need for admin to request admin status.

But when I tried that route :

[B]passwd: Authentication token manipulation error
passwd: unchanged[/B]

....was returned :confused:

---

### Post by tonewheelkev on 2011-11-01
Ttt....

---

### Post by jaquino on 2011-11-05
Sadly, none of these solutions work. The installation for 11.10 is BROKEN BROKEN BROKEN. Doing "passwd username" or "sudo passwd username" from the recovery console only brings up "Authentication token manipulation error"  Someone needs to come up with another solution -- I sure as hell do not have one for this and am getting very frustrated.

---

### Post by tonewheelkev on 2011-11-10
Can't help but agree with jaquino

.....over 220 updates...and counting, and can't get past the Password Authentication stage:confused:

Has someone out there cracked this one yet????

---

### Post by oldos2er on 2011-11-10
Check post #3 in this thread: [http://ubuntuforums.org/showthread.php?p=11379306](http://ubuntuforums.org/showthread.php?p=11379306)

---

### Post by tonewheelkev on 2011-11-10
> **oldos2er said:**
> Check post #3 in this thread: [http://ubuntuforums.org/showthread.php?p=11379306](http://ubuntuforums.org/showthread.php?p=11379306)

Thanks oldos2er for the reply.......

Tried this.....entered the password...
...returns "password incorrect"

What am I doin' wrong....:confused:

---

### Post by tonewheelkev on 2011-11-10
Solved it by following Post #2 here.....

[http://www.linuxquestions.org/questions/linux-newbie-8/i-lost-my-ubuntu-user-name-and-or-password-597888/](http://www.linuxquestions.org/questions/linux-newbie-8/i-lost-my-ubuntu-user-name-and-or-password-597888/)

Worked for me...at LONG last...:)

---

### Post by OlympicSoftworks on 2011-11-14
Ok, I don't know if this is what is happening for everyone but for me it worked and it makes sense.

My own installation that I had password retrieval issues with uses a fairly custom partitioning scheme.  I have /home on it's on partition and several smaller partitions set up with various installs of GNU/Linux.  I was getting this error after I tried to retrieve and it made absolutely no sense.  Then it dawned on me that /home had not been mounted at this point in the recovery boot.

Then I noticed an option to mount devices above the selection to drop to root console...I selected that, and after it mounted all my partitions I dropped to root console and changing the password worked perfectly.

For anyone getting discouraged, remember that the install process takes an enormous amount of things into consideration and selects what it thinks is the best way.  It isn't always going to be correct. Therefore if you have a situation where you are not installing things in a completely standard way, you may need to intervene in any recovery attempts because of it.

---

