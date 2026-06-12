---
title: "Help with BURG"
date: 2010-08-09
forum: General Help
---

### Post by borth92 on 2010-08-09
Just a quick question, I want to partition my computer with Ubuntu, WinXP, and Win7. Is there a way I can change the icons in burg so the xp and 7 icons look a little different?

---

### Post by borth92 on 2010-08-09
not to sound impatient, but im just keeping the thread at the top

---

### Post by borth92 on 2010-08-09
cmon people, someone has got to have an idea...

---

### Post by dcstar on 2010-08-10
> **borth92 said:**
> Just a quick question, I want to partition my computer with Ubuntu, WinXP, and Win7. Is there a way I can change the icons in burg so the xp and 7 icons look a little different?

As the BURG site says, there are numerous themes you can install and use.

---

### Post by dshosu on 2010-08-10
I did what you are trying to do but with two linux distros (Ubuntu NBE, and BackTrack4). In short what you have to do is define two new OS classes for two new icons sets.

[LIST=1]
[*]create the icons you want to use for win7 and winxp with [using these guidelines]("http://code.google.com/p/burg/wiki/ThemeCustomization")
[*]you should now have 6 images (3 for each OS (grey_*, [COLOR="red"]**small_***[/COLOR], and large_*). Now you need to put those in the icon folder.
[*]```
sudo nautilus
```
[*]navigate to /boot/burg/themes/icons
[*]copy your 6 new icons to that directory (if you saved them to your user directory, that's located in /home/*username, took a while to figure that out.)
[*]open "grey", "hover", "large", and "small" (these define what icons go with which OS class, more on that later)
[*]insert 2 lines at the top of each file for your two new icons

     *in your case something like:   
```
-[COLOR="blue"]**windows7**[/COLOR] { image = "$$/[COLOR="Red"]**small_windows7**[/COLOR].png" }
-windowsxp { image = "$$/small_windowsxp.png" }
```
[*]Now you need to change the classes of your OSs in burg. There are two ways to do this. 
[INDENT]a) using 40_custom ([link]("http://ubuntuforums.org/showthread.php?t=1195275"), see #6)
b) using GRUB_CLASS_OVERRIDE ([link]("http://code.google.com/p/burg/wiki/ConfigurationVariables"))[/INDENT]
...I could go on from here but depending on how you have your system setup I could walk you through more harm than good. But basically you need to change the lines in your burg.cfg (*don't change it directly in burg.cfg or you will lose it anytime you run "sudo update-burg". If you don't plan to run that again you could get away with it but the 2 other methods are much more stable*) from

```
menuentry "**windows 7 title**" --class windows --class os {....etc
```
...to...
```
menuentry "**windows 7 title**" --class [COLOR="Blue"]**windows7**[/COLOR] --class os {....etc
```
...and the same for the WinXP entry.
[/LIST]

---

