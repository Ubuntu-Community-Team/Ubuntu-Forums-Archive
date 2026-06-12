---
title: "Power Management: Shutdown when the suspend button is pressed?"
date: 2010-06-25
forum: General Help
---

### Post by athoma13 on 2010-06-25
Hi,

I have a dell zino inspiron media pc with Ubuntu 10.04 installed. I am able to shutdown using the power button on machine i.e. System->Preferences->Power Management
option 'when power button is pressed': choose 'Shutdown'

But

for option 'when suspend button is pressed', I only get 'Suspend' or 'Hibernate' in the drop-down. Where is my 'Shutdown' option?

I really want to be able to shutdown my machine from my wireless keyboard!

/etc/acpi/events/sleepbtn is not invoked when I press sleep on the keyboard... (why is the script even there?!?).

Any ideas on how to get this going?

---

### Post by athoma13 on 2010-06-26
Replying to my own message...

call **gconf-editor** from a terminal window

Navigate to /apps/gnome-power-manager/buttons

In the properties, find 'suspend', and change the value to 'shutdown'.

Et Voila, now pressing sleep from your keyboard will shutdown your machine...

PS:
As to why the option is not there in Power Management, I have no idea. Note that going back to Power Management now shows blank for the 'when suspend button is pressed' option.

---

