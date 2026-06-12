---
title: "sound not working on ubuntu 9.10"
date: 2010-03-13
forum: General Help
---

### Post by ikgardner on 2010-03-13
hey, i cant get my sound option to work in preferences. it just puts a dialog box up saying waiting for sound to respond. also, if i right click my sound icon on the top panel i cant access volume control. these issues seem to have occurred after i upgraded to 9.10. any suggestions?

---

### Post by ikgardner on 2010-03-13
ok, so in addition to not being able to access my sound preferences or volume control. i have sound coming out of the computer but i have no control over it (volume adjustment, etc). so those are problems 1 and 2. thirdly, when i try to use skype or even try the recording option my input is clearly not working. something wrong with the microphone i suppose. please help!

---

### Post by Villiam on 2010-03-13
Starting with identification of your sound card and hardware there are many reasons that your sound problems are happening. You may like to see this: [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by lidex on 2010-03-14
Go to "Software Sources" in your menu. "Applications>System>Administration>Software Sources"
On the updates tab, check-select the third option: "Unsupported Updates" (Backports). Close that out. Now in a terminal enter these commands:
```
sudo apt-get update
sudo apt-get upgrade 
sudo apt-get install linux-backports-modules-alsa-karmic-generic
sudo update-grub
```

One line at a time; enter your user password when prompted. "Applications>Accessories>Terminal"
[SIZE="4"]**Now Reboot!**[/SIZE]

---

