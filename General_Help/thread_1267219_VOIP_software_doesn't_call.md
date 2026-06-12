---
title: "VOIP software doesn't call"
date: 2009-09-15
forum: General Help
---

### Post by andrew2221 on 2009-09-15
Hi everyone.. 

I am a newcomer in this forum, and I don't know if I am posting at the right place. Not so newbie in Linux, generally, anyway.
My problem is quite particular, I think, so don't judge before reading. I will try to be as clear as I can.
I am working in a call center. At this moment, we have Windows on the workstations, using OpenOffice 3.1.0 (for the contact list - XLS) and X-Lite as soft phone (for calling). The system is quite simple. In the contact list there is a column, with the phone numbers, which is a hyperlink, actually it is a SIP URI - the formula is like that: =HYPERLINK((CONCATENATE("sip:";$J401));$J401)) - where J is the column that contains the actual phone number. Until here, everything is fine, works great.
We want to pass to Linux Mint. Of course, before, I have to be sure that everything is work as it should, since I am in charge with this. So. I installed Linux Mint 7, official release (probably I will need XFCE version, but it shouldn't be different anyway), and after, 6-7 soft phone software (mostly known ones). The one I found that is suitable for our purposes is SFLphone (latest version). But!

When I open the same file (which worked just fine in Windows), with OO in Mint, and I click on a number (the SIP URI), nothing happens. I started to make some researches, and I found out the way HYPERLINK works (detecting a link it passes the control to the browser, and the browser should take care of the rest - starting the right software and making the call), but this is not happening. Since it's possible to run virtually any program from the computer with the same technique, I tried to run a program as a link (with the full path) to see if it's acting the same way, and all it did was opening the browser. Nothing else. Strange is, that this time at least the browser opened, meantime clicking on the number, not even that. I tried, also, to tweak a bit SFLphone's settings, as I read on the official forum, but it didn't helped.

Exporting the database in HTML format is not really an option, since we have to change many things in that list, at every contact (row). But opening the exported HTML, in Firefox 3.0, I managed only to open SFLphone, not actually making the call. 

Could be the libpurple, could be Firefox, could be an OO issue, or the SFLphone itself, or, it could be me.. But I did not found out any solution that could work. Since it could be related to anything, I did not knew where to post this problem.
I can only hope that someone could help me. I know, it's about Mint, but it should be the same for Ubuntu too. Thank you in advance.

---

### Post by jonobr on 2009-09-15
Hello

Welcome to the forum.

Thats an interesting puzzle for a first time post.
Im not sure if I can help much but heres what Im supposing walking through this logically.
Im wondering the following.
If you replace your string with a regular link,

eg
```
=HYPERLINK("http://google.com","test")
```

Does it open the way you expect with the browser you expect?
Does it go to google,? Does it open a w3m page or something else?
If that works the way it is supposed to then I would open the browser it invokes when the link is clicked.

In the browser , enter the URI thats received from the OO application,
When you hit enter, does it open the client?
Does it place the call?

DOes it recognize the sip URI and do something meaningful with it?


Im also guessing the sip clients on the machine work and that is not an issue.


I think taking the above approach should narrow down where the problem lays

---

### Post by andrew2221 on 2009-09-15
[SIZE=2][COLOR=Red]Hi.. And thank you for trying to help.. You can read my answers down here:[/COLOR][/SIZE]
> **jonobr said:**
> Hello

Welcome to the forum.

Thats an interesting puzzle for a first time post. [SIZE=2][COLOR=Red]- I know.. :)[/COLOR][/SIZE]
Im not sure if I can help much but heres what Im supposing walking through this logically.
Im wondering the following.
If you replace your string with a regular link,

eg
```
=HYPERLINK("http://google.com","test")
```Does it open the way you expect with the browser you expect?[SIZE=2][COLOR=Red] - Yes, it does open Firefox (predefined browser) if it wasn't open already, otherwise it opens a new tab[/COLOR][/SIZE]
Does it go to google,? [SIZE=2][COLOR=Red] - Yes, that's correct.[/COLOR][/SIZE] Does it open a w3m page or something else? [SIZE=2][COLOR=Red]- Sorry, I don't know exactly what is a w3m page[/COLOR][/SIZE]
If that works the way it is supposed to then I would open the browser it invokes when the link is clicked.

In the browser , enter the URI thats received from the OO application,
When you hit enter, does it open the client? [SIZE=2][COLOR=Red]- Originally not, but asked what I want to do.[/COLOR][/SIZE]
Does it place the call? [COLOR=Red][SIZE=2]- No, not at all.[/SIZE][/COLOR]

DOes it recognize the sip URI and do something meaningful with it? [SIZE=2][COLOR=Red]It is asking me which application should it start (option between purple-url-handler and sflphone(because I gaved once already the path to find the app) - and one more thing. It doesn't look if the app was already opened, meaning if I go to FF's adress bar and write something like sip:[0123456789]("sip:0123456789") and hit Enter, ok, it asks if it should open with SFLphone, I say yes, so the app opens, but not placing the call. Withouth closing the app, hitting enter again in adress bar, it opens an other instance of app, so now I have 2 running apps, etc.)[/COLOR][/SIZE]


Im also guessing the sip clients on the machine work and that is not an issue.


I think taking the above approach should narrow down where the problem lays

[COLOR=Red][SIZE=2]I also tried to add in FF to about:config the following: [/SIZE][/COLOR]network.protocol-handler.app.sip = /path/to/SFLphone [SIZE=2][COLOR=Red]as string (where of course, [/COLOR][/SIZE]/path/to/SFLphone [SIZE=2][COLOR=Red]is the path to the app, along with it's name) it doesn't helped. Tried to set it as  boolean, no changes.
[/COLOR][/SIZE][SIZE=2][COLOR=Red]One more thing. In Windows, the browser itself is bypassed, meaning that even if the browser is closed, not running, the call is placed in the right way. So actually it doesn't need the browser at all, at first sight (probably becouse of the registry?!).[/COLOR][/SIZE]
[SIZE=2][COLOR=Red] Thank you again for trying to help..[/COLOR][/SIZE]

---

### Post by jonobr on 2009-09-16
Hello


I tried this on Firefox , switchweasel and seamonkey and am getting exactly the same as you.
Im getting the dialog box open, I put in the application I want it to open,
but the dang thing just does not appear to want to work.

Im thinking that windows firefox recognizes the sip prefix and knows what to do with it.
It appears linux firefox and its variants dont seem to be doing what you want it to do.

If thats the case, then Im thinking thatthe operation of Firefox on windows versus the operation on linux differ, and technically thats a bug.

Would you agree?

---

### Post by andrew2221 on 2009-09-18
Hi, and sorry for the delay, I've had to work some more.. Well, I would agree with you.. But! I found out some other things meantime. As been suggested by someone else (on other forum) I tried a workaround using gconf-editor and Ekiga, but actually it didn't worked as expected, and tried the same thing with SFLphone, with no luck.

I found a way to make it functional, anyhow. Managed to install X-Lite via Wine, and OpenOffice for Windows, also, via Wine. As expected, it worked out of the box (well, almost), without  any browser present. So, my thoughts were right. The browser is bypassed totally, like I told you. Just that X-Lite via Wine is very unstable, plus sound issues sometimes, so that's not a walkable path, talking in long-term. I tried 4-5 other Windows applications (soft phones) in Wine, none worked as they should (none reacted to the SIP URI, and all had sound issues).

Well, if you have something in your mind, I would really appreciate if you could share it with me/us.

Thank you again.

---

