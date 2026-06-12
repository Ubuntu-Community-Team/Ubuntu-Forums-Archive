---
title: "Pan Newsreader 'Refresh Groups' never finishes!"
date: 2010-01-02
forum: General Help
---

### Post by jim777 on 2010-01-02
Hi,
I am using Ubuntu 9.04 and with Pan Newsreader 0.132 or 0.133, the getting groups or Refresh groups task just keeps going.   I use Giganews which has
approx. 109000 groups yet Pan keeps on going showing 200000 or more groups and this task never finishes.  One time I left it going and it showed around
600000 groups and still going.  Just using default settings on port 119.
I have tried Pan 0.132 and Pan 0.132 as well.   same result.

Can anyone help me with this please?   Or is it a known problem with Pan and Giganews?

I can use Forte Agent and Wine but would like to get Pan working as well.
I tried Agent yesterday and it worked fine displaying the 109 000 groups no
problem at all.

---

### Post by jim777 on 2010-01-04
Tried again to get the groups list.   This time it worked, got to maybe 220000 groups & there they were.   Other times I tried my ISP had traffic shaping implemented & it was very slow.
Looks like a bug though because Giganews has around 109000 groups not 218000.   I might try to SSL working & use a non standard port to avoid the traffic shaping.

---

### Post by marcvdakker on 2010-03-01
Hello, I had the same problem with pan ( hangs during getting listings ) and i discovered that it has to do with 'assistive technologies'.
Go to System --> preferences --> assistive technologies and unmark 'enable assistive technologies' 
Press 'Close and log out'
When you are back 'Pan' newsreader will work again (i hope)
Succes!

---

### Post by jaybob20 on 2010-08-19
Turning off assistive technologies fixed it for me and so many other problems.

---

