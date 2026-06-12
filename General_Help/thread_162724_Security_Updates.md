---
title: "Security Updates"
date: 2006-04-19
forum: General Help
---

### Post by SimoneDice on 2006-04-19
I was wondering - I have Ubuntu Breezy and it is currently using the Firefox 1.0.7 version of the browser.  With Firefox recently releasing Firefox 1.5.2 to address security vulnerabilities, does Breezy 1.0.7 for Breezy get updated to fix the security vulnerabilities too?  Or, does it just use the old browser with all the vulnerabilities?  I don't believe there are just security patches for Firefox and I wonder how Ubuntu handles this since they don't update the browser to the most recent versions.  Anyone know the policy around this?

---

### Post by jazzmuzik on 2006-04-19
I don't have an answer for you but I was wondering myself why the browser isn't updated quicker. Here's how I understand firefox upgrade history:

[FONT="Courier New"]1.0.7 - 09/30/2005
1.0.8 - 04/13/2006
1.5 - 12/08/2005
1.5.0.1 - 02/17/2006
1.5.0.2 - 04/13/2006[/FONT]

I'm not criticizing, just wondering what the reason is.

---

### Post by OffHand on 2006-04-19
[QUOTE=jazzmuzik]I don't have an answer for you but I don't understand why the browser isn't updated quicker. Here's how I understand firefox upgrade history:

[FONT="Courier New"]1.0.7 - 09/30/2005
1.0.8 - 04/13/2006
1.5 - 12/08/2005
1.5.0.1 - 02/17/2006
1.5.0.2 - 04/13/2006[/FONT]

I'm not criticizing, just wondering what the reason is.[/QUOTE]
Ubuntu uses his own Firefox. It's not the same as the one from mozilla.

---

### Post by SimoneDice on 2006-04-19
Where is it documented that Ubuntu uses their own version of Firefox and how customized is it?  I understand that there might be some customization, but the meat of the browswer, I'm pretty positive, is standard Mozilla/Firefox, which would mean that the main security vulnerabilities would still be the same and would affect the browswer just the same.

---

### Post by aysiu on 2006-04-19
Even though the general policy of Ubuntu is to backport security updates, the update from 1.0.7 to 1.5 was particularly difficult and threatened the whole stability of Ubuntu's Breezy release.

Read more of the official explanation [here](http://www.ubuntuforums.org/showpost.php?p=529570&postcount=1).

Firefox 1.5 will be available in Dapper Drake (to be released in June). In the meantime, this script will update you to 1.5 in Breezy rather painlessly:

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

I know that seems to make no sense (1.5 threatens stability, update painlessly here), but the script doesn't really update 1.0.7; it just installs 1.5 separately and changes your launcher links.

---

### Post by bollix47 on 2006-04-19
You can get firefox 1.5.0.1 by installing Automatix:
[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

You can then use the Firefox update mechanism to get 1.5.0.2.  There's a thread on here somewhere that explains you might have to use 'sudo' or be root to do the update which is what I had to do and it worked fine.

[http://www.ubuntuforums.org/showthread.php?t=162257&highlight=firefox+update](http://www.ubuntuforums.org/showthread.php?t=162257&highlight=firefox+update)

---

### Post by jazzmuzik on 2006-04-19
[QUOTE=aysiu]Even though the general policy of Ubuntu is to backport security updates, the update from 1.0.7 to 1.5 was particularly difficult and threatened the whole stability of Ubuntu's Breezy release.[/QUOTE]

An app upgrade makes the OS unstable? I don't understand that.

---

### Post by aysiu on 2006-04-19
[QUOTE=jazzmuzik]An app upgrade makes the OS unstable? I don't understand that.[/QUOTE] I'll repeat:

Read more of the official explanation [here](http://www.ubuntuforums.org/showpost.php?p=529570&postcount=1).

---

