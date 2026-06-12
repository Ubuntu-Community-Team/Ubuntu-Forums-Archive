---
title: "How to fix Top Panel corrupt , no more Shut Down Icon"
date: 2010-10-16
forum: General Help
---

### Post by aimwin on 2010-10-16
It happen at random login or boot up.
It happen to me on all previous versions, 8.04, 8.10, 9.04, 9.10, 10.04,

and just now on 10.10
edit - 6 nov 2010 -->Ubuntu 10.10 produce more Top Panel corrupt than any other previous version. 

So I need to support " chris hayes-clarke ", at lunchpad on
[https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/126290](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/126290)

[COLOR="Red"][B]How do I fixed this, easy option 1, temporary fix.
(Please look at easy option 2, more permanent fix)

1. Right Click on the Top panel. 
       [COLOR="Magenta"]==> new window for Panel configuration pop up.[/COLOR]
2. Left Click on "Properties" menu (second from the top "Add to Panel ...") 
       [COLOR="Magenta"]==> new bigger "Panel Property" window pop up.[/COLOR]
3. Choose the "Orientation" choice, CHOOSE "Right", 
       [COLOR="Magenta"]==> Top Panel will be move to the right hand side of the screen border.[/COLOR]
4. Now CHOOSE "TOP" 
       [COLOR="Magenta"]==> Right Panel will be move to the TOP POSITION[/COLOR]
        and become good 100% Original Top Panel.[/B][/COLOR]
[COLOR="Blue"]
Easy Option 2.(my friend, Prashan, remind me to add this option)
(Please look at attached screenshot below - 
Top Panel corrupted, and the fixed Shut Down ICON)

1. Right Click on Top Panel.
2. Left Click choose "Add to Panel"
3. scroll down to choose "Shut Down..." ICON
4. You always have Shut Down ICON on Top Panel which will always available, even though the Top Panel corrupted.
--->if some one experience differently, please post comment.<----[/COLOR]

But That is not the way UBUNTU should be.

MS windows never has that issue to me at all since window 3.1 till now.

I think it is time the Development team should seriously look into this "LongLong Time" bug.

Or at least some GURU help write the script checking the condition of the "default Shut Down ICON"
and order the reset to Right and to Top automatically.

since when it corrupted, you cannot even "software restart or SHUTDOWN Ubuntu".
(later edited - as I forgot I did what pc_michael commented in next post)

[COLOR="Red"]except you have to be command line user, and use left click on
>>>Application>Accessories>Terminal
then type "sudo shutdown now"
you need to have root password to key in for shutdown now command.[/COLOR].

Or
You can also >>System>Preference>Power Management>
Then at new Power Management Preference window, choose "General" tab.
ON Actions "When the power button is pressed" choose Shutdown,

And hope When Top Panel mess up, just press the Power Button to shut down computer.

Best Regards to All the GURUs

---

### Post by pc_michael on 2010-10-16
Thanks for the tip!  I certainly see that problem occasionally.

> **aimwin said:**
> since when it corrupt you cannot even "software restart or SHUTDOWN Ubuntu".

Just FYI, you definitely can software restart or shutdown Ubuntu, via terminal.

See the manpages for the "poweroff" and "restart" commands! :)  Also, the way *I* usually fix the problem is to log out and back in again, also via terminal using the "gnome-session-save" command when the Power icon is all weird in the gnome panel.

---

### Post by aimwin on 2010-10-17
Thanks for your feed back,"pc_michael"
So I decided to add to your comment.

In my experience:
log out and log in again is 50-50 % success chance.

My HOW TO above has never miss once, 
and quick fix,
on more than 10 different computers, over the last 3 years.
(please give feed back on my comments from your experiences).

And when after login, if it is still corrupt.
you can't even shut down from the login screen,
(with the shutdown icon on the buttom right hand corner)

So you have to shut down the computer only 3 ways.

Option 1.

Either go to Applications > Accessories > Terminal
at the "user:~$" prompt type in
shutdown now

--- if you got problem try

sudo shutdown now
but you got to know the admin password

IF you cannot shut down go to next option.

Option 2.
Press Power button for 2 seconds,
on many of computers, but not all computers,
the "shut down screen" will pop up.
and you can choose to shut down or restart here.

I did happen to me that even this option was not working,
the "Smart Ubuntu" don't want to go to sleep.

If you cannot shut down again, next option is 100% sure

Option 3.

 ==> only if option 1 and 2 cannot shut down UBUNTU.

take 4 seconds 
>>>>> but you should not take this option.>>> WHY ?
[COLOR="Red"]It could ruin you data in the hard disk,
    if the program is still writing to hard disk.[/COLOR]

Though in the past I did it many many times,
and it never ruin my "Super Robust UBUNTU", nor my data.
 may be just lucky for me,?, but no choice left.
---any Gurus please help comment.

Press the power buttons for 4 seconds
    >>> to turn off the power to the computer.

---

### Post by achookang on 2010-12-26
Thanks for the solutions to this incredibly annoying bug that I have only really noticed since the upgrade to 10.10

---

