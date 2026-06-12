---
title: "Unprovocated logout when typing certain search string in Firefox"
date: 2010-05-13
forum: General Help
---

### Post by zainka on 2010-05-13
... Yes, I know it sounds strange, but never the less, I am able to reproduce this behaviour.

Case is that I was about to search for information aboute an 3M projector MP7740i. I opened Firefox and in the google search field i entered "MP774". In the moment i pressed number 4, screen went black and login appeared. 

I thought I had pressed sleep or something and logged in again. When trying to once again to enter the same search phrase the same thing happened. I write "MP774" and in the moment i press 4, i get logged out.

Now this could not be true so I tried it several times, just to realise that this actually happened. I then tried to change search engine and choosed "Ask". That worked as expected, giving me data aboute my search as normal.

Next logical thing then was to choose google search engine again. I entered the phrase... And i got locked out again.

I am running X-Ubuntu 10.04 with firefox 3.6.3, and I would be glad if someone could try to open a firefox session and try to enter MP774 into the google search field. 

A StartTrek captain would probable addressed this as a fluctuation in the space convey in the google universe, altering the ships main computer, but I call it a possible bug. I cant figure out what is happening, but something is fooling my laptop to logout.

Thanks in advance
Vidar

---

### Post by arkham on 2010-05-13
I have not yet taken the plunge and upgraded my Xubuntu install to 10.04, so all I can tell you is that this does not happen on FF 3.5.9 and 9.10

What it sounds like, though, is that typing that string (which triggers an auto-complete in the search bar btw) is causing the X windows server to crash/restart, hence you get a login prompt once it comes back up.  

Given that reproduction is possible with your set up you may have a genuine bug that needs to be reported to the X Server folks, for 10.04.  You can do it over on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bugs").  Be sure to have a look at a couple of other filed bugs and check out [the instructions]("https://help.ubuntu.com/community/ReportingBugs") if you have never done it before.  A cursory search did not reveal anyone with your exact symptoms, but then they might be filing them under Firefox, or elsewhere....

Some of the things that would be helpful to know would be the Video card you are using (and driver), if this happens with other common search terms that trigger an auto-complete, etc.

And, of course if you find out anything further or file a bug report, come back and give us some of the detail here so if someone else runs into it they know what is going on :)

A

---

### Post by RI2CA on 2010-06-06
So I'm not the only one! Since installing to Ubuntu 10.04, I've been experiencing the logout when typing in the Firefox search window. (I too use FF 3.6.3)

It happens with many different input strings and it's quite maddening. 10.04 is not ready for prime-time if it can't play nice with Firefox.

---

### Post by jwbrase on 2010-06-06
> **RI2CA said:**
> So I'm not the only one! Since installing to Ubuntu 10.04, I've been experiencing the logout when typing in the Firefox search window. (I too use FF 3.6.3)

It happens with many different input strings and it's quite maddening. 10.04 is not ready for prime-time if it can't play nice with Firefox.

How do you know it's 10.04's fault and not Firefox's?

---

### Post by Wbie on 2010-06-07
Same problem here. Would love to find a fix.

---

### Post by pbhj on 2010-06-07
Same problem here, presumably it's the rendering of the autocomplete list - I'm using Kubuntu (karmic) the Nouveau driver for my old nVidia geforce 2 GTS on an Athlon 1.1G.

---

### Post by sandyd on 2010-06-07
ill report this bug when I get home. meanwhile, since I dont have this bug, can you try these things? 1. type it in the actual google search engine. 2. try different combinations of the word. 3. run "cp /var/log/Xorg.log" ~/Desktop/xorglog" and upload the file thats on your desktop to your post? thanks!

---

### Post by calpopin on 2010-06-07
Hi 
I'm using Ubuntu 10.04 and Firefox 3.6.5
and i'm having exactly the same problem. 
when using this search field in firefox  i got a logout and it's systematic.
it can be done repetitively.

what's going on with firefox??
is there a way to stop the auto-completion to check if that the problem?

thanks for any help

calpo

---

### Post by macrohard on 2010-06-07
You can go ahead and me too the list too, lately its been happening every time I do a search in Firefox, running 10.04 too....

Not sure what or who is the culprit, but I have also been having issues as well with Firefox on my Windows XP laptop at work, same thing.

---

### Post by calpopin on 2010-06-09
Here is the solution:
open terminal and past :
sudo add-apt-repository ppa:bryceharrington/purple

it ask you for password and then acquire private keys and add a new source repository.
then open your update manager hit the check button and start the update from the bryceharrington part. should contain xcore_server or something near.

i had the same problem and it fixed it all for me.

all explanations in this bug report :
[https://bugs.launchpad.net/ubuntu/+s...er/+bug/539772](https://bugs.launchpad.net/ubuntu/+s...er/+bug/539772)

and the specific answer is at the post 29.
enjoy :p

---

