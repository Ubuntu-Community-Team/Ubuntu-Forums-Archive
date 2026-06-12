---
title: "Login Screen does not load (no GDM) after removal of SLiM in Ubuntu x64 10.04 LTS"
date: 2011-06-12
forum: General Help
---

### Post by Meharisian on 2011-06-12
Hope that anyone who encounters this problem after making the fatal decision to install SLiM after which choosing SLiM to manage the login screen over GDM and then later marking SLiM for complete removal (because you decided to go back to GDM anyway) without running the following command before restarting:

**sudo dpkg-reconfigure gdm**

What happens if you don't do this and reboot, Ununtu will not load your login screen - what you need to do is restart and hold shift to go into 'recovery mode' (or when your Grub loads in the case of you having a dual-boot setup with Windows just go to recovery mode directly).

When in recovery mode... go to **root** (NOT netroot, just root, it's probably right at the bottom in the selection menu).

Initially I followed (unsuccessfully) the suggestion on this thread: [http://ubuntuforums.org/showthread.php?t=1499610](http://ubuntuforums.org/showthread.php?t=1499610) 
(linking it here in case my solution doesn't work for someone)

Specifically the advice was (read the rest of the post before trying this! Thanks @ prylux for the information I've pasted below):

> **Re: no login screen in ubuntu lucid**             
                                                                I don't know if these will help you but...

  You could go into recovery mode and see if "xfix" is available and run it
------------------------------------------------------------
You could see if you can set it up to automatically login

Try starting in the recovery mode by holding the shift key during startup.
Choose root not netroot
then:[INDENT]cd /etc/gdm [Enter]
vi custom.conf [Enter]
[/INDENT]then change
"AutomaticLoginenable=false"
to
"AutomaticLoginenable=true"

You do this by doing this:[INDENT]Highlight the "f" in false and press [Shift+C] a "$" should appear at the end of the line "fals$"
Then type "true" and press [ENTER]
Then press [ESC]
Then [dd]
Then hold [Shift] and press [ZZ]
[/INDENT]then reboot the system
------------------------------------------------------------
You could try to go in to recovery mode and choose "root"
and run[INDENT]dpkg-reconfigure xserver-xorg[/INDENT]In my opinion I'd try and auto login first then xfix then run dpkg
                                                                                               __________________This didn't work for me because my screen kept flickering between the recovery-mode selection list (where you can choose from options like netroot and root) and the purple screen saying ubuntu with the dots below, and the screen that it was supposed to be showing me where I was typing commands under 'root') - another tip if trying the method above: even if your screen doesn't show you what you're typing, it's getting typed, some of the time, so just press enter and the command will still run.

After fumbling around trying to do the above unsuccessfully and not wanting to wreck my custom.conf file... I rebooted (without saving my not-sure-if-I-made-any edits to custom.conf) and instead of going into /etc/gdm I did the following:

- got into recovery mode
- selected root
- typed 'gdm' and hit [enter]
- voila! it showed me my login screen... logged into my user account...
- [IMPORTANT!] I then got into terminal and ran the following:

**sudo dpkg-reconfigure gdm **

...now it's working as normal! :)

If there's a more proficient user out there who can suggest other ways to tackle such a problem for us lesser-noobs then please post on this thread. Thanks!

---

### Post by Jose Catre-Vandis on 2011-06-12
You could probably just go into recovery mode, got to the command line and type:
```
dpkg-reconfigure gdm
```
no need to login

---

### Post by EdTheUniqueGeek on 2011-06-15
What's wrong with SLiM? What issues did you have? Why was it a fatal decision for you?

---

### Post by clenceo on 2011-07-04
**[SIZE="3"]Linux Mint 10 (should work with Ubuntu 10.10)[/SIZE]**

I had a bad experience with SLiM. Seemed like a good idea at the time, but if you don't remove completely...you're in for a big headache.

I was stuck in the boot loader. Could not access my login screen.

Boot into Recovery Mode.
Select: failsafeX Run in failsafe graphic mode (use the letter key, type f) do not use arrows or enter key.
use cursor to select "ok" in command box
select: Run Linux Mint in low graphics mode for one session. Click on OK

you will reach your login screen. Login in as normal

Open Terminal, Enter:
sudo dpkg-reconfigure gdm

you will be prompted to select gdm or slim.. select "gdm"

after it completes, restart.

It should restart as normal.

Go to synaptics and uninstall slim

Restart and all should be back to normal

If running Ubuntu Tweak, purge SLiM.
Or in Terminal try:
sudo apt-get remove --purge slim

---

