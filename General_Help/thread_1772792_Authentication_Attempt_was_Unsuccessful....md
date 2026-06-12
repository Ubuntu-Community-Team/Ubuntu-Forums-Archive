---
title: "Authentication Attempt was Unsuccessful..."
date: 2011-06-01
forum: General Help
---

### Post by GutsyVirgin on 2011-06-01
I've searched far and wide and I can't seem to find an answer to this problem. I get the following error message whenever I try to install an app using the "Ubuntu Software Center." Ironically though, I can install the same app via aptitude or apt-get without issue.

[IMG]http://img34.imageshack.us/img34/1803/ssautherror.png[/IMG]
*The glitchy-ness of this is due to the error appearing and disappearing about 8-10 times in the blink of an eye. I was barely able to screenshot it, lol.*

Possible cause?
Once I was trying to chown my phpMyAdmin folder on my root purely for testing purposes and I may have accidentally entered some stupid command, realizing it after about 5 seconds of it running when I wondered why it was running so long. As I recall, I was IN the phpMyAdmin folder in Terminal and I ran (if memory serves) the following command thinking it would apply to my CURRENT directory. I know, I know...
<-- NOOB :P

_Ooopsy Command_:
**sudo chown -R matthew /**
ROFL!! (doh, how do I revert the permissions to their defaults? Can this be done?)

I really appreciate any help I can get. This has been quite a booger and a nuisance to deal with. :(

**EDIT**: As it turns out, this appears to be an issue when attempting to perform any sort of action requiring root authentication. It happened when trying to "Unlock" gdmsetup in the dialog. Also when running Update Manager.

**EDIT**: Ok, I finally found the solution, lol. One-hour to reinstall and reconfig :P
Also, I found this interesting link. Apparently this guy wrote a [Ruby script]("http://askubuntu.com/questions/43621/what-if-i-accidently-run-command-chmod/43636#43636") to recursively log all chown & chmod info in the Filesystem and another to restore them all. **If someone tries this, I'd like to know how it turns out** :)

Cheers,
~Matthew

---

