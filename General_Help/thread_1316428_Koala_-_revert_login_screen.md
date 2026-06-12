---
title: "Koala - revert login screen"
date: 2009-11-05
forum: General Help
---

### Post by MrGrey1 on 2009-11-05
I just upgraded to Koala and am very unhappy about the new login screen situation. I have googled around a bit but have been unable to find the information I require. I fail to see how saving a few seconds on boot time is worth removing features that I would consider essential. Am I the only one?  Ubuntu seems to be more concerned with its e-peen status boot time then it is concerned about its users ability to customize their own systems. This is the behavior or mindset typically displayed by M$ and from where I'm sitting completely contradicts the whole ethos behind Ubuntu. Seriously WTF moment of the month?! /rant

I do not want my usernames displayed full stop!
Is there any way at all to set the login screen to a prompt so both username and password have to be entered?
(edit via gconf-editor through /apps/gdm/simple-greeter/disable_user_list true  does not work.)

If this is not possible is there anyway to remove the new login screen and revert or reinstall the previous login setup with all the customization settings restored?

---

### Post by pastalavista on 2009-11-06
This command in terminal will fix it```
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type bool --set /apps/gdm/simple-greeter/disable_user_list true
```

edit: well... it fixed it for me

---

### Post by MrGrey1 on 2009-11-06
> **pastalavista said:**
> This command in terminal will fix it```
sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type bool --set /apps/gdm/simple-greeter/disable_user_list true
```

edit: well... it fixed it for me

Thankyou, that worked for me. If anyone knows a way to revert to the old configuration options I'd still like to know. 

Why couldn't there be a simple tick box in the login screen gui? User friendly?..

---

