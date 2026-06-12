---
title: "Terminal title"
date: 2011-01-04
forum: General Help
---

### Post by Lism on 2011-01-04
Hey,

Is there a way to change the terminal title without using using the command line interface?

Even better would be a way to hide the terminal window but not close it.

GNOME terminal btw

---

### Post by KJ KJ KJ on 2011-01-04
Right click inside the terminal, choose Profiles, then Profile Preferences, then the 2nd tab 'Title and Command' - note the drop-down box under Title.

What exactly would you like to do with hiding the terminal? If you want a terminal you can bring up anywhere, hide when you don't want it, but keep its state while hidden, there are ways to do this.

---

### Post by ajgreeny on 2011-01-04
Use Alt+F2 and enter gconf-editor.  In the window that appears navigate to gnome-terminal->profiles->Default and then use the title and title_mode keys as shown in screenshot.

The terminal title in the top bar will then show **Gnome-terminal - user@host:~**

Is that what you meant by terminal title?

EDIT:-

Silly me!  I didn't think about KJ's method.  It does the same thing, but now you know two ways to do it.

I also forgot the screenshot; now added.

---

### Post by Lism on 2011-01-05
Yes, like in windows you can enter:

```
title "my_title"
``` I want to be able to do that but from the command line.

See, i've created a launcher from the desktop to launch Spotify in WINE, as if it is a windows installation. I want a command to add to the launcher command so that the terminal is called spotify too. Just like you can in a windows batch file.

Like I said, a way to hide the terminal from the task bar would be better.

---

### Post by claydon on 2011-01-05
I hope you don't mind me butting in on this thread but I'm looking for something similar. 

In Windows when you telnet via the command prompt the title changes to the device you are connected to. Is there anyway for terminal to show this. I manage switches for a living and am often connected to a few at a time so this would be helpful for me.

---

### Post by Lism on 2011-01-05
Yeah, I work with many different terminal windows and I want this unused one to either go away or be named.

---

### Post by KJ KJ KJ on 2011-01-05
> **claydon said:**
> I hope you don't mind me butting in on this thread but I'm looking for something similar. 

In Windows when you telnet via the command prompt the title changes to the device you are connected to. Is there anyway for terminal to show this. I manage switches for a living and am often connected to a few at a time so this would be helpful for me.

It's a mission, but you should be able to do it. 

[http://www.ibm.com/developerworks/linux/library/l-tip-prompt/](http://www.ibm.com/developerworks/linux/library/l-tip-prompt/)
and, for the ultimate in details:
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

---

### Post by KJ KJ KJ on 2011-01-05
> **Lism said:**
> I want a command to add to the launcher command so that the terminal is called spotify too.

```
gnome-terminal --title=Spotify
```> **Lism said:**
> 
Like I said, a way to hide the terminal from the task bar would be better.


OK, you'll have to do some reading and some shell script programming, but it's do-able

[http://www.semicomplete.com/projects/xdotool/xdotool](http://www.semicomplete.com/projects/xdotool/xdotool)

You can install it on Ubuntu.

---

### Post by Lism on 2011-01-05
Thanks a lot KJ!

Works sort of, i'm gonna look into the window hiding option.

Thanks again.

---

