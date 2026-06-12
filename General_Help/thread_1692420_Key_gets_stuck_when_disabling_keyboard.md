---
title: "Key gets stuck when disabling keyboard"
date: 2011-02-21
forum: General Help
---

### Post by dualityim on 2011-02-21
I'm running into some weird behavior while using xinput to disable the keyboard that might be an underlying bug, and I'm wondering if anyone could reproduce it or provide any insight into what's causing it. I'm running Ubuntu desktop 10.10 64-bit in a VMware Workstation VM running on a Windows 7 64-bit host.

First I use "xinput list" to find out which keyboards are present in the system. In my case there's only one with id=9. Next I execute "xinput set-prop 9 "Device Enabled" 0" to disable the keyboard at id=9. Now, if I type this into the terminal and hit enter, the keyboard gets disabled but at the same time the enter key becomes stuck. The system thinks the enter key is being held down. However, if I make a script with the same command and execute it by clicking it in Nautilus, the keyboard gets disabled and no keys are stuck. It seems if the keyboard is disabled with a press of the keyboard, then whatever key was pressed to trigger the disabling of the keyboard becomes stuck.

You might ask why I would want to disable the keyboard in the first place. It's because I'm running Ubuntu in VMware Unity mode, where the system in the VM is integrated with the host desktop system, the VM's windows appear as individual windows on the host desktop, etc. In this mode, whenever I close a VM window by hitting a key on the keyboard (for example, hitting Ctrl+D while in gnome-terminal) and focus goes back to a host window, then that key becomes stuck the next time I open a VM window. If I close a VM window by clicking the mouse then there's no problem. I'm pretty sure now that this is caused by the above mentioned bug from disabling the keyboard. I think in Unity mode VMware workstation runs a script to disable the keyboard in the guest whenever VM windows lose focus, so key presses don't continue to be piped to the guest OS. However, if this action is triggered by a press of the keyboard, then that key becomes stuck in the guest OS.

I'd be grateful if anyone could see if they can reproduce this bug, perhaps I can file a bug report.

---

### Post by dualityim on 2011-02-23
I just tried this on a native installation of Ubuntu 10.10 32-bit on one of my old computers and the same behavior occurs, so it's not due to running the system in a VM. I'm thinking of filing a bug report but I've never done it before, and I don't even know where to file it since I have no idea how far upstream this goes. What should I do?

---

### Post by stinkeye on 2011-02-23
I have this problem with a couple of commands using xdotool.
Adding a sleep command so it doesn't catch the pressed key usually solves it.

eg
```
sleep 1 && xinput --set-prop 8 --type=int "Device Enabled" 0
```

---

### Post by dualityim on 2011-02-23
> **stinkeye said:**
> I have this problem with a couple of commands using xdotool.
Adding a sleep command so it doesn't catch the pressed key usually solves it.

eg
```
sleep 1 && xinput --set-prop 8 --type=int "Device Enabled" 0
```

Interesting...

Unfortunately I have no idea how VMware-tools triggers this mechanism, so I don't know where I could insert the sleep to prevent this from happening. I'll dig around VMware-tools some more.

---

