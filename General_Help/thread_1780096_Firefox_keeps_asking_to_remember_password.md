---
title: "Firefox keeps asking to remember password"
date: 2011-06-11
forum: General Help
---

### Post by nomko on 2011-06-11
HI,

I've got a strange issue here concerning Firefox. Of some sites i don't ant my login and password to be saved by Firefox. The question pops up (below navigation bar) i click no and it's gone. But when i go to the same website, let's say, the next day, i get the same question. This issue is not related to 1 website, it's doing with all kinds of sites i log in to.

How can i prevent that FF comes up with that question to remember my login/password even when i clicked on No, do not remember? Pleae keep in mind that some site i do let FF save my login/password, those sites are regular visited by me. So unchecking the option in preferences i rather don't want that.

Who can tell me why FF keeps coming up with that question even if i click on no?
Many thanks!

---

### Post by tredegar on 2011-06-11
FF 3.6:
Firefox - Edit - Preferences - Security - Remember Passwords - **Exceptions**
Enter a list of the sites you do *not* want passwords saved for.

---

### Post by nomko on 2011-06-13
> **tredegar said:**
> FF 3.6:
Firefox - Edit - Preferences - Security - Remember Passwords - **Exceptions**
Enter a list of the sites you do *not* want passwords saved for.

The websites i don't want' to remember the login/password are in that list. But still FF keeps asking me if FF has to remember the login/password. Very strange. Looking for an answer.

---

### Post by nomko on 2011-06-15
Is there some file in the hidden mozilla directory which can be modified?
Cause i've had 2 sites now of which i don't want them to remember the login/password but still FF keeps coming up with that question and this: *Firefox - Edit - Preferences - Security - Remember Passwords - Exceptions* doesn't show the 2 sites after clicking on No.

---

### Post by gmargo on 2011-06-15
> clicking on No.

When the password-remember pop-up occurs, click on "Never for this site" instead of "No".

---

### Post by nomko on 2011-06-16
> **gmargo said:**
> When the password-remember pop-up occurs, click on "Never for this site" instead of "No".
 
That's what i do all the time. I mixed those 2 buttons up but i mean the "*Never for this site*" button. But the problem is that FF doesn't put the website in *Firefox - Edit - Preferences - Security - Remember Passwords - Exceptions *permanent. It put's it in there, but when i close FF and restart it, the entries are all gone. 
 
So, does someone know if FF is using some kind of (hidden) file where FF keeps track of those things which i might modifiy.

---

### Post by gmargo on 2011-06-16
Are you using any settings or add-ons that clear the history/cookies/etc upon exit?

For testing: Have you tried creating a new profile?   Or even easier, just temporarily rename your $HOME/.mozilla/ directory and let firefox create a new one.

---

