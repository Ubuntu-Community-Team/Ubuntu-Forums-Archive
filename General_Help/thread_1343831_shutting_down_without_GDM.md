---
title: "shutting down without GDM"
date: 2009-12-02
forum: General Help
---

### Post by cong06 on 2009-12-02
I've managed to get Ubuntu to load nicely without gdm:
[http://ubuntuforums.org/showpost.php?p=4552480&postcount=3](http://ubuntuforums.org/showpost.php?p=4552480&postcount=3)

The problem is that the power button on the front doesn't work to turn it off, and that by going to "shutdown" I'm given a terminal.

Does anyone have a work around? or do I have to install gdm to get these features back?

---

### Post by coffeecat on 2009-12-02
To shutdown from a terminal:

```
sudo shutdown -h now
```It's also useful on the rare occasions that your GUI freezes up solid. Simply ctrl-alt-F1 to a virtual console, login and use the above command.

And ....

```
sudo shutdown -r now
```... gives you a reboot. See man shutdown if you want a time other than 'now'.

---

### Post by cong06 on 2009-12-03
> **coffeecat said:**
> ```
sudo shutdown -h now
```

I'm sorry, a bit of background is in order.
I'm installing these computer for other people, and have decided that it's better to not install gdm to save memory.

Telling people they need to learn command prompt to turn off their computer is unacceptable. I'd rather write a script:
```
gksudo shutdown -P 0
``` and place it on the desktop

I would, however, rather do this without requiring root privileges, and if possible by simply restoring the features I had when I had GDM installed.

So with that in mind. Any ideas?

---

### Post by coffeecat on 2009-12-03
I see what you mean. A bash script invoking shutdown would obviously need root privileges, so that doesn't help you.

According to the link in your first post, you must be running fluxbox rather than gnome. You might want to edit your thread title to include 'fluxbox' to catch the attention of someone familiar with that DE. I'm not. Sorry.

---

### Post by cong06 on 2009-12-03
> **coffeecat said:**
> According to the link in your first post, you must be running fluxbox rather than gnome. You might want to edit your thread title to include 'fluxbox' to catch the attention of someone familiar with that DE. I'm not. Sorry.

I'm actually not running fluxbox ;)
That was just the best instructions I could find to get running without login. I'm actually trying to stick to Nautilus for various compatibility reasons and ease use.

---

### Post by JKyleOKC on 2009-12-03
Take a look at the "visudo" command, which lets you make special modifications to the "sudo" actions. Specifically, you can configure the system to not require a password to execute the shutdown command, and then add a launcher to the desktop to call "sudo shutdown now" without needing a password or a terminal...

There's even a specific example in "man visudo" showing how to set up the shutdown!

---

### Post by cong06 on 2009-12-04
Well, I didn't find the example in man visudo, but I found it here:
[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

I'm gonna take this and run with it. Thanks.

---

### Post by cong06 on 2009-12-05
Well, that was premature.

I changed the /etc/sudoers file (with visudo) to add the line:
```

user   ALL=NOPASSWD:/sbin/shutdown

```
And now when I type "sudo shutdown now" in to commandline, it works.

But if I write a script and run the script (either through the gui OR as a regular script from commandline) it still prompts for a password...

What's going on? I was sure that sudoers would do it. Somehow the scripts are being treated differently...

---

### Post by blueridgedog on 2009-12-05
> **cong06 said:**
> I'd rather write a script:
```
gksudo shutdown -P 0
``` and place it on the desktop

I would, however, rather do this without requiring root privileges, and if possible by simply restoring the features I had when I had GDM installed.


You could investigate setting the shutdown script to run as root with setuid:

[http://en.wikipedia.org/wiki/Setuid](http://en.wikipedia.org/wiki/Setuid)

Note that there are substantial security risks involved in root setuid scripts and this should be a last resort.

---

### Post by ibuclaw on 2009-12-05
Is Gnome-Power-Manager running?

Adding that to your autostart applications should help...

---

### Post by cong06 on 2009-12-05
> **tinivole said:**
> Is Gnome-Power-Manager running?

Adding that to your autostart applications should help...

gnome-power-manager is running. tail -f /var/log/messages gives no output when I press the power button. That's what you were expecting?

I think it makes sense that I'll need to go with a script, (unless there's something more elegant that I've missed), I just can't figure out why the script doesn't work.

At least I have blueridgedog's back up plan.

---

### Post by JKyleOKC on 2009-12-05
Your addition lets userid "user" avoid the password, but apparently the script runs as a different user. Take a look at how to specify group specs, using the original "admin" item in sudoers as an example, and change the "user" part of your new line to match.

Also note that the sequence of lines in sudoers may be significant. I remember running into this a few years ago but don't recall whether it's the first, or the last, line that takes effect when two lines contradict each other...

---

### Post by ibuclaw on 2009-12-05
> **cong06 said:**
> gnome-power-manager is running. tail -f /var/log/messages gives no output when I press the power button. That's what you were expecting?

I think it makes sense that I'll need to go with a script, (unless there's something more elegant that I've missed), I just can't figure out why the script doesn't work.

At least I have blueridgedog's back up plan.
It should output anything into /var/log/messages when pressed...


OK, so going into System->Preferences->Power Management.
In the "General" tab, what is it set to on the "**When the power button is pressed**" dropdown?

Gnome should adhere to that setting - but I guess it is possible that skipping GDM circumvents a certain process which monitors this.

---

### Post by cong06 on 2009-12-07
> **tinivole said:**
> OK, so going into System->Preferences->Power Management.
In the "General" tab, what is it set to on the "**When the power button is pressed**" dropdown?

It was "Ask me"
Switching it to "Shutdown" did nothing. (as in, no response, and still nothing in /var/log/messages)

I'm still puzzled why the [visudo + script](http://ubuntuforums.org/showpost.php?p=8432466&postcount=6) idea [didn't work](http://ubuntuforums.org/showpost.php?p=8443941&postcount=8)...

---

### Post by ST3ALTHPSYCH0 on 2009-12-07
Since you can shutdown from the CLI w/out passw, but not script.... have you tried a launcher instead of a script?

---

### Post by cong06 on 2009-12-07
> **ST3ALTHPSYCH0 said:**
> Since you can shutdown from the CLI w/out passw, but not script.... have you tried a launcher instead of a script?

Launchers react the same as scripts...
If I set "Terminal=true" it pops up and prompts for a password.
Otherwise it just does nothing.

---

### Post by cong06 on 2009-12-07
Wow. that's really embarrassing.
I hadn't actually gotten the /etc/sudoers file working right. and I couldn't tell because I would run sudo on something, and then since it stores the password it wouldn't ask the second time.

So... actually it works. as long as you put the "NOPASSWD" line on the last line of /etc/sudoers.

---

### Post by ST3ALTHPSYCH0 on 2009-12-07
That was good for a chuckle.... but I'm glad you posted the solution. I once had a "log out" launcher not working on one account. I beat my head against the keyboard for days before realizing that I had omitted a space in the command sequence.

---

