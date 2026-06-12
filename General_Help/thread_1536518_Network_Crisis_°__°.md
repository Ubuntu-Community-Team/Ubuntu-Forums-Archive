---
title: "Network Crisis °_ °"
date: 2010-07-22
forum: General Help
---

### Post by Alessandro.Previti on 2010-07-22
Network crisis °_°

Hi! I'm a ubuntu user from v.8; i just installed the new ubuntu on my mother's pc, it's a hp laptop.
I enjoyed the ease of use of the new windows installer. Sadly i fell into 2 troubles!

1) internet connection: my ubuntu can't detect any wi-fi in my home; can detect a normal lan connection but when i try to load a page it loads just few elements from the web and stays loading and loading and loading; a google search is composed just by the text box for the search and some texts, not even google logo appears.
I tried many tutorials for ipv6 deactivation, done.. and nothing.. i configured the ip manually.. nothing.. T_T DESPERATION! I DON'T WANT TO GO BACK TO WINDOWS...

2) Another minor issue, maybe someone can help me with it: after installing ubuntu with the win installer i have now 2 boot menu... quite too many! At start the pc asks me without any timer "windows or ubuntu" when selected i go to another selection screen with "windows" "ubuntu" "ubuntu recovery"; can i remove one of the seleciton screens?

THAAAANKS!!! :KS

---

### Post by quixote on 2010-07-24
When you say "can't detect any wifi" and "can detect normal lan" what do you mean?  Do you mean the second one is a wired connection?  Run the following two commands in a terminal (Applications > Accessories > Terminal), and copy the results in your answer.  (An easy way to copy from the terminal is to select what you want with the mouse, and then use ctrl-**shift**-c to copy.  To paste here use the regular ctrl-v, of course.)```
sudo ifconfig
sudo iwlist scan
```

The browser problem is very bizarre.  I have no idea what could be causing that.  Which browser do you use?  Maybe just try reinstalling it using synaptic. (System > Admin > Synaptic)

I don't know much about wubi installs (i.e. ubuntu installed from within Windows), so I don't know if there's an easy fix for the double boot menu annoyance. Maybe someone else will chime in.

---

