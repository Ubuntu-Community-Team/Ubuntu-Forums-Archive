---
title: "Cont. Monitor Processes and Close Blacklisted Ones If They Start"
date: 2011-10-26
forum: General Help
---

### Post by nunoxic on 2011-10-26
Hi,
I realized that there are awesome tools on chrome and firefox to blacklist sites and prevent the user from spending excessive time on them. (StayFocsd is an example)
I wanted something similar for my system. I wish to close any instance of vlc player, chromium, firefox or rhythmbox the moment they start but only for a particular user.
I have made 2 users :
Nunoxic (Actual one where I can do anything I want)
Focus_Nunoxic (One where vlc, firefox, chrome etc. should not open)

Any ways to achieve this ? 

I tried : 
writing a script : 

for (( ; ;))
do
killall chromium-browser
killall firefox-bin
sleep 5s
done

and putting this in .bashrc but this requires the user to keep a gnome-terminal open. I don't want this.

---

