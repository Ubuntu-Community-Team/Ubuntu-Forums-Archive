---
title: "xubuntu wont finish boot after peerguardian pgld"
date: 2012-09-24
forum: General Help
---

### Post by Lobstercat on 2012-09-24
Greetings!  Okay, first let me say this is a fairly new instal so if all else fails I can just re-install but if possible I would rather learn something.  I have long been a user of PeerGuardian & PeerBlock under windows.  Combined with NoScript and my lack of dangerous browsing habits my pc is very safe.  So I was looking somewhere at something else & saw that it had been finally ported to Linux, instead of using MoBlock so I decided to give it a try.  Now I also installed a few other things through Synaptic but since PG is the only one that wasn't and needed to be put together I will assume that it is the culprit.

Now when I boot up it goes to the login screen (first difference - I had it set up to just log in with no grub or password) and after I enter the password it blips a few times & we're back at the password screen again.  I ran boot repair & installed Grub & did fsck & looked for broken packages & re-installed xubuntu-desktop & installed kubuntu-desktop & checked for dependencies.  Surely this would overwrite any problems but no such luck.  When it blips I saw there was some writing but it was only there for a fraction of a second so I used the video camera & paused on the frame.  Here it is:
* Starting BitlBee. IRC/I'M gateway: bitlbee.
* Starting ClamAV daemon clamav
* Starting ClamAV virus database updater freshclam
* Starting PeerGuardian Linux pgld
Speech-dispatcher disabled:  edit /etc/default/speech-dispatcher
* Starting the Winbind daemon winbind
* starting Mail Transport Agent (MTA) sendmail
Saned disabled:  edit /etc/default/saned
* checking battery state

And there you have it. It is a Acer Aspire ONE.   It had Windows XP on it before but now just has Xubuntu 12.04.  Also had an issue with it no longer turning the wifi radio on too.  Although there is no other OS the disk my have some bad sectors so the Linux is still at the end of the disk with an empty partition at the beginning.  Thank you for your time & thoughts or ideas.  Need more info?  Just let me know.  Have a great day!

---

### Post by Bucky Ball on 2012-09-24
Would you be willing to kill ClamAV and give that a shot? It could be that as can be problematic ...

You could try reinstall as last resort and install the Peer program *first*, before *any* other security stuff and just get that working properly. Then add what you need and see when it crashes. The way it is might be hard to tell what's crashing things.

```
* Starting BitlBee. IRC/I'M gateway: bitlbee.
* Starting ClamAV daemon clamav
* Starting ClamAV virus database updater freshclam
* Starting PeerGuardian Linux pgld
```PS: You're using Linux so you're off to a pretty safe start ... curious as to why you'd want ClamAV *and* Peerguardian both, though. Are you also connecting through a router? If so, bordering on overkill. ;)

---

### Post by Lobstercat on 2012-09-25
Thanks.  I will give it a try.  As to why, of course I have both running on my windows pc and was just curious.  Even now, I could easily do a fresh install & I wouldn't lose much but that would defeat the purpose of learning.  Thanks for your help - I'll let you know if it works!

---

### Post by Bucky Ball on 2012-09-25
Cool. Tweak away and enjoy the learning curve! Just make sure you have your valuables backed up. ;)

You don't need much on Linux (I've never used anything). Have a dig and see what's required to achieve the level of security you're after. Doubtful same as your Win install.

---

