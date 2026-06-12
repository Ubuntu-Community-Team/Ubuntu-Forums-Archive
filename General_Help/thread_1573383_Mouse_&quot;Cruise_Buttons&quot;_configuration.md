---
title: "Mouse &quot;Cruise Buttons&quot; configuration"
date: 2010-09-12
forum: General Help
---

### Post by AnotherMuggle on 2010-09-12
I have been using Ubuntu 10.04 in VirtualBox for a few weeks and the cruise up and down buttons (above and below the scroll wheel) worked as Home and End keys, this is how I like them.

I've just done a full install of Ubuntu and these buttons have the same action as the scroll wheel instead of working like Home and End.

Does anyone have any suggestions on what I can check in the VM to try and mirror what its doing with the buttons?

I am currently using HIDPoint drivers which are good, but they don't allow configuration of these particular buttons.

Cheers,
Tom

---

### Post by AnotherMuggle on 2010-09-12
Wahey, fixed it :-D

I just discovered btnx and mapped the cruise buttons to HOME and END keys...working perfect.

EDIT:

I may have spoken too soon.  It seems btnx adds the functionality to the buttons, but it doesn't ALWAYS work.  It seems like the buttons are now trying to cruise and emulate the HOME and END buttons both at the same time.  In some cases, particularly bad viewing eBay in Firefox, the content kind of bounces up and down instead of shooting to the top or bottom of the page.

---

