---
title: "gnome-termianl opens and closes recursively forever in an endless loop."
date: 2012-01-14
forum: General Help
---

### Post by landstander on 2012-01-14
_Relevant Specs:_ 
OS: Ubuntu 10.04 (64bit) 

**_Problem (short description):_**
Opening a gnome-terminal session results in an endless loop of opening and closing gnome-terminal due to a setting listed in the long description of the problem below.

**_Problem (long description):_**
**_Warning: Do not try to reproduce this problem._**
These reproductions steps are included to help people understand what the problem is and how it started.
Steps to reproduce the problem:
1.) Open up a terminal window:
CTRL+ALT+T, or F2 and type in "gnome-terminal"
2.a) From the menu bar select Edit > Profile.
2.b) then select the "Default" profile.
2.c) then select Edit from the right hand side of the window.
2.d) Select the "Tittle and Command" tab at the top of the window.
3.a) Check the radio box that says "Run a custom command instead of my shell"
3.b) In the "custom command:" text box type the following command:
"gnome-terminal --geometry=100x44 --tab"
4.) Close all the windows, and the current gnome-terminal session and restart it.
5.) The gnome-terminal now forever opens and closes in an endless loop.
6.) If you did not heed the warning at the begining: To kill your endlessly looping gnome-terminal, do CTRL+ALT+F2 and login to a shell, then type "sudo killall gnome-terminal". When you logback into your GUI via CTRL+ALT+F7 (or it might be F6 or F8 depending on things I don't understand) the gnome-terminal should be killed, but don't try and open it again or it will be back in its endless loop. You will have to wait for a solution to this thread to fix it.

**_Question:_**
How can I put the gnome-terminal back to its original Default packaged state, or at the very least undo the settings I implemented above?
[B][U]
Note:[/U][/B] There is no way to currently change the settings via the menu in the GUI for the gnome-terminal because it is continuously closing and reopening. I have also tried purging the system of gnome-terminal gnome-terminal-data and reinstalled them but _the problem still persists_.

Thanks.

---

### Post by marshmallow1304 on 2012-01-14
Use Alt+F2 to launch gconf-editor.  Under /apps/gnome-terminal/profiles/Default uncheck the use_custom_command key.  Then find the custom_command key, right-click and click "Unset Key".

---

### Post by landstander on 2012-01-16
marshmallow1304

Thank you. I've run into problems similar to this before and have solved them using gconf-editor, but since these types of problems don't happen to me that often I always end up forgetting that I can use the gconf-editor to solve it.

Thank you for the much needed reminder. I'm adding a note about it in my troubleshooting files so I will remember it next time. :)

Thread solved!

---

