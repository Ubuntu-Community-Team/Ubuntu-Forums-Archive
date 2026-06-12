---
title: "Gnome Shell &quot;Network Disconnected&quot; notification"
date: 2012-02-12
forum: General Help
---

### Post by forrestcupp on 2012-02-12
There seems to be some kind of bug with Gnome Shell where whenever your laptop is suspended from shutting the lid, when you bring it back up, there is a notification that says "Network Disconnected. You are now offline". It stays there until you click on it, even when you are back online.

I've googled around for this and didn't really find a solution. Has anyone figured out any workarounds for this? It's kind of annoying.

---

### Post by dcstar on 2012-02-13
> **forrestcupp said:**
> There seems to be some kind of bug with Gnome Shell where whenever your laptop is suspended from shutting the lid, when you bring it back up, there is a notification that says "Network Disconnected. You are now offline". It stays there until you click on it, even when you are back online.

I've googled around for this and didn't really find a solution. Has anyone figured out any workarounds for this? It's kind of annoying.

How about actually reporting it as a bug so it might actually get fixed?

---

### Post by forrestcupp on 2012-02-13
> **dcstar said:**
> How about actually reporting it as a bug so it might actually get fixed?

Thanks for the help.

There is already a bug reported. All they've done so far is to argue about whose fault it is. I was just hoping that maybe someone has found a workaround until the bug is actually fixed.

---

### Post by forrestcupp on 2012-02-14
I just installed Precise, and it seems like they have this working a little better. It still gives the "Network Disconnected" notification, but it does disappear after the timeout now.

---

### Post by Frogs Hair on 2012-02-14
My desktop disconnects during sleep but reconnects when it wakes up . I thought this was intended . I see a connection pop up message when the computer wakes . I am not using wireless though .

---

### Post by kurt18947 on 2012-02-14
> **forrestcupp said:**
> I just installed Precise, and it seems like they have this working a little better. It still gives the "Network Disconnected" notification, but it does disappear after the timeout now.

Not here, the message is persistent.  The wireless connection is reestablished by the time I enter a password but the message persists well past 3 seconds or whatever time it's supposed to disappear.  Not a problem, just an irritant.

---

### Post by forrestcupp on 2012-02-14
> **kurt18947 said:**
> Not here, the message is persistent.  The wireless connection is reestablished by the time I enter a password but the message persists well past 3 seconds or whatever time it's supposed to disappear.  Not a problem, just an irritant.

That's weird. It doesn't disappear on mine anymore, either. I clicked on the button that says something like "Don't show this message again", and after I did that, it stopped timing out.

Edit: I'm pretty sure that if you don't turn off notifications in your profile menu, the notification will disappear like it's supposed to.

And just so dcstar will know, I did update the bug that was already filed with my experiences.  :P

---

### Post by kurt18947 on 2012-02-16
Here's a bit of an update on my machine.  I was logged onto the guest account with gnome.  Put it in suspend.  Resumed a few hours later and notification disappeared as advertised.  Switched to my sudo account, changed to gnome, suspended, resumed, notification didn't even appear.  Created a new desktop user account, switched it to gnome, suspended and resumed, notification worked as expected.  There's some setting on my primary user account in PP that is a little off.  I'm not going to worry about it; I'll most likely delete this install and start fresh close to the release date.  It does seem that this bug is likely squashed.

---

### Post by forrestcupp on 2012-02-17
> **kurt18947 said:**
> Here's a bit of an update on my machine.  I was logged onto the guest account with gnome.  Put it in suspend.  Resumed a few hours later and notification disappeared as advertised.  Switched to my sudo account, changed to gnome, suspended, resumed, notification didn't even appear.  Created a new desktop user account, switched it to gnome, suspended and resumed, notification worked as expected.  There's some setting on my primary user account in PP that is a little off.  I'm not going to worry about it; I'll most likely delete this install and start fresh close to the release date.  It does seem that this bug is likely squashed.

Even in Precise, I ended up having the problem after I turned off notifications. After I did a clean reinstall of 11.10, I never turned off notifications, and it never caused any problems. I think it has something to do with that.

---

