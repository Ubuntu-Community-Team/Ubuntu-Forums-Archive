---
title: "Couplle things i want to fix"
date: 2010-01-20
forum: General Help
---

### Post by tarvtarv on 2010-01-20
Hi theres some minor annoyances i would like to fix if anyone would be kind enough to help me thanks in advance.

1. Stop the tomboy "Search all notes" window from showing at startup.

2. when i do a search in tracker it shows more than one entry for some applications eg. text editor.

3. how can i add the places menu to the panel

4. i have a bash script that isnt working for some reason i already made it executable but do i have to put in in the /usr/bin/ for it to work?

5. how to get firefox to subscribe to a page using blam as the reader


I would really appreciate some answers if anybody has the time

---

### Post by michy99 on 2010-01-20
I may have a solution for number 1. Go to System->Preferences->Startup Applications. Click Options tab. Make sure that 'Automatically remember running applications when logging out' has a check mark. Log out and then log in. Now go back and remove the check mark.

If you want help with a bash script, you need to post the script.

Also, it's better to stick to one problem per post.

---

### Post by n0dix on 2010-01-20
4. Sure the script has the execute permission?? Post the ls -la command. You don't need to put the script in /usr/bin to work. If it's not a problem, can you post the script

---

### Post by wojox on 2010-01-20
#4 If it needs sudo privileges try

```
sudo ./myscript
```

Else

```
./script
```

Make sure your in the directory that's holding you script.

---

### Post by wojox on 2010-01-20
# 3 Right click the panel and select Add to Panel and select Menu Bar.

---

### Post by tarvtarv on 2010-01-21
**wojox** thanks for getting back to me I got the script to work it just needed some adjustment ill post it here in case anybody wants it {it clears the recently used documents list in ubuntu} No guarantees but it works for me on intrepid...Thank you to the person who posted it on gnomehacks.org


**michy99** i tried what you said but the window still shows at at startup [is there a command option to achieve this]


also **wojox** for problem #3 i wanted just the places section of the main menu applet not the applications and system aswell


anyone know how to subscribe to feeds with blam?

or to remove duplicate entries in the applications list?

---

### Post by tarvtarv on 2010-01-21
Oh the big annoyance was when i set nautilus to show a folder in the compact view i cant scroll horizontally with my mouse any ideas/?

---

