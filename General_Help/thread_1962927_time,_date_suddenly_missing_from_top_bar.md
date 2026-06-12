---
title: "time, date suddenly missing from top bar"
date: 2012-04-21
forum: General Help
---

### Post by kline on 2012-04-21
What did i do?!  i was looking for a calender app and somehow the time and date string [with month drop-down] are now vanished.  after an hour of hunting i thought i'd ask here.  

on the top bar, no mouse buttons work on the empty space; only on my login and in the extreme upper-right ...

can anybody clue me in?

---

### Post by llamabr on 2012-04-21
Not sure.  Maybe a screenshot would help us to figure out what you're talking about.

---

### Post by stinkeye on 2012-04-21
Check if **indicator-datetime** is still installed
```
aptitude show indicator-datetime | grep State
```

If installed try resetting to defaults
```
gsettings reset-recursively com.canonical.indicator.datetime
```

---

### Post by kline on 2012-04-21
> **stinkeye said:**
> Check if **indicator-datetime** is still installed
```
aptitude show indicator-datetime | grep State
```

If installed try resetting to defaults
```
gsettings reset-recursively com.canonical.indicator.datetime
```


pts/1 17:54 <tao> [5800] aptitude show indicator-datetime | grep State           ~/Desktop
State: not installed


hmm, 'State: not installed'  

i just took a screenshot from workspace4....  you'll see that before my username or login, 'kline' is where the day and date strings were. to thr right of the spkr icon and to the left of the head.

now what.,,, :)

ok, it says w4.jpg {48.2k} is there.

---

### Post by stinkeye on 2012-04-21
reinstall
```
sudo apt-get install indicator-datetime 
```

May have to log in/out for it to appear.

Something you tried to install must have uninstalled it due to conflicts.

I always use synaptic, so I can check if anything is being uninstalled.

---

### Post by houseworkshy on 2012-04-21
I'm still on the LTS so this may be invalid but .... Can you right click on the top bar, choose "Add to panel" and simply put it back?

---

### Post by stinkeye on 2012-04-21
> **houseworkshy said:**
> I'm still on the LTS so this may be invalid but .... Can you right click on the top bar, choose "Add to panel" and simply put it back?
Not with the unity panel.

---

### Post by kline on 2012-04-21
well, fwiw, i Did install the 'indicator-dateline,'   then sat here for about a *month* waiting for the seas to part....  i finally checked and saw that i did have to do yet-another-reboot.  this was my fourth today.  

but yes, the day/month  s tring is back.  

[whew]    :-|

---

### Post by Gremlinzzz on 2012-04-21
so problem solved:popcorn:

---

### Post by kline on 2012-04-21
> **stinkeye said:**
> Not with the unity panel.

Yo, good thing i checked.  this is another thing that ubuntu has done that i dont like....  it may explain why right-clicking in/on the top bar does nothing.  i already got rid of the binary that gave you only one menu on konsoles, e.g.     how can i get rid of this unity hack?

i have a netgate hardware firewall so i'm not worried about some cracker breaking in and stealing my poetry.....  Zeus forbid.  that said, i do not trust any free cloud backups. i have enough computers and disk and do my own backups.  i would appreciate others' opinions.

PROBLEM SOLVED!

---

