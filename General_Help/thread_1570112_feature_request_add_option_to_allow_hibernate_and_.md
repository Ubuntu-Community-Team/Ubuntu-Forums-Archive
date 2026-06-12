---
title: "feature request: add option to allow hibernate and suppend when loged out"
date: 2010-09-07
forum: General Help
---

### Post by BryanFRitt on 2010-09-07
The other day somebody sat next to me whom I don't feel like entering in my password around, and I wanted to take my computer elsewhere. If I put my computer in my backpack while it's running, my computer will get hot, and the batteries will drain. So I'd like to put my computer in hibernate, or suspend mode, but my computer was already locked, and I couldn't hibernate or suspend without logging in, but I didn't want to enter my password around this guy so I could hibernate or suspend, so I was stuck.

I know there are reasons to keep things the way they are, (like maybe a server environment, etc...) and maybe it should default the way it is now, but I'd like the option to add the ability to hibernate and/or suspend when logged out, at the log in screen and/or a locked screen, without having to use a password. (be sure to still ask for password to use the computer afterwards)

---

### Post by Hobgoblin on 2010-09-07
Doesn't it suspend when you close the lid or did you turn that feature off?

---

### Post by cariboo on 2010-09-07
This really has nothing to do with securiy. Moved to General Help

For feature request try [Brainstorm]("http://brainstorm.ubuntu.com/") or become a member of the [ubuntu-devel]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel") mailing list.

---

### Post by wojox on 2010-09-07
> **Hobgoblin said:**
> Doesn't it suspend when you close the lid or did you turn that feature off?

Yeah, same here mine suspends.

---

### Post by pastalavista on 2010-09-07
On the Gnome desktop, there is a toolbar 'button' at the bottom-right of the log in screen which has the suspend option. I'm not familiar with KDE.

---

### Post by BryanFRitt on 2010-09-07
> **Hobgoblin said:**
> Doesn't it suspend when you close the lid or did you turn that feature off?

Didn't think of that...
Just looked at my [FONT="Courier New"]'System Settings'[/FONT] [FONT="Courier New"]'Power Management'[/FONT], and it's set to [FONT="Courier New"]'Do Nothing'[/FONT] [FONT="Courier New"]'When laptop lid is closed'[/FONT]
I set the option to [FONT="Courier New"]'Do Nothing'[/FONT] so I could close the lid, and think for a few seconds without the display distracting me. There could be an added option of time delay before locking a computer with suspend. (I could imagine there being a security issue that users might not think about, if a time delay before locking option was added to hibernate)

I still think it might be a good idea to add the ability to add hibernate and suspend to the GUI for the log-in and for the unlock screens. Maybe the option to add this should be with each [FONT="Courier New"]'Power Management'[/FONT] [FONT="Courier New"]'Edit Profiles'[/FONT] profile?

Just tied the options [FONT="Courier New"]'Turn Off Screen'[/FONT], and [FONT="Courier New"]'Lock Screen'[/FONT], they both require passwords to start using the computer again, except [FONT="Courier New"]'Turn Off Screen'[/FONT] turns off the display too. What would be the purpose having the option to leave the display on with the laptop lid closed be? (external monitors?) Maybe the current option [FONT="Courier New"]'Turn Off Screen'[/FONT] should be called [FONT="Courier New"]'Turn Off Screen and Lock'[/FONT], and an option that will really is just [FONT="Courier New"]'Turn Off Screen'[/FONT] be added?

p.s.

Question: do batteries charge faster when the computer is on a power saving mode vs a performance mode, if so...
For those who want maximum battery life, with minimal performance loss.
[FONT="Courier New"]'Profile Assignment'[/FONT] [FONT="Courier New"]'When AC Adaptor is plugged in'[/FONT] should replaced with two options, 'When Plugged in and Charging Installed Batteries' (aka batteries not at 100%...) and [FONT="Courier New"]'On AC with Installed Battery(ies) Fully Charged'[/FONT]. If not, maybe saying that batteries would charge at the same speed either way' could be added to the 'help'

---

### Post by Hobgoblin on 2010-09-07
> **BryanFRitt said:**
> 
I still think it might be a good idea to add the ability to add hibernate and suspend to the GUI for the log-in and for the unlock screens. 

Suspend is there on the login screen on mine, I suspect hibernate is missing because I have no swap to hibernate to.

It's not an option on the unlock screen but pressing the switch user button takes me to the login screen which does have it.

This is on Ubuntu 10.04

---

### Post by BryanFRitt on 2010-09-07
> **Hobgoblin said:**
> Suspend is there on the login screen on mine, I suspect hibernate is missing because I have no swap to hibernate to.

It's not an option on the unlock screen but pressing the switch user button takes me to the login screen which does have it.

This is on Ubuntu 10.04

On KUbuntu 10.04 Suspend/Hibernate option isn't on any of those screens(login/unlock/switch user)

I've read somewhere there's a way to hibernate without a swap partition*. I've got my computer set up to hibernate using a swap partition, and haven't tried the way that doesn't require a swap partition.

*I think the required swap partition (or free space for other method) size is AT LEAST the size of RAM. Example: For my system with 4GiB of RAM I've got my swap partition size set to 4GiB+256MiB or approx 4360MiB of swap space.

---

### Post by Hobgoblin on 2010-09-09
> **BryanFRitt said:**
> 
*I think the required swap partition (or free space for other method) size is AT LEAST the size of RAM. Example: For my system with 4GiB of RAM I've got my swap partition size set to 4GiB+256MiB or approx 4360MiB of RAM.

I have 2GB of RAM and an 8GB SSD.  That's why I have no swap or other space set aside to hibernate.  It's a feature I'm happy to live without.

---

### Post by BryanFRitt on 2010-09-17
> **Hobgoblin said:**
> Suspend is there on the login screen on mine, I suspect hibernate is missing because I have no swap to hibernate to.

It's not an option on the unlock screen but pressing the switch user button takes me to the login screen which does have it.

This is on Ubuntu 10.04

Sounds like this issue might be a KDE issue. How can I change this thread from '**[all variants]**' to '**[KUbuntu]**'?

---

