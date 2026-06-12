---
title: "Thunderbird"
date: 2011-05-04
forum: General Help
---

### Post by KirkS on 2011-05-04
Hello,  maybe this has been covered an umpteenbillion times, but I am wondering why Ubuntu Software Center has Mozilla Thunderbird as a possible download for e-mail, when it won't actually GET the e-mail.  First off it sets itself up as an i-map account, which I do not have.  My account is POP3.  Thunderbird doesn't want to notice that little fact.  Second, why can't I Import Settings from my Evolution account.  I don't mind Evolution, but I like (or use to Like) Thunderbird better.   I have tried everything I know how to do, but I just can't get Thunderbird to work on Ubuntu 10.10.  Any help would be much appreciated.  Thanks. :confused:

---

### Post by leclerc65 on 2011-05-04
Thunderbird works perfectly for my Gmail account, nothing to setup.
It does not work for Hotmail nor Yahoo (unless you want to pay for premium Yahoo).
I never use my ISP email account because I would loose the freedom (to change ISP when they jack up price).

---

### Post by raziel09 on 2011-05-04
Firstly what type of email account are you trying to set up?

Which version of Thunderbird do you have installed; i believe that i have the latest one (3.1 i think) and when i go to set up an email account it asks for an name - the email address (mine is an hotmail one which works fine and has done since version 2.4 with no add-ons) and your password and then when you click next it then automatically configures it for you with the pop3 servers if required.


On an side note it also work fine with my AOL account which uses IMAP - i can view both and send\receive fine.

---

### Post by zacktu on 2011-05-04
I just went through the first three steps of setting up a new Thunderbird account for my TB 3.1.8.  Here they are:

1. File/New/Mail Account
2. Enter your name (will show up in your email header), email adddres, and password; select save password if you want; press Continue
3. While TB is searching for your email server (as IMAP), press Stop.  You now are in a more manual mode, and you can use the pulldown to change to POP.

---

### Post by KirkS on 2011-05-04
OK, first off, GMail is an iMap account, so Thunderbird loves it, and takes it in with no problems.  My email account is POP3, and I use to be able to configure Thunderbird to use POP3, when I had my system platform as Microsoft Windows.  Ubuntu is a whole different beast, evidently, which is one of the reasons I love it.

Zactu, I tried what you suggested, but it didn't work, so I uninstalled Thunderbird, and reinstalled it, thinking it would go through the same steps as you list.  NOT!  For some stupid reason I forgot that uninstalling an application doesn't remove the file created for it, so if it is reinstalled it has all of the configuration info from before.  In other words, Thunderbird just latched onto everything I had done on the first installation, and wasn't any changeable than before.  Now, I tried to Remove all data related to Thunderbird, so I could start from scratch, but it seems I don't have the Permissions needed to do those acts.  I use to know how to gain Permissions on Windows, but Ubuntu is different, and I have yet to figure out how to get the Permissions, and make the System understand that I (the administrator) have the Permissions.  Any suggestions? :-({|=

Oh, I forgot, the version I'm working with is 3.1.8.

---

### Post by Rasa1111 on 2011-05-04
I don't know..
 Thunderbird works perfectly with whatever email address I throw at it,
GMX, yahoo, gmail, whatever. 

All i have to do is give my email info, and thunderbird does the rest, without fail. 

It's only worked this good for me since 10.10, but it works the same in 11.04 also, quite well. 

Wish I could help.
good luck.

---

### Post by zacktu on 2011-05-04
I don't see why your existing profile would affect anything, so it shouldn't require that you uninstall TB.  I already have several IMAP accounts set up in my TB installation and just experimented with adding a new one.  It worked as I described.  

Sometimes you have to specify parameters as provided to you by your email server.  From the original post it appeared that there was a problem specifying POP rather than IMAP.

I'm using Thunderbird 3.1.8 with Ubuntu 10.10.

---

### Post by KirkS on 2011-05-05
> **zacktu said:**
> I don't see why your existing profile would affect anything, so it shouldn't require that you uninstall TB.  I already have several IMAP accounts set up in my TB installation and just experimented with adding a new one.  It worked as I described.  

Sometimes you have to specify parameters as provided to you by your email server.  From the original post it appeared that there was a problem specifying POP rather than IMAP.

I'm using Thunderbird 3.1.8 with Ubuntu 10.10.

I must be about the stupidest person on the planet.  You were right, I didn't have to uninstall Thunderbird at all.  I just had to remove the first account that got set up as iMap.  After I figured that out, and did it, I created a new account which immediately detected my POP3 account.  I must have interfered with the original setup, but I honestly don't know how.  Whatever, Thunderbird is running fantastically now.  Thanks to everyone that helped me out with this.  It was good just to discuss it, and get me thinking about things to try.........Now, can anyone tell me if I need to keep Evolution, or can I uninstall it without causing troubles?  :D

---

### Post by Rasa1111 on 2011-05-05
Glad you figured it out! :)

and no worries.. i know some truly "stupid' people..
and you seem nothing like them. lol

This stuff is just confusing sometimes!  ;) 

Regarding the removal of evolution.. 
I don;t want to suggest you remove it, you know.. "just in case"..lol
But speaking from my own personal experience..
I always remove it, with no ill effects. 

 i havent done so in my 11.04 install yet..
but every other install I have it removed. 

<3

---

### Post by Irihapeti on 2011-05-05
I've got a slightly oddball ISP email account that doesn't use IMAP. I used to find the automatic account setup in Thunderbird highly annoying - still wish it could be overridden more easily.

Nowadays, if I'm installing Thunderbird on a new installation, I disconnect the machine from the internet first. Then it can't go jumping on-line and trying to grab stuff when I don't want it to.

---

### Post by Off Topic on 2011-05-05
Is it really that hard to hit the Manual Setup button?

---

### Post by Irihapeti on 2011-05-05
> **Off Topic said:**
> Is it really that hard to hit the Manual Setup button?

You've got to be darn quick, and a few times I had not been quick enough. Then the quickest way to deal with the mess is to delete the faulty account profile and start again.

I wish there was an option to hit "manual" before even starting with the account setup.

---

### Post by Off Topic on 2011-05-05
I set up 3 accounts today.  The 2 POP accounts I had to add manually,  it isnt that difficult.

---

### Post by Rasa1111 on 2011-05-05
> **Off Topic said:**
> I set up 3 accounts today.  The 2 POP accounts I had to add manually,  it isnt that difficult.

Neither is humility.

---

### Post by Off Topic on 2011-05-05
Actually humility is hard work.  Arrogance however even a cave man can do.

---

### Post by Rasa1111 on 2011-05-06
lol

better not let any cavemen hear you say that...
They don't take to it kindly! :lol: lol

---

### Post by KirkS on 2011-05-06
> **Off Topic said:**
> I set up 3 accounts today.  The 2 POP accounts I had to add manually,  it isnt that difficult.

It isn't that difficult, IF you know what to watch for.  I was kind of caught off guard on my first attempt.  You really shouldn't abuse yourself by calling yourself names, like "caveman".  [-X :)

---

