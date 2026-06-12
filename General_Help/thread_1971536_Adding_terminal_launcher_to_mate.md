---
title: "Adding terminal launcher to mate"
date: 2012-05-02
forum: General Help
---

### Post by codingman on 2012-05-02
I wanted to know how to add a terminal launcher to the panel. I've tried right clicking the panel and then clicking add to panel and then creating a custom application launcher and then  typing in the command of terminal and then it shows me the terminal icon in the top left corner and then clicking ok, but then when I click the launcher icon on the bar, I get an error that says it could not find the application "terminal".

Any help is appreciated!

---

### Post by david.rahrer on 2012-08-30
This question is a little stale but perhaps someone else will need the answer.  Normally you could launch a command in terminal from the Custom Application Launcher by choosing "Application in Terminal" from the first dropdown box.  However, it appears that this applet needs to be ported for use in Mate.  You can make it work in the mean time by chosing "Application" in the top dropdown and then appending "mate-terminal" to the front of your command (or by itself if you just want to lauch the terminal).  This is the name for the default terminal application in mate.

I looked for this in the Mate GitHub to see if I could make the change but couldn't find it.  This workaround should accomplish the same thing, at least it does for me.

Note:  Don't forget to add the -x after mate-terminal (mate-terminal -x [command here]) if you are running a command in terminal from the launcher.  This would be taken care of by chosing "Application in Terminal" if that applet was working properly in Mate, but you have to add it yourself until it get's ported.

---

