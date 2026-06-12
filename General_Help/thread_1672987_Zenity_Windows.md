---
title: "Zenity Windows"
date: 2011-01-21
forum: General Help
---

### Post by fret669 on 2011-01-21
Hey all,

I've been making a "gui" for a script to help automate some of the steps involved in customizing a live cd with zenity. I have a menu with radio buttons for each option. When I pick "Remove a package manually", i have it show all of the installed packages as well as a text box for me to type the name into.

The only downside to this method is that the package window overlaps the text box. Is there a way to change the window position of zenity windows?

Thank you :)

---

### Post by VCoolio on 2011-01-21
See if you can have devilspie running by default on your livecd; then it's a piece of cake. Google it for some howto's, it's quite easy, works with .devilspie/anything.ds files. Or let your script run a wmctrl command to relocate zenity windows if that's possible. Just some ideas, hope it helps.

---

### Post by fret669 on 2011-01-21
Oh the live cd part works fine. The script I made to run all the commands to set up the environment is where I'm using zenity. For instance:

if [ blahh == blahh ]; then
    zenity --options --text "dpkg output" &
    zenity --input-box --package name
fi

That's the idea anyway. It is run on the host machine, not in the live cd itself. I have to move the windows out of each other's way lol. It's also possible that I misunderstood you :P Does happen from time to time. 

Searching now, thank you :)

I've come to the conclusion that it is very difficult with metacity :P I'll just live with it as it is. Thank You.

---

