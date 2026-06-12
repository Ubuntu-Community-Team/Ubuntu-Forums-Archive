---
title: "Thunderbird 13.0.1 crashes - will not run - in Ubuntu 12.04 updated. Help!"
date: 2012-06-27
forum: General Help
---

### Post by candtalan on 2012-06-27
I have just returned after a few days and I have updated Ubuntu 12.04 (about 13 updates) and immediatelty after this when I start thunderbird, (now apparently version 13.0.1) Thunderbird crashes after approximately 15 seconds!! I have tried restart of the machine also starting thunderbird off line, or online, it still just crashes out! 
WTF! Cannot use thunderbird!!

Urgent - help please anyone?

Edit:
Ironically, about the same time as the password request appears in thunderbird - I have hardly enough tinme to enter the pw before tbird crashes out -  I see a update information window - What is new in thunderbird - and an invitation to set up Filelink (or similar) and also a statement about 'increased stability'. (How sick is that)?

I really need an answer to this soon, I use email a lot.....

---

### Post by candtalan on 2012-06-27
fwiw the thunderbird crash information is this:
Add-ons: [email]edsintegration@mozilla.com:0.3.9,messagingmenu@mozilla.com:0.9.3,globalmenu@ubuntu.com:3.2.3,langpack-en-GB@thunderbird.mozilla.org[/email]:12.0.1,{972ce4c6-7e08-4474-a285-3208198ce6fd}:12.0.1
BuildID: 20120615093033
CrashTime: 1340823901
EMCheckCompatibility: true
Email: [email]aeclist@candt.waitrose.com[/email]
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1340822273
Notes: OpenGL: Tungsten Graphics, Inc -- Mesa DRI Intel(R) G41 x86/MMX/SSE2 -- 2.1 Mesa 8.0.2 -- texture_from_pixmap

ProductID: {3550f703-e582-4d05-9a08-453d09bdfdc6}
ProductName: Thunderbird
ReleaseChannel: release
SecondsSinceLastCrash: 333
StartupTime: 1340823884
Theme: classic/1.0
Throttleable: 1
Vendor: 
Version: 13.0.1

Is anyone else finding this problem please? If not then I will strip any plugins back etc

tia

---

### Post by candtalan on 2012-06-27
I had some simple custom css stuff in a chrome folder (in the .default folder) and I disabled this by renaming the folder, and restarted the machine then thunderbird, but it still immediately crashed.

I then briefly  looked at the Tools>addons listed fro thunderbird, and could see three shown. The crashes happen SO quickly that it was a slick task to try to 
1) login with my pasword and 
2) list the addons and 
3) disable the addons
before thunderbird crashed, but I did manage to achieve this. With all three shown addons  then disabled, I noticed that there was no crash, so I then took a screenshot  of theaddons list (attached).

Thunderbird now seems to be working ok..... (hoping) but am I an isolated case I  wonder?

---

### Post by Endash on 2012-06-29
Hi candtalan,

I am following your post.

I have been struggling with the exact same bug and crashes since I upgraded Xubuntu from 11.10 to 12.04, more than a month ago. I use no fancy CSS or any other add-on, except Google Calendar.

I hope someone will find a solution.

Good luck !

Dash

---

### Post by candtalan on 2012-06-29
Hi Endash
fwiw, I have now had no crashes at all since I disabled all three addons as mentioned in my post (and screenshot). I have not had time to go back and do some tests, one addon at a time, not even to file a bug.
Have you been able to see the addons and disable them?

---

### Post by Endash on 2012-06-29
Hi candtalan,

I misread your posts, I thought you still had the crash.

I use only 2 add-ons with Thunderbird: Lightning and Google Calendar. Is one of them in your add-on list as well ?

---

### Post by candtalan on 2012-06-29
> **Endash said:**
> Hi candtalan,

I misread your posts, I thought you still had the crash.

I use only 2 add-ons with Thunderbird: Lightning and Google Calendar. Is one of them in your add-on list as well ?

The addons apparently giving my grief were not added my me(!) they came as part of the Ubuntu 12.04 install afaik
So at present I am running a 'non standard' ubuntu 12.04.....

can you see  the names by looking a tmy screenshot?

EDS contact integration 0.3.9
global menu bar integration 3.2.3
messaging menu and unity launcher (etc)

hth

---

### Post by tshiker on 2012-06-29
Try removing and then reinstalling Thunderbird. It worked for me when I had the same problem.

Tom.

---

### Post by Endash on 2012-06-29
Finally, starting TB in safe mode and deactivating some add-ons before restarting TB in normal mode seem to work.

---

### Post by candtalan on 2012-06-30
> **tshiker said:**
> Try removing and then reinstalling Thunderbird. It worked for me when I had the same problem.
Tom.
Thanks. Was that a warm reinstall or a 'purge'? A 'warm' reinstall would install over the original but will expect to retain the original data , emails, etc?

---

### Post by ray field on 2012-07-08
> **candtalan said:**
> Thanks. Was that a warm reinstall or a 'purge'? A 'warm' reinstall would install over the original but will expect to retain the original data , emails, etc?

I'm curious about this too -- at this point Thunderbird 13.0.1 is unusable, it consumes so much CPU I'm actually afraid it's apt to damage my computer.

---

### Post by firekage on 2012-07-09
> **Endash said:**
> Finally, starting TB in safe mode and deactivating some add-ons before restarting TB in normal mode seem to work.

How did you run it in a safe mode? On Windows when we click on thunderbird icon there is such an option but under Ubuntu i don't know where it is hidden.

---

### Post by ChrisHodgesUK on 2012-07-09
run:
thunderbird --safe-mode 
from a terminal

There are 3 addons I don't recognise (unity integration on xfce - doesn't sound right!) newly upgraded to 13.0.1 under xubuntu 11.10
disabling all 3 addons sorted it for me, crashing seconds after launching except once when it hung

---

### Post by ray field on 2012-07-09
I disabled all plugins -- about 15 of'em -- & restarted -- no problem. then I enabled them, one by one, except for three I don't really use (Allow HTML Temp, Mail Redirect, ThunderBrowse) and now T-bird seems to be behaving itself & no longer taxing the CPU. weird.

---

### Post by diegA70 on 2012-07-10
I am following this post, since I have the same problem. 
I have completely reinstalled the application and did not solved my problem. 
However I have disabled the two add-ons which are coming by default (quickly, before the crash)
- EDS Contact Integration 0.3.9 
- Messaging Menu and Unity Launcher Integration 0.9.3 
and now TB is not crashing so far. 
I will keep working this way and post additional information. 

Hope that helps.

---

### Post by leona on 2012-11-07
I was hoping these changes would help me, but sadly, after disabling all the extensions, Thunderbird still freezes up now and again.

---

### Post by Elmer Fudd on 2012-12-28
Had the same problem.
Disabled "EDS Contact Integration" extention.
That seems to have fixed it for me.

I also set Addressing (account settings/composition & Addressing) to "Use my global LDAP server pref ..." and Thunderbird Preferences Composition/ Addressing to "local Address Books" but have not changed any of those back to see if it mattered.

12.04
Sony F series laptop
Thunderbird 17.0

---

