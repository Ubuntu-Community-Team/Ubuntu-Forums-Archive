---
title: "Closing/minimizing a program"
date: 2010-10-27
forum: General Help
---

### Post by romerje on 2010-10-27
Hello All,
 
Just got Mythbuntu installed and working this weekend(new to Linux)...but apparently I did something to mess up how I close a program. Right now when I open a program I have a little tab that shows up on the top of the window of the open program and the x and minimize button that usually shows up on the right side to close or minimize the program is gone!! Can't seem to find out where the fix is. Right now I have to right click on the tab and scroll down to quit!! Can anyone help!!
 
Thanks
Jennifer

---

### Post by sikander3786 on 2010-10-27
Press Alt + F2, type **gconf-editor** and hit enter. Navigate to apps > metacity > general and 'button layout' key should have the value 'close,minimize,maximize:menu'.

Change the order if you want them on the right side. It should be 'menu:minimize,maximize,close' then.

---

