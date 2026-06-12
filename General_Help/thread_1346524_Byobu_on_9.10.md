---
title: "Byobu on 9.10"
date: 2009-12-05
forum: General Help
---

### Post by gibbylinks on 2009-12-05
I've been looking at Lucid Lynx 10.04. (Created a USB image and booted from it). It's the first time I've come across Byobu and I was impressed.

Thing is I'd like to use it instead of terminal in my current 9.10 set-up, and I was pleasantly surprised to find it already installed in synaptic.

Thing is....it doesn't appear in the menu under system tools like 10.04. Where can I find it and can I add it to my awn dock ?

Thanks ;)

---

### Post by jnew93 on 2009-12-28
I understand this thread is a few weeks old, but I found this via google search and couldn't resist the urge to help anyone else who finds this thread. Here is the solution: simply run 

```
byobu
```

in your terminal for it to start.

If you then wish to have it run every time you open terminal, first in byobu's menu (press f9) turn start on login to yes. Second, in the terminal you have open, navigate to Edit>>Profile Preferences>>Title and Command. Then tick "Run Command as a Login Shell". This will enable Byobu to start when you launch gnome-terminal. :)

Cheers!

---

### Post by gibbylinks on 2009-12-28
Thanks for response.

Only glitch is when I press F9 screen goes dull and nothing appears, going to try reinstalling byobu. I'll let you know if it helps

Cheers

---

### Post by gibbylinks on 2009-12-28
Update.

Thanks to jnew93 I've got this working now.

> If you then wish to have it run every time you open terminal, first in byobu's menu (press f9) turn start on login to yes. Second, in the terminal you have open, navigate to Edit>>Profile Preferences>>Title and Command. Then tick "Run Command as a Login Shell". This will enable Byobu to start when you launch gnome-terminal. :smile:All I've done different is instead of ticking "Run Command as a Login Shell" I've ticked 
"Run a custom command instead of my shell" and entered "byobu" in the "custom command" box.

This works better for me because byobu would only run for me at prompt if elevated (using sudo).

I'm still getting grey screen though and menu doesn't appear when I press F9....if any one has any ideas. Reinstalling didn't work and installing byobu-extras didn't help (and what does "subsumed" mean in synaptic against the extras ?)

---

### Post by sisyphus1978 on 2009-12-28
You must've done something wrong. Byobu runs excellently on my 9.10 system. Things to check: is screen working? byobu-config?

Oh and my byobu doesn't need to be run as root, so maybe that's something to check too. GL

---

### Post by gibbylinks on 2009-12-28
> **sisyphus1978 said:**
> You must've done something wrong. Byobu runs excellently on my 9.10 system. Things to check: is screen working? byobu-config?

Oh and my byobu doesn't need to be run as root, so maybe that's something to check too. GL

Ok going into noob mode.... :)

What can I do to

[LIST]
[*]Check screen working ? Nothing seems untoward, compiz working OK.
[*]What can I look at regarding needing to run as root ?
[/LIST]
This is a fresh install of 9.10 not an upgrade. I've not knowingly tweaked anything.

:P

---

### Post by jnew93 on 2009-12-28
Alright, here's something for you to do to see if this is byobu's fault. When you are logged in, press cntrl+alt+F1 to switch to a terminal login. Login and you will be presented with a command prompt or a running instance of byobu. If it is a running instance of byobu exit it with the "exit" command. Then once you are at a basic command prompt type this:

```
byobu-config
```

This should bring up the config screen without having to press F9. Tell me if that works? Seems to work for me. I think your problem could be conflicting keybindings with some other program. Oh, and to switch back to your other session, press cntrl+alt+F7.

---

### Post by spiky001 on 2009-12-28
ok just been reading thread have installed 10 04 had byobu in apps list till i updated? it  has now gone, type it in terminal nothing appears? also what is it used for sorry for iggnorance. Check on packages sayes i have it

---

### Post by gibbylinks on 2009-12-29
> **gibbylinks said:**
> Update.

Thanks to jnew93 I've got this working now.

All I've done different is instead of ticking "Run Command as a Login Shell" I've ticked 
"Run a custom command instead of my shell" and entered "byobu" in the "custom command" box.

This works better for me because byobu would only run for me at prompt if elevated (using sudo).

I'm still getting grey screen though and menu doesn't appear when I press F9....if any one has any ideas. Reinstalling didn't work and installing byobu-extras didn't help (and what does "subsumed" mean in synaptic against the extras ?)

OK live and learn. I've managed to screw my terminal, since reboot if I click on terminal it loads and then disappears....

Please how can I reset terminal profile...:(

---

### Post by jnew93 on 2009-12-29
> **gibbylinks said:**
> OK live and learn. I've managed to screw my terminal, since reboot if I click on terminal it loads and then disappears....

Please how can I reset terminal profile...:(

Easy! :) Well, we'll use a workaround to keep the terminal open so you can fix settings.

First open xterm by hitting alt+f2 and typing xterm, then hit enter.
Then you'll be greeted with a plain-jane terminal, which is NOT gnome-terminal, the one we want to reset. Next, from xterm, enter:

```
gnome-terminal -e top
```

This will open a terminal in the default profile that will run top, a system monitoring application. This is important because top will run until you close it (preventing the window from closing) and you will be able to fix your terminal settings. The "-e" argument you pass tells gnome-terminal to run the command "top" under the default profile, in case you were curious. I found this out by entering "gnome-terminal --help-all" in xterm, which opens the help menu for the terminal. Anyway, this should work!

Cheers!

---

### Post by gibbylinks on 2009-12-29
jnew93 you are obviously a guru !!

Thanks a million. Got it working again now. :guitar:

---

### Post by gibbylinks on 2009-12-29
> **jnew93 said:**
> I understand this thread is a few weeks old, but I found this via google search and couldn't resist the urge to help anyone else who finds this thread. Here is the solution: simply run 

```
byobu
```in your terminal for it to start.

If you then wish to have it run every time you open terminal, first in byobu's menu (press f9) turn start on login to yes. Second, in the terminal you have open, navigate to Edit>>Profile Preferences>>Title and Command. Then tick "Run Command as a Login Shell". This will enable Byobu to start when you launch gnome-terminal. :)

Cheers!

Ok back to this. I've noticed I get the following when I type in byobu at the prompt

"Cannot make directory '/var/run/screen': Permission denied" 

Could this be related to not being able to run without sudo, and the F9 key not working.

Thanks

---

### Post by jnew93 on 2009-12-29
> **gibbylinks said:**
> Ok back to this. I've noticed I get the following when I type in byobu at the prompt

"Cannot make directory '/var/run/screen': Permission denied" 

Could this be related to not being able to run without sudo, and the F9 key not working.

Thanks

Ok, so I was halfway through a lengthy post trying to manually solve the problem, which is simply a permissions error, when I stumbled upon a script that you can run that will fix it for you (supposedly). So first, try this in your terminal:

```
sudo /etc/init.d/screen-cleanup start
```

Tell me if this works! It _should_ create a new screen directory in /var/run with the right permissions and group ownership. So run it, then try to open byobu.

I'll check back to see if things have worked out!

---

### Post by gibbylinks on 2009-12-30
You know when you wish you hadn't started something !!! :P

Well on the plus side...the script works...but....

When I subsequently type byobu it launches but has all the processes listed. Looks like it's running the ps -ef command, and you can't type anything.

Also I'm having to run the script after every re-boot. It looks like the directory is having it's permissions reset on boot up.

I will understand fully if you wave your hands up in the air, and say....sorry can't help.

My advice... run away run away :)

---

### Post by jnew93 on 2009-12-30
Haha when is giving up in the spirit of Linux!? I'll give you a few more pointers and we'll see if it fixes it. If not, then we tried. :)

In response to launching byobu and being greeted with running processes, and you can't get out of it: the shortcut in terminal for killing the current process is CNTRL+C. Type that and whatever is running will be killed. Then type CLEAR and hit enter and you should be at a clean byobu prompt. (Most likely the process running is called TOP).

In response to the script having to be run at startup, I'm not sure why this is the case :-k, but here's a quick and dirty fix, add that command I gave you to your startup programs. 

System>>Administration>>Startup Programs, then click add, and type Screen Fix under name, and the code to clean the screen file under command. Add a comment about fixing byobu if you wish. This will run that command at startup automatically!

And as far as driving me crazy, just think of this as a test of my knowledge, I'm up for it.

---

### Post by gibbylinks on 2009-12-30
Hi

ctrl+c gets rid of top, but also drops terminal out of byobu, leaving me at the prompt.

I await your response oh fountain of knowledge....:)

---

### Post by jnew93 on 2009-12-30
Hahah I know much less than so many people here. If you're back at the prompt, you can always run byobu again, if you have put the screen fix script in your startup applications , and it has run, everything should run smoothly, as long as you follow the instructions wayyy back in my first post. Hope this fixes everything once and for all!

EDIT: I've attached a picture of my terminal profile, so you can see how I've got it working.

---

### Post by gibbylinks on 2009-12-30
I can't seem to stop byobu from running that program.

I'll try uninstalling it, rebooting and re-installing, see how we go then

It's a challenge

---

### Post by jnew93 on 2009-12-30
Sounds good. After you uninstall, do a search of your filesystem for any files byobu might leave behind, like config files. If you still have top running, type "q" to quit top, it's as simple as that. Forgot that when I made my last post. :P

---

### Post by gibbylinks on 2009-12-30
Foiled, still runs that TOP program and q quits byobu leaving me at the prompt

---

### Post by jnew93 on 2009-12-30
Argh, I'm out of ideas haha. Have you tried to run:

```
byobu-config
```

in your terminal? That should bring up the config screen and you can tweak settings. Also when you uninstalled, did you use:

```
sudo apt-get purge byobu
```

or "remove". You want to use purge. I'm sorry that I can't be of more assistance. :(

---

### Post by gibbylinks on 2009-12-30
Aha....

byobu-config then drop down to "manage default windows" move down to the "screen -t top top" option, press space bar to deselect then tab to apply.

Then when you run byobu, bob's your aunty......:lolflag:

---

### Post by jnew93 on 2009-12-30
No way! So is that a thread solved? Finally haha. \\:D/

---

