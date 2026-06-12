---
title: "Growing pains!  Problems after upgrading from 11.10 to 12.04"
date: 2012-04-26
forum: General Help
---

### Post by Eirreann on 2012-04-26
I started another thread in the Absolute Beginner section, but I'm making another one here because threads in the Beginner section don't tend to get much feedback.... and since posting that thread more issues have become present.  Please, if any of you can even suggest a solution for one or all of the issues I am experiencing, I would really appreciate it!
What's been going on thus far:

1. Trying to use Ubuntu (non-2D) is impossible, because all that is  visible is the gnome bar thing on the top of the screen; everything else  is white except for the strip where the applications usually are and  that's a different colour; I can still open applications but they don't  show up, all I see is this white screen.  I had this problem with 11.10  as well, and then all I had to do was update the Nvidia drivers through  the Additional Drivers section in System Settings.  However, when I went  to Additional Drivers after installing 12.04 (got there through using  Ubuntu (Unity 2D)), first I got an error then no drivers appeared, so  now I'm stuck with the 2D version of Ubuntu.  After searching it seems that the Nvidia settings application is gone as well.
2. The launcher won't auto-hide.  If I turn auto-hide on, it will hide, but it won't reappear.
3. Occasionally I get "Encountered a problem and needs to close" error messages, although the program in question doesn't close.  I don't know if I should worry about this or not....
4. The boot sound doesn't sound.  I checked the Startup Applications but the boot sound isn't there!!!

Please, please, please, if any of you even have an idea, I would greatly appreciate some help here!
Thanks!

---

### Post by Eirreann on 2012-04-26
Okay, encountered a new problem: the boot sound doesn't sound.  I checked the Startup Applications but the boot sound isn't there!!!    (added to first post)

---

### Post by techsupport on 2012-04-26
> **Eirreann said:**
> I started another thread in the Absolute Beginner section, but I'm making another one here because threads in the Beginner section don't tend to get much feedback.... and since posting that thread more issues have become present.  Please, if any of you can even suggest a solution for one or all of the issues I am experiencing, I would really appreciate it!
What's been going on thus far:

1. Trying to use Ubuntu (non-2D) is impossible, because all that is  visible is the gnome bar thing on the top of the screen; everything else  is white except for the strip where the applications usually are and  that's a different colour; I can still open applications but they don't  show up, all I see is this white screen.  I had this problem with 11.10  as well, and then all I had to do was update the Nvidia drivers through  the Additional Drivers section in System Settings.  However, when I went  to Additional Drivers after installing 12.04 (got there through using  Ubuntu (Unity 2D)), first I got an error then no drivers appeared, so  now I'm stuck with the 2D version of Ubuntu.  After searching it seems that the Nvidia settings application is gone as well.
2. The launcher won't auto-hide.  If I turn auto-hide on, it will hide, but it won't reappear.
3. Occasionally I get "Encountered a problem and needs to close" error messages, although the program in question doesn't close.  I don't know if I should worry about this or not....

Please, please, please, if any of you even have an idea, I would greatly appreciate some help here!
Thanks!

All of these issues are normal for 12.04 right now because they are having technical issues patching the video drivers for that, and it just got released so there are going to be other unknown issues that will need to be reported.  That's the name of the game with 12.04, for now.

---

### Post by Eirreann on 2012-04-26
> **techsupport said:**
> All of these issues are normal for 12.04 right now because they are having technical issues patching the video drivers for that, and it just got released so there are going to be other unknown issues that will need to be reported.  That's the name of the game with 12.04, for now.

Thanks for the quick reply!  Is it the same case for the boot sound, as well?
And about when will these problems be resolved, do you think?

---

### Post by TBABill on 2012-04-26
Was this an actual upgrade or a fresh install moving from 11.10 to 12.04? If it's an upgrade it sounds like it may not have gone well. Perhaps trying a fresh install would give you an opportunity to see if it's a software issue. Also, did you try it in a live session to make sure it all worked ok before moving to 12.04?

---

### Post by Eirreann on 2012-04-26
> **TBABill said:**
> Was this an actual upgrade or a fresh install moving from 11.10 to 12.04? If it's an upgrade it sounds like it may not have gone well. Perhaps trying a fresh install would give you an opportunity to see if it's a software issue. Also, did you try it in a live session to make sure it all worked ok before moving to 12.04?

It was an upgrade via Upgrade Manager from 11.10 to 12.04... unfortunately a fresh install may be a bit difficult for me, as I don't have any blank cds or USB devices that I can wipe and re-format... I may be able to get a hold of something but who knows when that will happen...
And I paid careful attention to the terminal as the installation was taking place, and not a single error occurred that I could see.

---

### Post by gontofe on 2012-04-28
I am also having the problem with auto-hide - once I enable it the Launcher won't come back even when I move my mouse to the left-hand side of the screen. I have to press the super key to make it happen...

---

### Post by amr-maro on 2012-04-30
1) It is _**NOT**_ about how _**hard**_ you push the mouse cursor, it about how _**far**_ you push. To be able to reveal the launcher, you have to _***continuously***_ push the cursor against the edge to reveal it.

2) To fix the launcher reveal sensitivity:
a. Install then start "CompizConfig Settings Manager"
b. Navigate to "Desktop" > "Ubuntu Unity Plugin" > "Experimental" tab
c. Find the string "Launcher Reveal Pressure"
d. The default is 20, change it to 7 (or whatever you prefer)
e. You don't have to close CCSM to apply the changes. Keep changing the  value till you are satisfied with the result, then close CCSM.

3) You won't find the login sound because it is completely removed from 12.04 by default. It was an official decision from Canonical. :)

---

### Post by keithpeter on 2012-04-30
> **amr-maro said:**
> 1) It is _**NOT**_ about how _**hard**_ you push the mouse cursor, it about how _**far**_ you push. To be able to reveal the launcher, you have to _***continuously***_ push the cursor against the edge to reveal it

That is a good explanation thanks!

@gontofe: you can adjust the reveal sensitivity in 12.04 without installing CCSM. Just

 right click over the desktop and select the **Change Desktop Background** item. 

Click on the **Behavior** tab, then switch the **Auto-hide the launcher** On.

You can try the slider control for different sensitivies. I have mine set quite 'high' but whatever works for you.

CCSM does a lot of other things but I find it confusing because it interacts with other settings that Unity uses.

---

### Post by amr-maro on 2012-05-01
> **keithpeter said:**
> You can try the slider control for different sensitivies.
Yes, you're right :) But here is the thing, I think there is a bug with the slider, meaning, moving the slider all the way to the right does not make any change at all. Many people are complaining about this in another thread :) [http://ubuntuforums.org/showpost.php?p=11891182&postcount=81](http://ubuntuforums.org/showpost.php?p=11891182&postcount=81)

---

