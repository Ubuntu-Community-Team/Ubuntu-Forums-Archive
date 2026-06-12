---
title: "Unable to reboot/shutdown"
date: 2010-03-09
forum: General Help
---

### Post by gigaSproule on 2010-03-09
I have recently upgraded to the 10.04 Alpha and have been unable to reboot or shutdown. I know it's just an alpha and therefore problems are bound to exist, so I tried reinstalling from a live cd of Alpha 3. But I am still unable to reboot or shutdown.

To clarify what happens, I click on shutdown or reboot, the pop-up appears, I click on the shutdown/reboot button and it seems to complete it. It says that processes have been killed and something has exited with 255. But my computer is still on. I am guessing that Ubuntu is shutting down, it's just not actually shutting my computer down or restarting it.

---

### Post by patchwork on 2010-03-09
What happens when you reboot or shutdown from the command line?
```
sudo shutdown -r now #reboot
sudo shutdown -h now #shutdown
```

---

### Post by gigaSproule on 2010-03-21
I got the same issue no matter what I did. It would all shutdown fine and then just hang on a black screen. The computer would stay on. I just reinstalled Ubuntu 9.10. But thanks for the help anyway.

---

### Post by gigaSproule on 2010-03-22
I have reinstalled the beta and I'm still getting the same issues. When I do the sudo shutdown -h now command, it goes to the shutdown splash and then prints some code out and the last thing to show is init: Disconnected from system bus, at which point it hangs. With the sudo shutdown -r now command, it goes to the shutdown splash and then prints out some other code with the last bit being something about daemon and terminating with (255).

---

### Post by patchwork on 2010-03-22
How about ```
sudo shutdown -P now
```
This explicitly requests the computer to power down after the system processes are terminated.

---

### Post by gigaSproule on 2010-03-22
Same sort of thing. My computer's 'busy' light flashes still, but very slowly which leads to me thinking that there is still some process going on, but for some reason never finishes. I have left my computer to shutdown for half an hour earlier and it still didn't work.

EDIT: I have just tried to reboot from the live CD and it failed.

---

