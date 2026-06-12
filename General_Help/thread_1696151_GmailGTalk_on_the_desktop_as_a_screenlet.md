---
title: "Gmail/GTalk on the desktop as a screenlet"
date: 2011-02-27
forum: General Help
---

### Post by patrick_the_fat on 2011-02-27
Hello,

As you may know, Google provides the ability to make and receive calls for free (up until 2011) using your Gmail account with your microphone and speaker.

I have found a way to incorporate the calling features of Google Talk into the Linux desktop as a widget (assigned to a hotkey), which loads automatically on startup.  The goal is to have a fast and easily accessible interface that we can use to make and receive calls from Gmail all the time, from the minute your desktop appears.

Feel free to try it out and tell me what you think. There is a security issue I need to work out.  The password is stored directly in the script, accessible to the non-super user and the code can probably be written better.  I have an idea of creating a separate user for this screenlet, changing the owner of the script to the same as the screenlet, and denying other user access to the script to tighten the security of it, but again, there is probably a more secure way to do it and at this point I don't know.  Please read below, and tell me of any ideas or suggestions you might have?

On startup, the script actually simulates pressing the keystrokes necessary to bring up the Webframe screenlet, sign into Gmail, and activate the call window without you pressing a button. (The script simulates pressing F9 to activate the widget, the keys for entering the username, tab, the keys for the password, the enter key, then g+p in Gmail to bring up the call window and F9 again to hide the widget.)

- install screenlets and xdotool from the repository
- install Webframe from screenlets.org
- run ccsm, search 'widget', turn on Widget Layer (make sure F9 is assigned)
- run screenlets, find WebFrame, click Options button and set options to Sticky, Widget, and Always on top
- start (and autostart) Webframe, press F9 to toggle visibility, right-click the border and click Properties/Options/Webframe, then set Home page to [http://mail.google.com/mail/](http://mail.google.com/mail/)
- Restart the screenlet to make sure it goes to Gmail by default.  It should now be at the Gmail login screen when you press F9.
- create a script gtalk-screenlet.sh to send the appropriate key strokes to the call window:

#/bin/bash
sleep 40 &&
xdotool key "F9" &&
sleep 1 &&
xdotool type "gmail-username" &&
xdotool key "Tab" &&
xdotool type "gmail-pw" &&
xdotool key "Return" &&
sleep 4 &&
xdotool type "gp" &&
sleep 6 &&
xdotool key "F9"

- next, mark this script as executable and add it to Startup Manager

For some reason, the Webframe requires that I log into Gmail every time the computer turns on.  No big deal, but there has to be a better way of going about this?

Here's an idea.. temporarily make the widget transparent, toggle the busy cursor signal and temporarily disable the mouse/keyboard, send the keypresses, hide the widget layer, and revert back to normal?  Or is there a more-direct way of getting "logged in" to the widget?  

This should probably be a widget of its own (I noticed the Gmail notifier directly asks you for your username and password).  I am willing to dedicate some time to a little scripting and perhaps a little building for the repo if we can all get together!

patrick_the_fat

---

### Post by nickleboyblue on 2011-02-27
It should be possible to send the values for the login name and password, and any other necessary information, directly instead of simulating keystrokes.  The advantage of doing this is that you can do things in a much more "linux-ish" way by storing the password in an encrypted password file and the other information in a configuration file that the script reads.  This would also give the script direct control over the call to be made, and it would make it possible to include support for evolution contacts.

Of course, this approach might not work outside of POP and smtp, but you can find out if you look up Google api's.

If you're looking to the future at all, consider programming an interface in the Unity Launcher.  You could potentially make a phone call to a contact in two clicks form a Unity icon's menu.  If you ever get around to that, let the rest of us know, because I'm sure it would be a smash hit.

---

### Post by patrick_the_fat on 2011-02-27
Bump..

---

### Post by polardude1983 on 2011-03-01
I would love to have this, but unfort I cannot help :/

---

### Post by patrick_the_fat on 2011-03-02
Let me clarify that the script is working great on my machine.

I am aiming to get others to test it out and hear what they have to say.  I believe that many people will find this script very useful and also, I believe there is probably a much better way to write the script (although my first attempt yielded great results!)

Perhaps you can test it out and post a comment?  As far as I know, I am the only one using this mod and I don't know if it's going to work well for everybody else.

---

### Post by polardude1983 on 2011-03-03
I would love to help out anyway I can. Even if it's just using it on a different machine and saying it works for me.

---

### Post by nickleboyblue on 2011-03-03
Same here.  If you can get a link to it or just post it somehow, I'll test it out.  Let us know!

---

### Post by patrick_the_fat on 2011-03-03
Dude! I posted the instructions.  All you have to do is follow them.  It's literally the first post.

---

### Post by polardude1983 on 2011-03-04
yeah lol. I got it. and works fine. i love it.

---

### Post by patrick_the_fat on 2011-04-20
Here's an important update,

The developer of the Webframe screenlet released version 3 (and also version 2), and now Gmail forces the basic HTML view, which does not support Google Talk.  I have included the original v0.1, as I can no longer find it online.  It seems like versions 2 and 3 have the same bugs as version 1, but ironically, they do not seem to support spoofing.. Instead, the webframe forces using mobile versions of web sites, including Gmail.  For now, I am surely sticking with v0.1! It's a good thing I still had it on my system. You can install this tar.gz instead of the one online, simply through the Screenlets manager.

Good luck with it!  Free calling until 2011!  I would love to hear comments.



EDIT:
I believe the v0.1 comes with the standard screenlets-pack-all.. Try that first, and if it doesn't work, the attachment is here.

---

### Post by patrick_the_fat on 2011-04-23
Ooh! I got it.

Load Gmail in your web browser and switch to Basic HTML.  Then you can copy the link to Standard View and set that as your Webframe home page (rather than mail.google.com).  It does not matter which version of Webframe you are using.

Is anybody else having trouble with the Show/Hide Widget Layer?  Then again, is anybody reading this?

---

### Post by mcurran on 2012-01-05
Took my idea dude.  Look forward to messing with ur stuff.  I'll keep you posted w/ anything I might be able to add...  obviously I'm sure you've checked out the google-code repo for gtalk, gvoice, gcall, etc?...  That route might be better than a simple copied webpage, maybe some python devs can contribute to building a little ui around gvoice.  Right now, I'm still having periodic trouble making calls from terminal, but wicked cool to setup bash scripts and shut down people's phones who **** u off :).

---

### Post by patrick_the_fat on 2012-01-11
Actually-I haven't, I didn't have a clue. I was hoping to gain some support by sharing this, and I will surely do the research. I actually made a re-post [here]("http://ubuntuforums.org/showthread.php?p=10777025") to promote my idea.

And, for my assurance, Gmail's amazing VoIP calling feature is staying free [until the end of 2012]("http://www.pcworld.com/article/246144/gmail_calling_stays_free_through_2012.html").

Thank you, I am fairly novice to the Linux Community, but alike I may make some contributions with your support.

---

