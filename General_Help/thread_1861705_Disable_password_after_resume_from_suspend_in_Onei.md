---
title: "Disable password after resume from suspend in Oneiric"
date: 2011-10-15
forum: General Help
---

### Post by aysiu on 2011-10-15
In past versions of Ubuntu, to disable a password prompt when resuming from suspend, I could just go into *gconf-editor* and then go to Apps > Gnome-Power-Manager > Lock and then uncheck the appropriate box.

With Ubuntu 11.10 (Oneiric Ocelot), I can't do that any more.

*gconf-editor* isn't installed by default, but even after you install it, that option isn't there. And I checked all the options in System Settings, and I can't find how to disable the password prompt (no, the screensaver one is not the same thing).

If you think you have a solution for this, please let me know.

To reproduce: close the lid and wait for the computer to suspend-to-RAM (a.k.a. sleep). Open the lid to wake up the computer. Notice that you're prompted for your password.

If the solution to the problem exists: open the lid and notice there is no password prompt.

Appears to be a bug report on this already:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/871560](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/871560)

---

### Post by drs305 on 2011-10-16
I believe I've figured this one out.

The setting is now in dconf: org.gnome.desktop.lockdown

Either install dconf-tools and run dconf-editor to manually set it, or run this command:
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```

Note: can also be run as root.

---

### Post by Gitominoti on 2011-10-16
If you click the Dash Home button on the left hand side and type in lock, go to the icon that just says, "Screen". Uncheck "Lock" and you should be good

---

### Post by drs305 on 2011-10-16
> **Gitominoti said:**
> If you click the Dash Home button on the left hand side and type in lock, go to the icon that just says, "Screen". Uncheck "Lock" and you should be good

That wasn't working as of a few days ago for resuming from suspend - at least for me. It worked for the screensaver though...

---

### Post by Gitominoti on 2011-10-16
> **drs305 said:**
> That wasn't working as of a few days ago for resuming from suspend - at least for me. It worked for the screensaver though...
Well, it worked for me

---

### Post by drs305 on 2011-10-16
> **Gitominoti said:**
> Well, it worked for me

I've no doubt, and hopefully for most other users as well. :-)

I should probably note that if the lockdown is disabled with the command I used, it 'locks' the 'screen' options via the Dash Screen setting you describe and no changes can be made to the options appearing on that System Settings page.

---

### Post by ProntoAnthony on 2011-10-16
> **drs305 said:**
> I believe I've figured this one out.

The setting is now in dconf: org.gnome.desktop.lockdown

Either install dconf-tools and run dconf-editor to manually set it, or run this command:
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```

Note: can also be run as root.

Outstanding!

Thanks for posting that one. It annoys me to have to type in the password after waking the PC from sleep mode.

---

### Post by Gen2ly on 2011-10-16
> **drs305 said:**
> I believe I've figured this one out.

The setting is now in dconf: org.gnome.desktop.lockdown

Either install dconf-tools and run dconf-editor to manually set it, or run this command:
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```

Note: can also be run as root.

Well done, works for me as well. Thank you.

---

### Post by aysiu on 2011-10-16
> **drs305 said:**
> I believe I've figured this one out.

The setting is now in dconf: org.gnome.desktop.lockdown

Either install dconf-tools and run dconf-editor to manually set it, or run this command:
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```

Note: can also be run as root. Thanks! How did you figure that out?

---

### Post by drs305 on 2011-10-16
> **aysiu said:**
> Thanks! How did you figure that out?

Brute force!  

I've figured out a lot of the dconf settings over the past six months. dconf-editor isn't nearly as user-friendly as gconf-editor is/was. I haven't figured out if that was by design or unintentional.

What I really find disappointing is dconf-editor doesn't have a decent search feature.

Anyway, I just went through every setting in dconf-editor, starting with the likely sections. Fortunately there aren't a tremendous number of entries as yet.

I'll attach the list of the gsettings commands I've figured out. I have them in a post-installation script to automatically input some of my preferences. It will take me a few minutes as I'll try to add some comments (if they aren't self-explanatory) as to what they do before I attach it.

---

### Post by aysiu on 2011-10-17
Well, thanks for doing all that digging. I assure you a simple Google search yielded nothing for me.

Kudos!

---

### Post by drs305 on 2011-10-17
> **aysiu said:**
> I assure you a simple Google search yielded nothing for me.


You've now blazed the path for successful future Google searches though!  :guitar:

I've attached the script entries to my previous post.

---

### Post by mc4man on 2011-10-17
The layout of using gsettings seems much simpler & logical to me vs. gconf. Though over the last several months it has grown so much that the schemas list has gotten imposing, seen in

gsettings list-schemas

But the layout of using is quite straightforward
gsettings <command> <schemas> <key> <value>

Man gsettings is quite imformative to get some of the useful commands -
 
gsettings list-recursively <schemas> is very useful as is
gsettings get <schemas> <key> and
gsettings range <schemas> <key>
It all flows pretty nicely after a bit

---

### Post by cRoMo on 2011-10-18
> **drs305 said:**
> 
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```
This will also disable the possibility to manually lock the screen either by using the CTRL-ALT-L shortcut or through the Lock Screen option in "power menu".
Still searching for the solution to be able to only disable the post-resume screen lock.

---

### Post by drs305 on 2011-10-18
> **cRoMo said:**
> This will also disable the possibility to manually lock the screen either by using the CTRL-ALT-L shortcut or through the Lock Screen option in "power menu".
Still searching for the solution to be able to only disable the post-resume screen lock.

This is correct so for those wanting to lock the screen without suspending this is not a viable option. 

As a workaround, I'm sure an enterprising forumite could write a suspend script. It would 'sed' this command to 'true' when a 'suspend' script was activated and then 'sed' it back to 'false' after the system has returned from suspend. Or you could probably more easily incorporate a script to run when the "Lock Screen" option is run, since it wouldn't have to deal with resuming from suspend issues.

It shouldn't be necessary, but it could be done in this manner.

---

### Post by aysiu on 2011-10-18
In the ideal world, you would want the ability to keep those two things separate. Truthfully, it'd be rare to find someone so annoyed by having the screen locked upon resuming from suspend but who would want to lock the screen manually.

---

### Post by drs305 on 2011-10-18
@ cRoMo,
> This will also disable the possibility to manually lock the screen either by using the CTRL-ALT-L shortcut or through the Lock Screen option in "power menu".
Still searching for the solution to be able to only disable the post-resume screen lock. 

Not that you or anyone else was anxiously waiting for this, but...

[LIST]
[*]Blanking the screen is invoked with "gnome-screensaver-command -l"
[*]The command uses the dconf value set in the "disable lock screen" *at the time of execution*
[*]You can enable and use the Compiz Config Settings manager to set a key binding command to a script which will would temporarily change the lock value immediately before the command is invoked, and change it back immediately thereafter. I used CTRL-ALT-. (period)
[*]You will now have the lock on a manually blanked screen invoked by [COLOR="DarkRed"]CTRL ALT [SIZE="3"].[/SIZE][/COLOR] , but no lock for a suspended screen. (As *aysiu* stated, I'm not sure under what circumstances you might desire this action, but here it is.)
[/LIST]

The script to bind:
> #!/bin/bash
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'false'
gnome-screensaver-command -l
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
exit


With that, as Forrest Gump says, "That's all I have to say about that".

Or does, "Stupid is as stupid does" more likely apply to me?...

---

### Post by henriquemaia on 2011-10-26
Another satisfied customer. Thanks a lot.

---

### Post by MuddBuddha on 2011-10-30
Thanks a million!  That was really annoying me.

And yes....I found it through a Google search!  Viola!

---

### Post by powerofpi on 2011-11-29
> **drs305 said:**
> I believe I've figured this one out.

The setting is now in dconf: org.gnome.desktop.lockdown

Either install dconf-tools and run dconf-editor to manually set it, or run this command:
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```

Note: can also be run as root.

Thank you thank you thank you!

---

### Post by peufeu on 2012-03-14
My 70 years old mom has been using linux for years now (she just does internet and mail), and I've installed a Linux Mint 12 on a laptop for her, to replace her old dead PC...

Since she can't remember a damn password, you just enabled the Suspend feature on her laptop ! Isn't that cool ! The planet thanks you.

It seems there is a tendency amongst idiotic UI designers these days to need to change everything that worked perfectly well before. For instance, since the "Shut Down" command is so well hidden in the latest versions, my mom just clicks the switch on the powerbar, which kills the power to the computer. 

But since she's been shutting down the PC like this for about ... a few years ... I guess the fact that it was a hardware failure that killed the PC (dead HDD, not corrupt FS, lol) speaks a lot for the skill of linux kernel and filesystem hackers... not so much for stupid UI designers, though...

---

