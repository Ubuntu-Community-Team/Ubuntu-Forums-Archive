---
title: "How to give automatic authorization to certain applications?"
date: 2009-12-05
forum: General Help
---

### Post by tokyo-joe on 2009-12-05
I'm using a twitter client called TweetDeck. It is an Adobe Air application and prompts me to input system password every time I start the application.

Also, the indicator-applet requires password input every time I start the system.

How can I give an automatic authorization to certain applications?

I am using Karmic Koala 9.10.

---

### Post by Joshua Lückers on 2009-12-05
I had similar problems when using auto login. Disabling this fixed those issues. :)

---

### Post by tokyo-joe on 2009-12-05
> **Joshua Lückers said:**
> I had similar problems when using auto login. Disabling this fixed those issues. :)

I don't want to disable automatic login.
Is there any solution?

---

### Post by Joshua Lückers on 2009-12-05
Thus far I have not found a solution for it. Maybe others do know a good solution.

---

### Post by 3rdalbum on 2009-12-05
Set the keyring password to blank (nothing), then it won't ask you for your password to unlock the Gnome keyring.

I'd be worried about the Adobe Air program - is this asking you to unlock your keyring, to authorise an action or to run a program as administrator? If it's the latter I'd be very worried.

---

