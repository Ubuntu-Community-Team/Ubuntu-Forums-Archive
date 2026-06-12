---
title: "gimp help browser missing, help opens in Terminal"
date: 2010-01-31
forum: General Help
---

### Post by L a r r y on 2010-01-31
I opened gimp 2.6 and hit the help menu, only to be told that the help browser is missing.  So I figured it would open in Firefox instead.  It opened in Terminal.  I think there may be some images in help, and the command line terminal does not do well at displaying images for some reason!  Therefore, I would like either to get the help browser installed or get help to open in the Web browser as it said it would.

There's another solved thread around here on this topic, and it said to go to Synaptic and put in a search for gimp-help.  All that does is bring up documentation files in every language available, and I already have the English help.  It opens in Terminal, however.

I looked for gimp browser and gimp help without the hyphen.  And I looked for gimp.  Downloaded a few things I thought might have some bearing and closed gimp and re-opened it.  But I still get help in my terminal.  The one thing I did not do, and I will do after I post is restart the session, either by logging out and back in or by restarting the computer.

I will come back and post the result.

---

### Post by L a r r y on 2010-01-31
Log out and Log in, and start gimp.  Help still comes up in the terminal.  Anyone have any ideas?

Ubuntu 9.04, gimp 2.6 with version 2.4 English help.

---

### Post by L a r r y on 2010-02-05
Bump

Anyone?> **L a r r y said:**
> I opened gimp 2.6 and hit the help menu, only to be told that the help browser is missing.  So I figured it would open in Firefox instead.  It opened in Terminal.  I think there may be some images in help, and the command line terminal does not do well at displaying images for some reason!  Therefore, I would like either to get the help browser installed or get help to open in the Web browser as it said it would.

There's another solved thread around here on this topic, and it said to go to Synaptic and put in a search for gimp-help.  All that does is bring up documentation files in every language available, and I already have the English help.  It opens in Terminal, however.

I looked for gimp browser and gimp help without the hyphen.  And I looked for gimp.  Downloaded a few things I thought might have some bearing and closed gimp and re-opened it.  But I still get help in my terminal.  The one thing I did not do, and I will do after I post is restart the session, either by logging out and back in or by restarting the computer.

I will come back and post the result.

> **L a r r y said:**
> Log out and Log in, and start gimp.  Help still comes up in the terminal.  Anyone have any ideas?

Ubuntu 9.04, gimp 2.6 with version 2.4 English help.

---

### Post by warfacegod on 2010-02-05
Have you tried you tried completely reinstalling GIMP?

---

### Post by L a r r y on 2010-02-07
> **warfacegod said:**
> Have you tried you tried completely reinstalling GIMP?

Thank you for that suggestion, for as a matter of fact I had not.  I went ahead and did a complete uninstall and reinstall without a solution to *Help* displaying in the Terminal.

[SIZE="4"]Step-by-step:[/SIZE]

I uninstalled gimp.  Logged out and back in.

I ran Ubuntu Tweak's package cleaner and among other things, removed gimp configuration files.  Logged out and back in again.

No gimp on the applications menu under Grapics anymore.

I added gimp from the add/remove menu, and fired up gimp.

I hit the help menu, selected help from the menu **and it came straight up in Terminal**.
I would like for it to come up in Firefox or its own help browser, as I believe there are images involved, and they don't display in the command line Terminal.

Gimp 2.6 - where do I look now?  Thanks in advance!

---

### Post by warfacegod on 2010-02-07
Do you have gimp-help-common installed?

---

### Post by L a r r y on 2010-02-11
> **warfacegod said:**
> Do you have gimp-help-common installed?

Yes.  I marked it for re-installation.  Started gimp and Help still opens in the Terminal.  What next?

And thank you for your time!

---

### Post by warfacegod on 2010-02-11
Try Synaptic. Edit in the top left and select Fix Broken Packages.

---

### Post by mechro on 2010-02-11
In Gimp, what does it say under **Edit > Preferences > Help System**?

---

### Post by L a r r y on 2010-02-11
> **warfacegod said:**
> Try Synaptic. Edit in the top left and select Fix Broken Packages.

OK.

"Successfully fixed dependency problems" on the status bar, but had no effect on gimp help behavior.

---

### Post by audiomick on 2010-02-11
Can't advise you on the gimp help, but look at this
[http://gimp-savvy.com/BOOK/index.html](http://gimp-savvy.com/BOOK/index.html)

---

### Post by L a r r y on 2010-02-11
> **audiomick said:**
> Can't advise you on the gimp help, but look at this
[http://gimp-savvy.com/BOOK/index.html](http://gimp-savvy.com/BOOK/index.html)

Thank you for the book.  I may find some good reading there.

Meanwhile, back at the ranch, I looked in the Synaptic again, looked up gimp-help.  There I figured I'm looking at the file name and started poking around in the computer to find gimp-help stuff.  In /usr/share/gimp//2.0/help/en/index.html is the opening web page of the instruction manual, so I placed alauncher on the desktop to run firefox /usr/share/.../help/en/index.html.

Now that I was able to see the instruction manual, I did some reading and started poking in my Preferences in gimp.

I found the bug-a-boo:  I was set to open help in the web browser, which was called a sensible browser instead of firefox.

I changed the name to firefox and I am now opening from the help menu in Firefox.

Methinks it's leftovers from having installed Firefox 3.5 unbranded version, called "A browser."

This Firefox 3.5 precursor had some misfit moments in my version of Ubuntu, and I still have "A Web browser" showing up in my open-with choices, even though I have taken it out in favor of Firefox 3.0.

Thank you for your help.  It has pointed my way through possible solutions to the problem!

I declare this thread solved.

---

### Post by mechro on 2010-02-11
Poo! That's the direction I pointed you in! :D

---

