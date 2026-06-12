---
title: "Firefox &quot;untrusted connection&quot; has no &quot;continue anyway&quot; option"
date: 2012-04-02
forum: General Help
---

### Post by Dingbats on 2012-04-02
Since yesterday, when I try to access a certain site in Firefox, I get this:

[IMG]http://i.imgur.com/xtEUp.png[/IMG]

It's in Swedish, but the point is that there is no "I understand the risks" part that I've always had before when this happened.  So there's just no way for me to visit the site.  This certificate problem is well known on this site, so I know it's not dangerous.

What do I do?

---

### Post by zombifier25 on 2012-04-02
Hmm, try visiting about:certerror and see if the problem persists.
What Firefox are you using?

---

### Post by winh8r on 2012-04-02
If you got to Firefox Edit > Preferences > Advanced > Encryption you should be able to add an exception to the way it handles the request.

In your case , you seem to be fairly certain that the site is trusted , but for anyone else reading this you should always excercise caution before allowing potentially harmful sites to be accessed by your browser.

The choice is yours.

Hope this helps.

---

### Post by Dingbats on 2012-04-02
> **zombifier25 said:**
> Hmm, try visiting about:certerror and see if the problem persists.
What Firefox are you using?
Sorry, of course I should have specified the version.  It's 11.0.  On the about:certerror page, I see the "I understand the risks" option.

> **winh8r said:**
> If you got to Firefox Edit > Preferences > Advanced > Encryption you should be able to add an exception to the way it handles the request.
Maybe, but I don't understand how...

It seems this specific problem is sorting itself out with this site now, but in case this happens again I'd like to figure out a workaround.

---

