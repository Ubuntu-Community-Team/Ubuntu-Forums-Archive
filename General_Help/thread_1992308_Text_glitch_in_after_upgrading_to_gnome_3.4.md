---
title: "Text glitch in after upgrading to gnome 3.4"
date: 2012-05-31
forum: General Help
---

### Post by balasankarc on 2012-05-31
Hi all
Recently i upgraded to GNOME 3.4 and i am suffering from text glitches... These occur mainly in programs like chromium but also in ubuntu software centre and other inbuilt programs.
I've attached a screenshot of the same.. The area marked in red shows the glitch... acually the page name was 'facebook' but the text is glitched...

[U]**In chromium, the glitch appears during page loading or when i move my cursor over the tabs (not clicking, just moving over them)**
[/U]
Pls tell me how to correct this issue...

Balasankar C

---

### Post by imachavel on 2012-05-31
try restarting the computer so you are un mounted and not logged in, un mounted is also good for fsck. Anyway doubt you have hdd glitches, it would run chkdsk at startup. Try from the grub menu going into recovery mode, don't use the terminal prompt mode unless you are very familiar with the command line

instead try selecting 'fix broken packages'

if that doesn't work and the system is almost crashing. Hey, you can get an external hard drive and back up all your files, or back up your home folder. Then re install the OS from your live cd, re partition using g parted if necessary. Then transfer your home folder by copy and paste with the external drive connected. Or use a command from another thread where they solved the issue today on this same sub forum. Which I believe is "rsync destination/ location/"(without quotes)

if you copy and paste, you will need permission to make chances to the file system through the GUI. In which case I don't recommend sudo su anymore, for some reason the admins recommend sudo -i. But neither of those will work really well with the gui, for that I recommend gsku nautilus at the terminal line.

I doubt any of that should be necessary though, try running repair broken packages from the grub menu

---

### Post by balasankarc on 2012-05-31
Hmm... I don't have any broken packages... Can't reinstall... So i'll just wait for the next gnome/ubuntu upgrade... anyway thanks for your effort.. well appreciated...

---

