---
title: "Problem with CheckGMail Notifier"
date: 2009-09-17
forum: General Help
---

### Post by craig10x on 2009-09-17
I just began having a problem with this program today...when i launched it this morning, the log in window popped up with message "error..incorrect user" and the log in window DOES have my correct log-in information...

I'm assuming that google must have changed something in the gmail log in that is causing the problem.....how do you fix this problem?  or perhaps get an updated version of the program that corrects the problem?

As it is now, can't use the notifier to see when new gmail has come in....i really like the program and would like to continue using it......

---

### Post by ajdrew06 on 2009-09-17
I am having the same trouble.  I found the website for checkgmail, and on their website they have a """""fix""""".  They say to type 'checkgmail -update' in terminal, and follow the instructions.  This doesn't work.  It eventually asks you for your user name and password, and continues to give the 401 error.  Please help.

This is directly from the website: 

401 Unauthorised Fix

Gmail recently changed the login procedure, resulting in this error. To fix this issue, please use the latest version from SVN -- the easiest way to do this is to run checkgmail -update from the commandline and follow the prompts.

---

### Post by stevo1977 on 2009-09-17
I have been having the same problem today.  The -update thing didn't work; people have said that sourceforge disabled CVN or something like that.

I found this resource:
[http://tombuntu.com/index.php/2008/07/23/updating-checkgmail-to-fix-login-errors/](http://tombuntu.com/index.php/2008/07/23/updating-checkgmail-to-fix-login-errors/)

but it's a few years old.  I followed the instructions, and now have v1.13 installed, but I have the same login error.  What is going on?

EDIT:
Okay, I once again tried the suggestion to run 'checkgmail -update' in the terminal, and after following the directions it asked for permission to overwrite 'checkgmail' with the new version. I typed 'y' for 'yes,' and then it said "Update NOT performed . . ."

Then is started up the app and gave me the same login error.

---

### Post by craig10x on 2009-09-18
Mine starting working again.....don't know what happened....it's a real mystery...i wonder if maybe google got a lot of complaints and made some kind of change....probably a lot of e-mail notifiers were experiencing problems because of whatever changes they made....

Anyone else's  CheckGmail notifer started working again? 
Just curious :)

---

### Post by ajdrew06 on 2009-09-18
mine still doesn't work >=|... how come yours works?? not fair =P

---

### Post by stevo1977 on 2009-09-18
Mine, also, still gives me the login error.

---

### Post by craig10x on 2009-09-18
well...i can't imagine why this would have made a difference on mine....but i did go to add/removeprograms and take it off and then add it back in TWICE.....the first time i put it back on...it was the same (couldn't log in)...then, about an hour later i took it off and added back on again...and it started to work immediately...like nothing ever happened!

weird, right??? :confused:

try what i did...and report back if it made any difference for you......
i still can't figure out why, after doing it 2x it came back to life again....lol ;)

---

### Post by stevo1977 on 2009-09-19
I tried removing and reinstalling a few times, hours apart, but no luck.  By the way, I'm having this problem on multiple computers (my ubuntu desktop and my eeebuntu netbook).  What is the deal?

---

### Post by ajdrew06 on 2009-09-19
I ran the command "checkgmail -no_cookies" and it seems to log in.  It does notify me of email; however, it only lets me "open" the email and does not let me "mark as read" or "delete" the email.

The one problem I have with this solution is that I don't know how to run this command without leaving a terminal window open.  If I close the terminal window, it closes checkgmail as well.  This seems to be a half-assed solution to our problem.

---

### Post by craig10x on 2009-09-19
And, as mentioned, the "weird" part is mine came back to life after two uninstall-reinstalls....and i haven't a clue as to why that happened.....

Hope someone is able to figure out how to solve the problem.....so far i am keeping my "fingers crossed" that mine will keep working...

Still, i would love to know the proper solution, in  case mine starts having trouble again...CheckGMail is one of the nicer Gmail notifiers......

---

### Post by stevo1977 on 2009-09-19
Yeah, I read about the 'no_cookies' workaround on that link I posted, but then I lose a lot of the functionality which made me choose checkgmail in the first place.  And as mentioned, it's a workaround, not a solution.

ajdrew06: For the time being, what you can do is right-click on the 'Applications' button and go to 'Edit Menus.'  Then find the entry for 'checkgmail' (usually under the 'Internet' category), highlight it, and then click 'Properties' over on the right.  There should be an entry there for the command to run the program (which should be just 'checkgmail').  You can add the 'no_cookies' option into that line (so that it reads 'checkgmail -no_cookies' w/o quotes).  I'm pretty sure that will do what you want.

---

### Post by stevo1977 on 2009-09-19
Here's a fun twist: using the 'no_cookies' option worked on my eeebuntu netbook, but not on ubuntu desktop (and yes, I checked to make sure the user and pass were correct).  Curiouser and curiouser.

---

### Post by amirhomayoun on 2009-09-23
Had the same problem yesterday. I already had v1.13. 'no_cookies' option worked for me too.
Today the problem is somehow solved! I did nothing!

---

### Post by chiccoch on 2009-09-24
same problem in my case. running on jaunty x64, kernel 2.6.31.

no luck with reinstalls or new SVN versions.

[http://swiss.ubuntuforums.org/showthread.php?t=1269146&page=2](http://swiss.ubuntuforums.org/showthread.php?t=1269146&page=2)

[https://bugs.launchpad.net/ubuntu/+source/checkgmail/+bug/433497](https://bugs.launchpad.net/ubuntu/+source/checkgmail/+bug/433497)

---

### Post by lordL on 2009-09-24
I've been experiencing the same issue, and I've also tried the "checkgmail -update" to no avail.

Here is the strange part:
- When my computer is connected to a wired network, Checkgmail works.
- When it's connected to a wireless network however, it doesn't.
- Also, if I have first used the computer on a wired network (where 
Checkgmail works), then enter sleep/hibernation, and then wake up the computer and connnect to a wireless network, Checkgmail works.  
- And if I reboot and connect to a wireless network right away, Checkgmail stops working again.

Is there some obvious explanation for this behaviour that I'm not seeing? Any thoughts?

---

### Post by stevo1977 on 2009-09-24
I have no explanation for others' problems; they are as mysterious to me as my own.  However, I tried running CheckGmail w/o the 'no_cookies' option and it worked fine.  I have yet to try it on my desktop, but I have high hopes.

No one has any idea what is happening?  Is Google just playing games with their protocol and not telling anyone?

>>>>>>>>>>>>>>>>>>
Edit: It is now working fine on my Ubuntu desktop as well.  As far as I know, I did nothing to make this happen.

---

### Post by craig10x on 2009-09-24
I still can't figure out why mine came back on it's own and is working fine now....
It is a real mystery...i am using a wired network, though.....

I re-installed it twice and on the second install it worked as if nothing ever happened...
STRANGE :confused:

---

### Post by craig10x on 2009-09-26
My CheckGmail Notifer went out again (same problem...doesn't recognize the sign in information)...Has anyone discovered an easy, working solution to this???? :confused:

---

### Post by craig10x on 2009-09-26
Now it's working again....all by itself.....sure is weird.... :P

---

### Post by kilaka on 2009-09-30
Perhaps some good info:
the application is working on my ubuntu 9.04 32 bit computer but on my 64 bit OS it is NOT working.

Don't know why is that.

---

### Post by kilaka on 2009-09-30
There is a forum on the project development site itself where the developer itself is posting:
[]("https://sourceforge.net/projects/checkgmail/")[https://sourceforge.net/projects/checkgmail/forums/forum/463626/topic/3405947](https://sourceforge.net/projects/checkgmail/forums/forum/463626/topic/3405947)

---

### Post by sailor2001 on 2009-10-04
alt/f2 and "checkgmail -no_cookies" worked for me (wireless)

---

### Post by lolwhites on 2009-10-06
Same issue for me this morning. The -no_cookies workaround did the trick, but I hope it gets resolved soon.

---

### Post by MyR on 2009-10-13
This is fixed in the development version.
Update to the latest SVN with this:
```
wget http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail
sudo mv checkgmail /usr/bin/checkgmail
sudo chmod +x /usr/bin/checkgmail
```
peace

---

### Post by nixie21 on 2009-10-13
> **MyR said:**
> This is fixed in the development version.
Update to the latest SVN with this:
```
wget http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail
sudo mv checkgmail /usr/bin/checkgmail
sudo chmod +x /usr/bin/checkgmail
```
peace

Did the above and can now log in...when clicking on the icon firefox opens but it NEVER remembers my password since yesterday!

---

### Post by KlinerDraken on 2009-10-13
running "checkgmail -update" will get you the newest version, that will fix some of the issues the program is facing 

[http://sourceforge.net/projects/checkgmail/forums/forum/463626/topic/3405947]("http://sourceforge.net/projects/checkgmail/forums/forum/463626/topic/3405947")

---

### Post by employeeno5 on 2009-10-13
> **stevo1977 said:**
> I have no explanation for others' problems; they are as mysterious to me as my own.  However, I tried running CheckGmail w/o the 'no_cookies' option and it worked fine.  I have yet to try it on my desktop, but I have high hopes.

No one has any idea what is happening?  Is Google just playing games with their protocol and not telling anyone?

>>>>>>>>>>>>>>>>>>
Edit: It is now working fine on my Ubuntu desktop as well.  As far as I know, I did nothing to make this happen.
I can confirm the same behavoir. My computers that are using an ethernet cable are fine. My ones using the same network wirelessly have the login issue.

---

### Post by craig10x on 2009-10-14
Was he able to correct the CheckGMail program?

If so, what would i need to do to fix it in mine (I am a relatively newbie linux user)
please outline the steps i would need to take....Thanks!

(In the meanwhile, i added the GMail Notify program...which interestingly enough, does work...though i do prefer CheckGMail if i can get it working normal again....) 

thanks in advance for any feedback :)

---

### Post by ertw1 on 2009-10-14
I got my CheckGMail working again by entering this into the console:

```
sudo apt-get install checkgmail && checkgmail -update
```

Though, ```
install checkgmail
``` seems kinda redundant if I already have it installed...anyways it worked for me.

---

### Post by KlinerDraken on 2009-10-14
> **ertw1 said:**
> I got my CheckGMail working again by entering this into the console:

```
sudo apt-get install checkgmail && checkgmail -update
```

Though, ```
install checkgmail
``` seems kinda redundant if I already have it installed...anyways it worked for me.

If you already have it installed you should only have to run "checkgmail -update" 

There are still some bugs being worked out by the programmer, caused by changes on google's end. 

[http://sourceforge.net/projects/checkgmail/forums/forum/463626/topic/3405947](http://sourceforge.net/projects/checkgmail/forums/forum/463626/topic/3405947)

---

### Post by craig10x on 2009-10-15
thanks guys...i will try that tomorrow....hope it will work for me :)

funny part is, the other program i added...which is GMail Notify...has no problem signing in at all....you would think that all the notifiers would be affected...

still, i do prefer the CheckGMail one because the icon on GMail Notify is a bit BIG and doesn't look quite as nice (LOL) ;-)

---

### Post by craig10x on 2009-10-15
Quick update....i tried it this morning....since CheckGMail Notifier was still on my applications, i tried just entering the update info in the terminal (checkgmail -update) and it updated the program and now it is working fine....

Using the "terminal" wasn't as scary as i thought it would be...actually, i did use it once before to get the latest version of Pidgin Instant Messenger....

Still, to make Ubuntu fully mainstream, it would be nice if everything could be done via GUI...and also if Ubuntu has some kind of downloading tool that would enable you to easily download programs directly from a website (a program that doesn't appear on Ubuntu's add/remove listings)...

And lastly, include all your codecs so you don't have to add them yourself...

Then, the "average joe" on windows would be able to make a super easy conversion from Windows to Linux....

Thanks again for your help!   :P

---

### Post by MyR on 2009-10-15
> **craig10x said:**
> Quick update....i tried it this morning....since CheckGMail Notifier was still on my applications, i tried just entering the update info in the terminal (checkgmail -update) and it updated the program and now it is working fine....
Great! checkgmail is one of my favorite apps.

> **craig10x said:**
> Using the "terminal" wasn't as scary as i thought it would be...actually, i did use it once before to get the latest version of Pidgin Instant Messenger....

Still, to make Ubuntu fully mainstream, it would be nice if everything could be done via GUI...
Checkgmail is not part of Ubuntu --  Ubuntu doesn't develop Checkgmail and as far as I know the developer does not use Ubuntu.

I took the liberty of adding a [feature request]("http://sourceforge.net/tracker/?func=detail&aid=2880199&group_id=137480&atid=738666") for updating to be added to the GUI.

> **craig10x said:**
> and also if Ubuntu has some kind of downloading tool that would enable you to easily download programs directly from a website (a program that doesn't appear on Ubuntu's add/remove listings)...
Such tools already exist.  
1. webmasters can add apt:// links to their sites so people can just click to install
2. developers can distribute .deb packages for easy installation to Ubuntu users
3. many applications have their own repositories (wine for example) that allow for easy installation and updates
etc.

> **craig10x said:**
> And lastly, include all your codecs so you don't have to add them yourself...
Ubuntu is based on free (as in freedom) software.  mp3 and other codecs are not free, open source software and are restricted by copyright law.  Ubuntu systems bought from Dell and HP have the codecs pre-installed.
Also some Ubuntu derivatives like Linux Mint have some codecs pre-installed.

> **craig10x said:**
> Then, the "average joe" on windows would be able to make a super easy conversion from Windows to Linux....

Thanks again for your help!   :P
Say what you will but Ubuntu is already a great choice for "the 'average joe' on windows".

peace

---

### Post by Enmi on 2009-10-18
> **MyR said:**
> This is fixed in the development version.
Update to the latest SVN with this:
```
wget http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail
sudo mv checkgmail /usr/bin/checkgmail
sudo chmod +x /usr/bin/checkgmail
```
peace

Thanks for this post! After trying (unsuccessfully) to use the -update tag, it wouldn't log in after repeated attempts... but this version works without a problem. I do hope that the fix ends up in the mainstream release so other users wouldn't have to run through this problem for much longer.

---

### Post by Lockheed on 2009-10-20
After updating to SVN old problem is gone, but new one appeared.

CheckGmail no longer logs in automatically when clicked on its tray icon (or Open new mail option). Before, I was taken directly into my email account. Now, however, every time I need to type in my password in the browser and it makes no difference what browser I use.

Anyone else encountered such problem?

---

### Post by stevo1977 on 2009-10-20
If you follow the conversation over at Sourceforge (link above, the creator and maintainer of CheckGmail is owenjm), it looks like this is an open problem.  No solution yet, I don't think.

---

