---
title: "How to get ahold of the Ubuntu developers? I wrote an improvement!"
date: 2011-10-16
forum: General Help
---

### Post by yanom on 2011-10-16
Soo I wrote an updated version of /usr/bin/cautious-launcher (A shell script).

```
 #!/bin/bash
# For use with .desktop files and MIME handlers so that the Ubuntu Policy
# can be followed: programs cannot be executed when they lack the execute bit.
# https://wiki.ubuntu.com/SecurityTeam/Policies#Execute-Permission%20Bit%20Required
exe="$1"
shift || true
if [ -n "$exe" ] && [ ! -x "$exe" ] && \
   [ "${exe:0:5}" != "/usr/" ] && [ "${exe:0:5}" != "/opt/" ]
then
    if [ -n "$DISPLAY" ] && [ -x /usr/bin/zenity ]; then
	if /usr/bin/zenity --question --title "Blocked: $*" --text "The file '$exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the <a href=\"https://wiki.ubuntu.com/Security/ExecutableBit\">executable bit</a>. HOWEVER, you can choose to override the security protections and open this potentially unsafe file. Execute manual override?"; then
		exec "$@" "$exe"
	fi
	
    else
        echo "$*: '$exe' is not executable.  Aborting." >&2
    fi
    exit 1
fi
exec "$@" "$exe" 
```

Where should I go to put my changes up for approval??

---

### Post by yanom on 2011-10-17
no one? I have a nice improvement here!

---

### Post by Atamisk on 2011-10-18
*snip* - 404

Anyway, as it turns out, that file is part of the mime-support package. its launchpad page is [here.]("https://launchpad.net/ubuntu/+source/mime-support") As far as who exactly to contact, it may be better to 'ask a question' on the launchpad page. 

HTH, 
-Aaron

---

### Post by sffvba[e0rt on 2011-10-18
I did some cleanup in this thread.

Please keep the CoC in mind when posting, be helpful and courteous or rather refrain from posting.  If someone isn't keeping within the CoC then report the post.



Regards
404

---

### Post by mc4man on 2011-10-18
Your best bet would be to file a bug against the mime-support package and or see if you could get dialogue with the security team, ck here
[https://wiki.ubuntu.com/SecurityTeam/Contacts](https://wiki.ubuntu.com/SecurityTeam/Contacts)
I believe something quite similar to what you have has been proposed before & rejected. (& likely will continue to be.

The policy requires that "not give the option of launching it anyway" - if that's not changed then something like your script has no chance

 I had a bug once against this, the explantion of why the option would not be allowed is basically this

> We are trying to protect the Ubuntu desktop from malware. One of the popular malware attack vectors is a "Drive by download": to have a user unknowingly download an executable file and hope they double click on it later at which point the malware is executed.

Since Ubuntu software is normally installed through signed repositories using the Ubuntu Software Centre, there is no reason to encourage the Windows-type behaviour of downloading a random piece of unsigned software from the Internet and executing it. Thus, random downloaded files are not executable by default, and executing them should be reserved for advanced users who know the implications of doing so.

Whether or not this policy offers any great protection in 'real world usage' is not that relevant

As far as .exe's & wine - users now have the choice of using a version that includes the cautious-launcher (1.2) or one that doesn't(1.3), plus the 'official' ppa never uses the launcher.

---

