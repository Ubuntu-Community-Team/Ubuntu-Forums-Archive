---
title: "Unable to see Launcher or Taskbar in Ubuntu...?"
date: 2012-07-15
forum: General Help
---

### Post by listentounderthegiven on 2012-07-15
I cant see the launcher or taskbar at the top of my screen, Ubuntu let me know I should update my display driver and when it finished it told me to restart for the changes to take effect.  After reboot, Im unable to see any Icons or taskbar now... any suggestions...? Thanks in advance. P.S. Im also unable to use terminal for some reason..?

---

### Post by Shadius on 2012-07-15
Could you post a screenshot? It could be a graphics card driver issue. What is your graphics card? What happens when you try to open Terminal?

---

### Post by listentounderthegiven on 2012-07-15
onboard NVIDIA GeForce 6150SE nForce 430

Ive posted screenshots before but i cant for some reason as well. I can only see the desktop background, no launcher or taskbar. I had the launcher to always be shown as well.

---

### Post by Shadius on 2012-07-15
> **listentounderthegiven said:**
> onboard NVIDIA GeForce 6150SE nForce 430

Ive posted screenshots before but i cant for some reason as well. I can only see the desktop background, no launcher or taskbar. I had the launcher to always be shown as well.

Can you access the Terminal using the keyboard shortcut ***Ctrl+Alt+T***?

---

### Post by listentounderthegiven on 2012-07-15
No, i tried to, but it wont respond to it.

---

### Post by Shadius on 2012-07-15
It could be a resolution issue as well. Are you able to access the Dash by pressing the Windows key, also known as the Super key (has Windows logo on it)?

---

### Post by listentounderthegiven on 2012-07-15
no I wasnt allowed to but, i had started creating a webpage and saved the file to my desktop so I am able to get my browser up and navigate around, somehow the All Settings window came up and I installed another display driver that was also in the initial list and I restarted afterwards and everything is displaying fine now. I want to thank you anyway for the prompt response to this thread, shall I note this thread as solved...? Thanks again!

---

### Post by Shadius on 2012-07-15
> **listentounderthegiven said:**
> no I wasnt allowed to but, i had started creating a webpage and saved the file to my desktop so I am able to get my browser up and navigate around, somehow the All Settings window came up and I installed another display driver that was also in the initial list and I restarted afterwards and everything is displaying fine now. I want to thank you anyway for the prompt response to this thread, shall I note this thread as solved...? Thanks again!

Great! Well, it seems like it updated to the correct graphics card driver and sorted itself out. If everything is working normally, you can mark this as solved. Happy to help. :)

---

### Post by listentounderthegiven on 2012-07-15
actually I apologize am I able to undo the display driver updates so it will completely go back to the way it was?

---

### Post by Shadius on 2012-07-15
> **listentounderthegiven said:**
> actually I apologize am I able to undo the display driver updates so it will completely go back to the way it was?

You can check in Additional Drivers from the System Settings window to see what is available. It should offer some propietary drivers. As for undoing the updates, I don't know how to do that and it would probably revert your system to it's problematic state.

---

### Post by listentounderthegiven on 2012-07-15
ahh ha. I see well thank you.

---

### Post by bogan on 2012-07-15
Hi!, **listentounderthegiven**,

If you loaded the updates driver from Additional Drivers, go there again and the entry should have a 'Deactivate' button, Click on it and go to Synaptic Package Manager.

If you do not have it, from a terminal: ```
sudo apt-get install synaptic
```.

From Dash enter 'syn' and select the SPM Icon; enter 'nvidia' in the Quick Filter box, [ If it says: "Rebuilding Search Index", wait for it to complete,] and select { Right-Click} the appropriate nvidia* entry that is shown Green, ie=installed, and mark it for Un-installation ie, "Mark For Removal" in the drop-down Menu.

[ Note: the entry will [AFAIK] either be 'nvidia-current295.40', 'nvidia-current-dev295.40', 'nvidia-current-updates295.49',  or 'nvidia-current-updates-dev295.49': could be something else if you have added ppa's, but do not remove 'nvidia-common', or 'nvidia-settings'.]

Select the 'Apply' Icon, confirm your selection and reboot.

Chao!, **bogan.**

---

