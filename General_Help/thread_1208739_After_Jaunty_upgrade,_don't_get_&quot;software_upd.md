---
title: "After Jaunty upgrade, don't get &quot;software updates are available&quot; reminders"
date: 2009-07-09
forum: General Help
---

### Post by kkruecke on 2009-07-09
I upgrade to Jaunty from Intrepid. And it seems that every since, I no loner get the "Software Updates are Available" icon (not sure of the exact wording) that used to show up in the upper right-hand corner. Instead I've had to rely on using aptitude by hand:

# sudo aptitude update
# sudo aptitude full-upgrade

Is there anyway to fix this? 

thanks,
Kurt

---

### Post by 5nak3 on 2009-07-09
no no they are still there, i think they changed the timing when the update checks for new updates to a week instead of immediately. To overcome this you have to do this:

Alt + f2

then type and run gconf-editor

then from the list choose apps and find update manager or update notifier.

There will be a value in one of those that is listed as 7 I believe. To get the updates when they are available you have to change the 7 to a 0.

I'm sorry about the vagueness of the last bit of this reply, I'm on my Hardy box at the moment so I don't know what the actual terms used are.

If no one else replies, later tonight when I'm on jaunty I'll post exactly where to make the changes.

But you should be able to work it out by getting into the 

gconf-editor -> apps -> update notifier and changing the value as I said.

Hope that helps

---

### Post by kkruecke on 2009-07-09
Thanks!

Yes, it is under update-notifier, under apps, which has the regular_auto_launch_interval set to 7. I assume that means 7 days. So I'm going to change it to 1.

---

### Post by 5nak3 on 2009-07-09
Glad you managed to work it out.

Once again, sorry for the vagueness of the reply, but I'm glad you could work it out.

If you don't mind, could you please mark the topic as solved so as other users can know you've worked out your problem.

---

