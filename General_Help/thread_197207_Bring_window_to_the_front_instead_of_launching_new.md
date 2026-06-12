---
title: "Bring window to the front instead of launching new instance"
date: 2006-06-15
forum: General Help
---

### Post by giuliastro on 2006-06-15
Hello,
This is more Gnome related.. anyway, I would like to set applications in my gnome panel so that when I click on them it checks if the application is already open and instead of opening a new instance it brings the window to the front.
I googled a little bit but haven't found anything.. any suggestions? Thanks in advance!

---

### Post by aysiu on 2006-06-15
How about instead of clicking the launcher, you just click the application's window list item?

---

### Post by giuliastro on 2006-06-15
Thank you aysiu, that's a good suggestion. But I end up opening twenty terminal windows every time, my window list gets full and small and it keeps getting worse. Also, it would be much easyer to have everything in one dock (list and launcher) pretty much as some docks do.. unfortunately there are no good docks for Linux, or at least docks that work well with XGL (gnome panel, ends up to be the best one). Anyway .. I would expect some dbus-send message to bring to front the window..

---

### Post by Anduu on 2006-06-15
He is probably like me and forgets it is already open :-P

---

### Post by eth on 2006-06-15
buy Alt+Tab!

---

### Post by giuliastro on 2006-06-15
[QUOTE=eth]buy Alt+Tab![/QUOTE]

Ok, if I open up many terminals it means I just click without stopping and thinking. Alt+Tab is not a good suggestion, since I do not know my terminals are already open. :)

---

### Post by aysiu on 2006-06-15
How about using tabbed browsing? I think that's available for the Gnome terminal.

I'm not sure if it's available for Nautilus, but that's worth investigating. It's definitely available for web browsers.

You can also, if you have many terminals open, try using the virtual terminals: Control-Alt-F1, Control-Alt-F2, etc.

---

### Post by Quirky on 2006-06-15
Tabbed windows in the terminal are great. That and "Always On Visible" means you only need 1 terminal window ever.

Shift+ctrl+T to open a new tab. I changed the key mapping to shift+left shift+right to switch tabs (like in Konsole).

---

### Post by aysiu on 2006-06-15
That is the wonderful thing about tabbed browsing, really. I remember before I switched to Firefox, I used to have a gazillion Internet Explorer windows open, and I could never sort through them all or easily switch to another application.

Now with tabbed browsing, I know distinctly on the taskbar--oh, that's my text editor; oh, that's my terminal; that's my web browser; etc.

---

### Post by mannheim on 2006-06-15
One way to do this is to use a script. This is what I do. I want a launcher on my panel for Thunderbird (for example). But I want this launcer to check if an instance of Thunderbird is already open on the desktop: if it is open, then I just want to bring that window to the front; otherwise, I want to just launch Thunderbird. These days (with dapper), I think that t-bird just behaves this way without needing to mess around like this. But I'll illustrate with t-bird.

To do this, I first installed wmctrl from the universe repostirories. This is a command-line utility that can list open windows, bring them to the front etc. Then I wrote a script, using wmctrl. Then I created a launcher on the panel, which just runs the script. For thunderbird, the script looked like this (excluding the annotations in blue):

```
#! /bin/bash

WINTITLE="Mail/News"            [COLOR="Blue"]# Main Thunderbird window has this in titlebar[/COLOR]
PROGNAME="mozilla-thunderbird" [COLOR="Blue"]# This is the name of the binary for t-bird[/COLOR]

# Use wmctrl to list all windows, count how many contain WINTITLE,
# and test if that count is non-zero:

if [ `wmctrl -l | grep -c "$WINTITLE"` != 0 ]  
then
        wmctrl -a "$WINTITLE"       [COLOR="Blue"]# If it exists, bring t-bird window to front[/COLOR]
else
        $PROGNAME &                  [COLOR="Blue"]# Otherwise, just launch t-bird[/COLOR]
fi
exit 0

```

Save this script as "my-tbird-script" and make it executable. Click on panel, and create a "Custom Application Launcher ... ". Make the command point to your script. Give it the t-bird icon. Change WINTITLE and PROGNAME to adapt your script to any other application.

As I said, for t-bird this is redundant now, I believe. For gnome-terminal, it is a bit tricky, because the title-bar doesn't have a "signature" that makes it easily recognizable in the list of windows. You can work around that by changing your default profile in terminal so that the title bar always contains "Terminal".

---

### Post by giuliastro on 2006-06-15
Again, to do multiple tabs you need to find the first terminal window that is somewhere in one of your monitors / views behind some of your windows (I have a multi-monitor system), if any. Actually the best and simplest way would be having my terminal shortcut behave this way when I click on it:

- Check if any other terminal windows are open (ps -A | grep gnome-terminal?)
-- If there aren't active terminal windows then just open one
-- If there are active terminal windows just bring the first one to front

What I miss is to find the way to bring a window to the front using command line or whatever.

---

### Post by giuliastro on 2006-06-15
That's it, mannheim! I will get wmctrl. :) Thanks a lot.

---

### Post by newsun on 2007-12-17
this is great, only does not work if the open app does not have any windows like skype can have.

I wonder why they took that feature out for linux, the ability to focus the contact list

---

### Post by spacedoubtman on 2008-02-10
mannheim, thanks. I have been trying to find a tool like wmctrl.for ages  - this is very usefull when controlling a computer with a remote control

---

