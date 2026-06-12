---
title: "Sending Picasa Pictures via Email using Thunderbird"
date: 2012-01-04
forum: General Help
---

### Post by Quarkrad on 2012-01-04
Newbie running 11.10 (with Gnome classic desktop), Picasa 3.9.0 (build 135.8000, 0) for Linux and Thunderbird 8.0.  I am trying to action the feature in Picasa to send pictures to a 3rd party via email -    at the bottom of the Picasa screen there is an email button that will enable this.    If you try this, instead of Thunderbird opening an email to send, with the picture attached, a (Thunderbird) window pops up  that says  **An error occurred while creating a message compose window. Please try again.**  I have found a bug reference to this on Launchpad but also a 'google' work-around at **[http://www.ubuntugeek.com/mailing-photos-from-picasa-3-in-thunderbird-3.html](http://www.ubuntugeek.com/mailing-photos-from-picasa-3-in-thunderbird-3.html)**.  I put the work-around in place and at the same time upgraded Picasa to version 3.9 via these instructions **[http://askubuntu.com/questions/86452/how-would-i-install-picasa-3-9](http://askubuntu.com/questions/86452/how-would-i-install-picasa-3-9)**.  I support my mother-in-laws machine via a remote desktop session and have, as far as I can, maintained a duplicate install of her machine on mine in Virtualbox. (I actually run 10.10 so use Virtualbox to give me her 11.10 environment).  I installed the work-around and upgrade (3.9) on my Virtualbox 11.10 system I found it worked like a dream, I can automatically send a picture as an email attachment via Thunderbird by clicking on the email icon at the bottom of the Picasa screen.   Thing is &#8211; having got it working in my Virtunal box machine it does not work on my mother-in-laws machine - and I do not know why.  On her machine, clicking on the Picasa email button launches Thunderbird as an email to **Send** but the picture is not attached; where as on my machine I get the Thunderbird **Send** mail window but the picture is there as an attachment.  I have checked the version numbers and config settings on both machines and they are identical.  Both machines have the same repos/servers and are up-to-date / upgraded.  So it works on my Virtualbox machine but not hers ????  Any advise on what else to check would be most appreciated.

---

### Post by Quarkrad on 2012-01-08
Just installed Thunderbird 8 and Picasa 3.9.0 (builds 135.8000 and 135.8100) onto my winxp side and it work perfectly - something on the Linux side is not quite right.  Strange because it does work as per original post - just cannot replicated it no matter what I do.

---

### Post by Quarkrad on 2012-01-10
I have got it working in my test version of 11.10 by re doing the script available at: [http://www.ubuntugeek.com/mailing-photos-from-picasa-3-in-thunderbird-3.html](http://www.ubuntugeek.com/mailing-photos-from-picasa-3-in-thunderbird-3.html). Although the script is the same on both machines something must have happened when I first installed it - now I can send/attach pictures via the email button on both 11.10 environments.  However, it is still not working on my 10.10 machine.

---

