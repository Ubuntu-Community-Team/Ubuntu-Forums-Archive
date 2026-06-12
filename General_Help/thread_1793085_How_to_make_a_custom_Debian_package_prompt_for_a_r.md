---
title: "How to make a custom Debian package prompt for a restart after installation"
date: 2011-06-29
forum: General Help
---

### Post by inameiname on 2011-06-29
I am wondering how to add a need to restart notification in a Debian package, so upon installation, it'd pop up something to tell the user to restart the computer for changes to take effect. Perhaps something like what happens with some packages through the update-manager when it prompts the user to restart for the changes to take effect.  

Is there any way to do that? Perhaps adding something at the end of a "postinst" file?


UPDATE:

Thinking about it, I could just add something like this at the end of the "postinst" file:

```

notify-send -t 86400000 -i /usr/share/icons/gnome/32x32/status/info.png "Please restart the computer for all changes to take effect."

```It'd work, but not as well. For instance, if the person isn't by their computer at the time.

UPDATE 2:

Another option could be using a Zenity dialog box. That might work. Though, if done, wouldn't a yes/no question box keep the actual package from technically finishing until the user would select yes/no to restart?

---

### Post by sam_delta on 2011-06-29
Ive personally used zenity in scripts that run as root and its not as simple as that because you have to export the display to the user root. It can be done, but id personally try look into another alternative. If you have no luck here, try asking in the motu (people on charge of managing packages of ubuntu repos) #ubuntu-motu on 'irc.freenode.net'.

sam

---

### Post by inameiname on 2011-06-29
Thanks for the tips. Maybe I will talk with those folks.

Its just a shame I can't figure out a simple method for the specific package to throw up some sort of notification prompting the user to restart, such as creating a launcher on the taskbar or something.

My zenity attempts were something along these lines, but as you said, permissions and root would cause problems:

```

if zenity --question --text="For changes to take effect, please press \"Yes\" to restart the computer."; then
    zenity --info --text="After you press \"Ok\", your computer will restart"
    sudo shutdown -r now
else
    zenity --error --text="You need to restart your computer for all changes to take effect."
fi

```I have a feeling the most simplistic means of doing something would be to do a notify-osd notification; its just it'd have to be extremely long, such as the 24hr one I put above. Annoying to those who refuse to restart their computer, but whatever. :P


UPDATE:

I found a way to tweak my notify-osd message, so it runs every 15 minutes, however, it doesn't work outside of a terminal window:


```

watch -n 900 "notify-send -t 60000 -i /usr/share/icons/gnome/32x32/status/info.png 'Please restart the computer for all changes to take effect.'"

```

---

### Post by sam_delta on 2011-06-29
between zenity and notify-send, i would go with zenity, you get into the same trouble and in my opinion its better to be prompt than to be informed by a notification.

The zenity code looks good, just keep in mind that the script is already running as root, so no need to use "sudo" in the shutdown statement, a simple 'shutdown -r now' would do.

What is it that it needs reboot? maybe some modprobes or services starts wouldn't do?

sam

---

### Post by inameiname on 2011-06-29
> **sam_delta said:**
> between zenity and notify-send, i would go with zenity, you get into the same trouble and in my opinion its better to be prompt than to be informed by a notification.

The zenity code looks good, just keep in mind that the script is already running as root, so no need to use "sudo" in the shutdown statement, a simple 'shutdown -r now' would do.

What is it that it needs reboot? maybe some modprobes or services starts wouldn't do?

sam


I would prefer to use zenity, however, when testing it, I found because it requires user input to continue, the package will not complete its installation until user input. Therefore, the notify-osd one is best, as it does pop up correctly and will stay there for as long as I have set (24hrs), until the user restarts. Plus, the package does get installed and finishes just fine using a notify-osd message. 

I am curious, though, just how the current notify-osd that seems to work above would get me into trouble because its root? I've tried this and it seems to pop up just fine.

And as for why I want to reboot in the first place, I have a 'sudo update grub" in this particular package, which does require a restart for any changes to take effect. Also inside is font changes, which I've noticed some (such as regarding Window titles) need to restart to be correctly switched to the correct font. Overall, there are several other things inside this package that change root files that require a restart. Its not a package I plan to update often, so a simple restart isn't needed very often.

---

### Post by sam_delta on 2011-06-29
Your right, notify-send might be a better option considering zenity would not let the install process to exit.

I see, i just did a test and it seems to be working fine (notify-send, and zenity running as root) i must have been wrong, its just that I recall a while ago when i was making a backup script which would ask you if you would like to make a backup each time you inserted a specific USB HDD, and i had to do do something like "export DISPLAY=:0.0" to make the X display available for root. Things might have changed tho.

sam

---

### Post by inameiname on 2011-06-29
> **sam_delta said:**
> Your right, notify-send might be a better option considering zenity would not let the install process to exit.

I see, i just did a test and it seems to be working fine (notify-send, and zenity running as root) i must have been wrong, its just that I recall a while ago when i was making a backup script which would ask you if you would like to make a backup each time you inserted a specific USB HDD, and i had to do do something like "export DISPLAY=:0.0" to make the X display available for root. Things might have changed tho.

sam


Hmmm, that would cause some trouble, indeed. I've never run across that in any scripting I've done to date. Maybe something did change, as you said, Idk. 

Anyway, I think I'll just use the notify-osd, as its the best option I can think of right now. Feel free to let me know if you or anybody else finds a better solution to this. Regardless, I'll mark it as solved. Good enough, for now.

---

