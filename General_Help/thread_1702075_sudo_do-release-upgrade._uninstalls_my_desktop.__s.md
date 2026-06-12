---
title: "sudo do-release-upgrade. uninstalls my desktop.  sigh"
date: 2011-03-07
forum: General Help
---

### Post by jtwdyp on 2011-03-07
[SIZE="2"]Hello. First let me say that for the most part I'm happy with the results of using do-release-uprade to go from Karmic to Lucid. But I'm puzzled by the process of deleting obsolete packages... [/SIZE]

[SIZE="1"][i]Note, I follow the "server" upgrade instructions at [http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade) rather than the "desktop" instructions because: 

A) I'm more comfortable trying to follow cli based instructions than trying to wrestle with my mouse pointer well enough to click on the right buttons. (especially with something I can't afford to mess up such as a system upgrade.)

B) I'm not comfortable with leaving X running during "major upgrades"[/i][/SIZE]

[SIZE=2]I suspect that it has to do with the fact that the process automatically disables 3rd party repositories by commenting them out in the sources list.
I have exactly to such repos. The one for e17 (my primary desktop environment) And the one for opera. (My preferred browser) Both of which got commented out when I used this process to update my desktop to Lucid. And again (more recently, when I got around to updating the laptop) In both cases the process removed some "Obsolete" packages including e17. This, I think because it njo longer considered the e17 repository as valid?? Yet in both cases it also did NOT decide that opera was obsolete. Even though it's repository was also commented out.

I'm curious why it dumps one and not the other. But more than that, I'd like to know (for next time) if there is a way I can safely stop the "do-release-uprade process before it wipes out my desktop. so I can re-enable the e17 repository. And them somehow resume the upgrade process in such a way that it still removes any other obsolete packages, but leaves e17 alone???

[/SIZE]

-- 
JtWdyP

---

