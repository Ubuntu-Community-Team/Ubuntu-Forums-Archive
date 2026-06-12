---
title: "Minimizing bar gone as well as start button"
date: 2010-06-29
forum: General Help
---

### Post by paintball on 2010-06-29
How do I get these back? Thanks for the help.

---

### Post by Noz3001 on 2010-06-29
If by start button, you mean the Applications menu, right click a panel and add a Menu Bar. I don't know what a "Minimizing" bar is

---

### Post by flick on 2010-06-29
Hold down Alt key, press F2 key at same time.

In box that appears, type killall gnome-panel

Wait a second or two, your panels will disappear and then respawn/reappear

---

### Post by Andrew-J on 2010-06-29
If you still have your top panel you can right-click on it and select new panel. Then just orient it to the bottom.

I think start buttons if your talking about a traditional windows start button are dictated by whatever theme you have on. Have you changed this recently?

---

### Post by paintball on 2010-06-29
> **Andrew-J said:**
> If you still have your top panel you can right-click on it and select new panel. Then just orient it to the bottom.
 
I think start buttons if your talking about a traditional windows start button are dictated by whatever theme you have on. Have you changed this recently?
 When I right click there is no new panel option.
And I don't believe so.

---

### Post by Noz3001 on 2010-06-29
Oh, I see.

Remove these directories from your home to reset gnome settings.

```
rm -rf .gnome .gnome2 .gconf .gconfd
```

---

### Post by Abu Azzubair on 2010-06-29
No need to worry  O:) 

Go to Terminal (ctrl+alt+T...or Applications, Accessories, Terminal)

Type:

'sudo shutdown -h now', then type your password, and press "enter"...that's to shutdown the computer/laptop

'sudo reboot', then type your password, and press &#8220;enter&#8221;...that's to restart the computer/laptop




That happened to me, and to be honest that's how I ended up for a while


But the people above me have recommended more strait forward ways

---

### Post by paintball on 2010-06-29
> **Noz3001 said:**
> Oh, I see.
 
Remove these directories from your home to reset gnome settings.
 
```
rm -rf .gnome .gnome2 .gconf .gconfd
```
 And how do I do that? To be honest I am just a noob.

---

### Post by Noz3001 on 2010-06-29
Just open a terminal and paste that command in. Then log out and back in.

---

### Post by Andrew-J on 2010-06-29
Thats a command line for the terminal go to applications>accessories>terminal

---

### Post by paintball on 2010-06-29
> **Noz3001 said:**
> Just open a terminal and paste that command in. Then log out and back in.
Ok, I need to figure out how to get to applications so I can open a terminal.
> **Andrew-J said:**
> Thats a command line for the terminal go to applications>accessories>terminal
How do I get to applications?
 
 
Thanks for the helps guys.

---

### Post by Noz3001 on 2010-06-29
Ctrl+Alt+T should do it or you could use Alt+F2

---

### Post by Andrew-J on 2010-06-29
Hit Alt+F2 and then select show applications in that window and then select Terminal and hit run.

Do you not have an upper task bar either?


Noz stop responding so fast. :)

---

### Post by paintball on 2010-06-29
> **Noz3001 said:**
> Ctrl+Alt+T should do it or you could use Alt+F2
 Neither worked
> **Andrew-J said:**
> Hit Alt+F2 and then select show applications in that window and then select Terminal and hit run.
 
Do you not have an upper task bar either?
 
 
Noz stop responding so fast. :)
 I believe I have an upper task bar. Thats the one that says fiel edit view etc. right?

---

### Post by Noz3001 on 2010-06-29
Oh dear. Ctrl+Alt+F1 then, login and type it

---

### Post by Andrew-J on 2010-06-29
Mine are different than yours apparently, but no matter. run the line and see what it does for you.

Typically, i think, the upper task bar has "Applications,Places,Sytem" all on the left and a power button on the right.

---

### Post by Andrew-J on 2010-06-29
WAIt! after you hit ctrl+alt+F1 to get back to normal hit ctrl+alt+F7

---

### Post by Noz3001 on 2010-06-29
> **Andrew-J said:**
> WAIt! after you hit crtl+alt+F1 to get back to normal hit crtl+alt+F7

Haha, oh yeah, there's that too. I'm sure he'd be able reboot if he's already done it =P

---

### Post by paintball on 2010-06-29
> **Noz3001 said:**
> Oh dear. Ctrl+Alt+F1 then, login and type it
 Ok, how do I login at the window that pops up when I press those buttons?
> **Andrew-J said:**
> Mine are different than yours apparently, but no matter. run the line and see what it does for you.
 
Typically, i think, the upper task bar has "Applications,Places,Sytem" all on the left and a power button on the right.
 Ok Ill try it once I figure out how to login from there. 
 
Thanks again guys

---

### Post by paintball on 2010-06-29
> **Andrew-J said:**
> WAIt! after you hit ctrl+alt+F1 to get back to normal hit ctrl+alt+F7
 When I do that it asks me to turn on or off caret browsing.

---

### Post by Andrew-J on 2010-06-29
you have to type in your user name hit enter then your password hit enter.

---

### Post by Andrew-J on 2010-06-29
Caret browsing? I'm sorry i'll have to bow out to greater minds now.

---

### Post by paintball on 2010-06-29
> **Andrew-J said:**
> you have to type in your user name hit enter then your password hit enter.
 Obviously, but there isnt anywhere to enter that.

---

### Post by Andrew-J on 2010-06-29
Alrighty settle down there I wasn't trying to be insulting.

I'm not finding out much through google. but what the heck i'll just google harder.

---

### Post by paintball on 2010-06-29
> **Andrew-J said:**
> Alrighty settle down there I wasn't trying to be insulting.
 
I'm not finding out much through google. but what the heck i'll just google harder.
 Same here, just am frustrated about this you know? Alright, thanks man.

---

### Post by Andrew-J on 2010-06-29
Okay i still don't know what it is but i found that F7  toggles caret browsing....or it does on my system anyway.

---

