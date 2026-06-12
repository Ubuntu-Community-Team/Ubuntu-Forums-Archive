---
title: "How to add panels if there are none?"
date: 2010-03-05
forum: General Help
---

### Post by huggs on 2010-03-05
I followed the instructions in this guide to get the plasma workspace without having to migrate to kde:
[http://digitizor.com/2010/01/01/how-to-get-kde-plasma-workspace-ubuntu-9-10/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+digitizor+%28Digitizor%29]("http://digitizor.com/2010/01/01/how-to-get-kde-plasma-workspace-ubuntu-9-10/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+digitizor+%28Digitizor%29")

All went well, I was able to complete all the steps in the guide, and I double clicked the "plasma workspace.sh" and it launched the plasma workspace fine.
Then I tried using the gnome-desktop.sh the same way, but it just started the gnome desktop and quickly reverted to the plasma workspace. So I looked at the commands in the plasma.sh and the gnome.sh, and the commands on the guide page, and noticed they were the same for both shell scripts. So I changed the gnome desktop.sh from:

#!/bin/bash
killall fusion-icon
killall gnome-panel
killall plasma-desktop
plasma-desktop &
fusion-icon &

to:


#!/bin/bash
killall fusion-icon
killall gnome-panel
killall plasma-desktop
gnome-desktop &  <-------changed this line
fusion icon &

It seems to have gotten me back into the gnome environment, but now there is no top or bottom panel on my desktop. Since there is no top or bottom panel, I cant simply right click a panel and choose "add panel".
How do I add a panel now, and will launching the plasma workspace always kill my gnome panels, and if so, is there a workaround?

---

### Post by Ozymandias_117 on 2010-03-05
I'm assuming you followed this part of the tutorial? > # In gconf-editor, go to desktop -> gnome -> session -> required_components. Double click the panel option and remove the gnome-panel value. Close it. If so, I would say going back to desktop -> gnome -> session -> required_components and adding a new key with "name" as "panel" "type" as "string" and "value" as "gnome-panel" it should fix it.

edit: If you didn't actually delete the key, just put the value back to "gnome-panel"

---

### Post by huggs on 2010-03-05
ok i didnt actually delete the key, and i was able to bring up gconf-editor under kde, since i couldnt open a terminal under gnome (no menus to open it) and alt/f2 doesnt seem to work now for some reason. 
well i added gnome-panel back in as the value and still there are no top or bottom panels on my gnome desktop.

edit:  wow i went back to that guide and posted a comment, they got back to me and pointed me to :
[http://http://www.digitizor.com/wp-content/plugins/wordpress-toolbar/toolbar.php?wptbto=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1291048&wptbhash=aHR0cDovL2RpZ2l0aXpvci5jb20vMjAxMC8wMS8wMS9ob3ctdG8tZ2V0LWtkZS1wbGFzbWEtd29ya3NwYWNlLXVidW50dS05LTEwLzx3cHRiPkhvdyBUbyBHZXQgS0RFIFBsYXNtYSBXb3Jrc3BhY2UgVWJ1bnR1IDkuMTA8d3B0Yj5odHRwOi8vZGlnaXRpem9yLmNvbTx3cHRiPkRpZ2l0aXpvcg%3D%3D]("http://http//www.digitizor.com/wp-content/plugins/wordpress-toolbar/toolbar.php?wptbto=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1291048&wptbhash=aHR0cDovL2RpZ2l0aXpvci5jb20vMjAxMC8wMS8wMS9ob3ctdG8tZ2V0LWtkZS1wbGFzbWEtd29ya3NwYWNlLXVidW50dS05LTEwLzx3cHRiPkhvdyBUbyBHZXQgS0RFIFBsYXNtYSBXb3Jrc3BhY2UgVWJ1bnR1IDkuMTA8d3B0Yj5odHRwOi8vZGlnaXRpem9yLmNvbTx3cHRiPkRpZ2l0aXpvcg%3D%3D")
and the last steps in the almost identical guide are to install an emerald theme for some reason, replace the kde window manager with compiz and emerald, and to configure the kde applications to use the gtk engine. Nice to know the guide that i originally followed was so complete and accurate. I see from the guide i was pointed to that i was right to change that one line in the gnome desktop.sh , now how do i complete the rest of the steps since i cant access emerald or anything else under gnome to do the rest of the stuff? and if i do manage to complete these steps, would that bring my panels back?

---

### Post by huggs on 2010-03-05
I really hope I'm not screwed. I have had to uninstall and reinstall wubuntu like 8 times in the past 2 days.
(Nobody's fault but my own though)
just venting

---

### Post by Ozymandias_117 on 2010-03-05
That link you provided leads me to a blank page. After adding the key back, did you run: ```
sudo /etc/init.d/gdm restart
```

---

### Post by huggs on 2010-03-05
no i didnt. what does that do? and i put that link in using the little link adder widget at the top of the comment box. here it it copy and paste style, maybe that'll make a difference cause the page loads for me.

[http://www.digitizor.com/wp-content/plugins/wordpress-toolbar/toolbar.php?wptbto=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1291048&wptbhash=aHR0cDovL2RpZ2l0aXpvci5jb20vMjAxMC8wMS8wMS9ob3ctdG8tZ2V0LWtkZS1wbGFzbWEtd29ya3NwYWNlLXVidW50dS05LTEwLzx3cHRiPkhvdyBUbyBHZXQgS0RFIFBsYXNtYSBXb3Jrc3BhY2UgVWJ1bnR1IDkuMTA8d3B0Yj5odHRwOi8vZGlnaXRpem9yLmNvbTx3cHRiPkRpZ2l0aXpvcg%3D%3D]("http://www.digitizor.com/wp-content/plugins/wordpress-toolbar/toolbar.php?wptbto=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1291048&wptbhash=aHR0cDovL2RpZ2l0aXpvci5jb20vMjAxMC8wMS8wMS9ob3ctdG8tZ2V0LWtkZS1wbGFzbWEtd29ya3NwYWNlLXVidW50dS05LTEwLzx3cHRiPkhvdyBUbyBHZXQgS0RFIFBsYXNtYSBXb3Jrc3BhY2UgVWJ1bnR1IDkuMTA8d3B0Yj5odHRwOi8vZGlnaXRpem9yLmNvbTx3cHRiPkRpZ2l0aXpvcg%3D%3D")

edit: yep i just didi the gdm restart command and it didnt bring back my top or bottom panel. i have a bottom panel under the plasma desktop, just no panels under gnome.

---

### Post by Ozymandias_117 on 2010-03-05
The previous command will restart your gnome desktop manager, without restarting it, the change you made in gconf-editor won't actually change anything.

---

### Post by Ozymandias_117 on 2010-03-05
Sorry, if those didn't help you, I'm not sure what else to try. Maybe someone smarter than me can help you.

---

### Post by huggs on 2010-03-05
yeah, i did that, and it didnt bring back my top or bottom panels. is there a command i can type into the "run command" under the plasma desktop to just create a blank panel, top or bottom, in my gnome desktop?

---

### Post by huggs on 2010-03-05
> **Ozymandias_117 said:**
> Sorry, if those didn't help you, I'm not sure what else to try. Maybe someone smarter than me can help you.

Ok. Thanks for all the help that you were able to give me. I really appreciate it. Thanks to you, I am further along towards getting all this straightened out. :)

---

### Post by huggs on 2010-03-05
OK so I have completed all of the steps in the 2nd guide, and everything is perfect except that under gnome, i still have no top or bottom panels. so if anyone could please tell me how to create a top or bottom taskbar thing in gnome without the use of alt/F2, i will be all set. thanks in advance to anybody who can help me!!!!

Edit:
      Problem solved. Did a whole bunch of different stuff to try n fix it, eventually got my taskbars back. :-D  . Im sure this is far from the last time I mess up my comp, but Im glad to have it workin for the next little while at least.

---

