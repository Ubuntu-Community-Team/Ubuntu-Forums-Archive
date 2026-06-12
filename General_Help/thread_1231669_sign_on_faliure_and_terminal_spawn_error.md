---
title: "sign on faliure and terminal spawn error"
date: 2009-08-04
forum: General Help
---

### Post by klunglejc on 2009-08-04
Usually don't reboot system unless upgrades require it. The other day, there were thunderstorms comming through our area (Martinsburg, WV) so I shut the system down. When I went to reboot the system, after the sign on and password, got a message saying the system was up for 10 seconds and then automatically shut down. Have a laptop running Ubuntu 9.04 also so booted it up and had no problem. Did a web search on the message I got after entering user id and password. Got several hits. One pointed me to the permissions on /dev/null being incorrect. Looked at the null file and permissions were -664. This was wrong so reset it to 666 (under root - chmod 666 /dev/null) Did this by using ctrl+alt+f1 to get to a terminal. After changing the permissions, I entered 'exit' which got me out of the terminal mode and back to the sign in screen. Entered id and password and the system brought up the gnome main screen. Thought everything was OK till I tried to bring up a terminal by clicking on the terminal icon. The terminal window came up but got a message child failure to spawn the terminal correctly. Again googled about child failure to spawn the terminal correctly. Got a lot of hits. People saying to redo mountdevsubfs.sh. Checking that pts is mounted. Adding a line of code to rcS for pts. None of this worked. Finally found a web page that stated the /dev entries were recreated every time when the system boots, and should look in /etc/udev/rules.d. So I started looking in each file and came to 99-hiddev.rules whose last entry was 'mode=664'. This was the permissions that were wrong so I changed it to read 'mode=666'. Saved the file and rebooted the system. Lo and behold so far every thing is working just fine. Wonder what changed that entry in the 99-hiddev.rules file.

---

### Post by blueridgedog on 2009-08-04
Excellent debugging.  It will be of help to others and perhaps light can be shed on what changed the file.

---

