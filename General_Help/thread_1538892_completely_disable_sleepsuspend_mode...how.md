---
title: "completely disable sleep/suspend mode...how?"
date: 2010-07-25
forum: General Help
---

### Post by jjloupe on 2010-07-25
My crappy PC is having problems recovering from suspend mode. I have tried everything to stop it from entering the suspended state to no avail. Every 10 minutes of inactivity it goes down, and will not start up again. YES, I checked the power settings.

So...how can I disable this completely, I have no use for a sleep/suspend mode.

---

### Post by jjloupe on 2010-07-27
Ok, I am shocked none of you smart people here knows the answer to this.

---

### Post by P4man on 2010-07-27
There is no reason to be shocked or get hostile like that. There is a gazillion people asking questions here and only a handful (relatively) trying to help. They are all unpaid volunteers. Not every question can be read or answered. If you want to be assured of getting a response; buy a support contract at canonical for $55 for a year:
[http://shop.canonical.com/product_info.php?currency=USD&products_id=528](http://shop.canonical.com/product_info.php?currency=USD&products_id=528)

To answer the question it would help if you explained in a bit more detail how you configured power management options as "i checked" doesnt exactly prove you set them correctly.

If you did set them correctly; open gconf-editor and browse to 
/apps/gnome-power-manager/timeout/sleep_computer_ac

---

### Post by jjloupe on 2010-07-27
there was nothing hostile about my post smart ***. It was just better than reply "bump".

Exactly who pissed in your cheerios this morning?

---

### Post by PocketHercules on 2010-08-03
I am looking to do the same?  Has anyone figured out how to disable sleep/suspend/hibernate?

---

### Post by jmfal on 2010-08-03
system> preferences> screensaver> power management> on ac power> set both options to never> make default> close...done

---

### Post by manish.shah on 2011-01-25
I'm running Ububtu 10.10 on a Lenovo x201s laptop and none of the above suggestions work to prevent hibernation.

Incidentally, hibernation works just fine on the laptop. I just don't want it. It kicks in after 30 mins of inactivity whilst on Mains Power.

In Power Manager, I have "Put Computer To Sleep" = Never and "Put Display To Sleep" = Never when on Mains Power.

In GConf /apps/gnome-power-manager/timeout/ I have sleep_computer_ac = 0 and sleep_display_ac = 0.

Regardless, nothing can prevent the laptop from hibernating after 30 mins. 

Any more suggestions?

Thanks,
Manish

---

### Post by Verbeck on 2011-01-25
> **manish.shah said:**
> I'm running Ububtu 10.10 on a Lenovo x201s  laptop and none of the above suggestions work to prevent hibernation.

Incidentally, hibernation works just fine on the laptop. I just don't  want it. It kicks in after 30 mins of inactivity whilst on Mains Power.

In Power Manager, I have "Put Computer To Sleep" = Never and "Put Display To Sleep" = Never when on Mains Power.

In GConf /apps/gnome-power-manager/timeout/ I have sleep_computer_ac = 0 and sleep_display_ac = 0.

Regardless, nothing can prevent the laptop from hibernating after 30 mins. 

Any more suggestions?

Thanks,
Manish
check the screen saver settings in system>preferences>screensaver preferences

---

### Post by manish.shah on 2011-01-25
> **Verbeck said:**
> check the screen saver settings in system>preferences>screensaver preferences
Oops, sorry should have mentioned those:

Regard the computer as Idle after 5 mins
Activate screensaver when computer is idle

This seems fine. I want the screensaver and it works ok. Just don't want the hibernate. Problem seems unrelated to screensaver (i.e. it happens whether screensaver is enabled or not).

---

### Post by yumgnomeandthensome on 2011-01-26
Perhaps you could script a shutdown command to run each time you boot to say
shutdown -h xxx minutes

make it say 24 hours and that way you'll probably power it off manually before it ever turns off.

---

### Post by manish.shah on 2011-01-26
Interesting idea, thanks. I rarely shutting down my laptop though - I usually standby at the end of the day and resume in the morning.

I think this is a general problem with Power Management Preferences not being read. For example, I have "Ask Me" as the setting for when the power button is pressed. However when I press the power button nothing happens.

---

### Post by rocthrttle on 2011-01-26
> **jjloupe said:**
> My crappy PC is having problems recovering from suspend mode. I have tried everything to stop it from entering the suspended state to no avail. Every 10 minutes of inactivity it goes down, and will not start up again. YES, I checked the power settings.

So...how can I disable this completely, I have no use for a sleep/suspend mode.

you can put a tool in your top bar called "inhibit applet". right click "add to panel" search for inhibit applet. add to top bar. with one click to your top bar you can tell your machine to stay on no matter what. 

i would check the BIOS. it sounds like there might be something outside of ubuntu causing it. if the settings are set properly i do not see any other possibility. make sure your settings are set for plugged in and unplugged properly. it could be hardware related. how old is your battery? if the battery is old and your wall connection is loose and not making connection at all times, then the machine is just shutting down due to low voltage alarm telling it too. which there is no stopping.

thanks for trying ubuntu. i hope your experience gets better and better.

---

