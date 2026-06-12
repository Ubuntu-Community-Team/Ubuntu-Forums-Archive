---
title: "Having a Windows manager issue? [ubuntu]"
date: 2010-05-03
forum: General Help
---

### Post by Algus on 2010-05-03
After upgrading from 9.10 to 10.04 my Windows Manager refused to load.  I spent the better part of the day trying to find a solution for it and it wasn't easy...but I did it! my manager is back, and starting on its own without my prompting.  I thought I'd write this post and share my experiences for other people who are having this issue.  

First and foremost a temporary workaround

```
metacity --replace
```

If you punch this into your terminal you should reload your basic manager and have things working fine again.  Unfortunately this is a temporary solution at best as you'll have to leave the terminal open (killing it ended up borking my keyboard of all things!) and put in the command every time you restart the machine.  Ergo, another solution is in order...

If you are like me (and others I've seen posting) you may have at one time been using Compiz and Emerald.  One solution is to reinstall both of these items in full.  Doing so will give Emerald control of your Windows Borders...but they will be back.  If you were thinking of going back to Emerald, now may be the time? 

You may give this a read 

[https://help.ubuntu.com/community/Metacity](https://help.ubuntu.com/community/Metacity)

Ultimately my solution was to fetch Compiz and fusion-icon (I junked Emerald as I do not like it...and I want my windows to have the new default Ubuntu look...for a bit)  

Ergo I used this command (from documentation above)

```
 sudo apt-get install fusion-icon compizconfig-settings-manager 
```

Per the documentation you can punch in

```
 fusion-icon 
``` in the terminal to get the icon.  Using the icon you can click to reload metacity via your GUI instead of having to play with the terminal.  

After you've got everything running smooth, do a log-off (or restart).  This was all I needed to do in order to get everything working again.   

For anyone else having a Windows Manager issue, I hope this is of at least some help in either solving (or tracking down) your issue.

---

