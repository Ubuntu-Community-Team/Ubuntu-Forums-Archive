---
title: "Power cord makes screen flicker"
date: 2010-05-25
forum: General Help
---

### Post by donder on 2010-05-25
Hi,
I'm pretty new to Ubuntu. I have LucidLynx installed on my eeepc 1005PE. I am currently using it under the gnome interface but i also have the notebook version of it installed (probably because i got a notebook remix of it, not quite sure). All is well except for the following: after i power up my notebook, login and i can see the panel i plug the power cord in. And the my screen starts flickering in orangeblack colors. Nothing i do seems to take it out of this state but a good old hard-reboot. Any ideeas on what the problems might be?
PS if you ask me for system specs or stuff like that please post the command to get those along with it.

Thanks.

---

### Post by badger_fruit on 2010-05-25
**If you boot another OS (eg a Live CD), does the problem persist?**
If it does, hardware error = return to shop or PC repair place.
If not then perhaps a re-install of the OS might fix it. Yes, a bit extreme but that's all I can think of right now ;)

---

### Post by donder on 2010-05-25
don't have a live cd with me atm. I'll check that on thursday. Then maybe a reinstall if all fails, thanks.
Any other ideas?

---

### Post by donder on 2010-05-25
Ok, i think i found what the problem is. I am using eeepc-tray. When i take the power cord out it switches automatically to power saver mode. Then when i plug the cord back in the screen starts flickering. But if i set the power mode back to super high performance while on battery and then plug the cable back in, there is no screen problem. My question now is either how to enforce permanent super high performance even when on battery, or should i just remove it and find something else to manage my power?

---

### Post by donder on 2010-05-26
bump

---

### Post by donder on 2010-05-26
I just managed to find a workaround. 

If you are in Power saver on battery and you plug in the power cord and you are still in power saver mode then no screen flickering occurs.

To force the eeepc to stay in power saver when changing from battery to AC you need to edit the /etc/default/eeepc-acpi file. Open it with a texteditor.
Then search in the file for *MODE_AC* and set it to:
MODE_AC="powersave"

It should actually have the same value as the MODE_BAT underneath it.

Save the file and exit.

The annoying part about this workaround is that you have to manually set the power mode every time you connecting the power cord to the laptop.


PS. I have tried a Live CD, but that doesnt have eeepc-tray. I think there is something wrong with the application and not my notebook.

---

