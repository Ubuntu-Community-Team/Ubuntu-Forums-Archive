---
title: "Comma between a date and time?"
date: 2011-12-01
forum: General Help
---

### Post by mr.interested on 2011-12-01
Hi there,

In the previous version of Ubuntu, there was a coma between a date and a time, for example, it showed:

Thu Dec 1, 12:49 PM

Now, it looks like this:

[[IMG]http://img703.imageshack.us/img703/8246/screenshotat20111201124.png[/IMG]](http://imageshack.us/photo/my-images/703/screenshotat20111201124.png/)

And it's very easy to read it as "1:12 PM". Is there any way to manually separate this by a comma?

Best

---

### Post by mr.interested on 2011-12-01
This ([http://askubuntu.com/questions/723/how-to-change-the-format-of-the-date-time-displayed-in-top-panel](http://askubuntu.com/questions/723/how-to-change-the-format-of-the-date-time-displayed-in-top-panel)) may provide an answer, but there doesn't seem to be a relevant option (clock applet) in the editor (dconf) for Ubuntu 11.10.

---

### Post by stinkeye on 2011-12-01
In dconf-editor, change 
time-format to **custom**
and then
custom-time-format to
```
%a %b %e, %l:%M %p
```

or whatever you like.
For date and time formats see...
```
man strftime
```

The dconf-editor window behaves strangely for me, so if you prefer
you can also do this in the terminal using...
```
gsettings set com.canonical.indicator.datetime time-format custom && gsettings set com.canonical.indicator.datetime custom-time-format "[COLOR="Magenta"]%a %b %e, %l:%M %p[/COLOR]"
```
[COLOR="magenta"]Shows as in pic or use your own format[/COLOR].

---

### Post by mr.interested on 2011-12-01
Many thanks stinkeye, it works perfectly! :-) The window-editor dconf also works strangely making it impossible to edit the time settings, but the command worked just fine.

Thanks for your help.

---

