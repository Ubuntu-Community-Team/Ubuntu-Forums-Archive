---
title: "Start up problem"
date: 2010-05-05
forum: General Help
---

### Post by Gallienus215 on 2010-05-05
Hello all I'm new to ubuntu, although I've been playing around with linux since Caldera Desktop.

A few weeks ago I installed Ubuntu 10.4 beta on a pc. I upgraded it to 10.4 RC and 10.4 final release. I think it was after upgrading to 10.4RC that I started having a problem during startup. Here is what happens:

I turn the pc on the bootstrap process occurres, then the grub screen comes up I let ubuntu boot. For a few seconds I get a black screen with a blinking cursor. The Ubuntu splash screen flashes on the screen for maybe a second or two. Then I'm dumped to the command prompt on TTY1.

At this point I can log in with a username and password type startx and I'm at the ubuntu desktop. If I log off I'm back at the command prompt on TTY1.

If I press alt-ctrl-F7 at the command prompt this is what I see, these are the last four lines of text:

init: ureadahead-other main process (742) terminated with status 4

*Starting apparmor profiles Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
[OK]
*Setting sensor limit                                                     [OK]
[COLOR=Red]*[COLOR=Black]Speech-dispatcher configured for user sessions
SSL tunnel disabled, see /etc/defaults/stunnel 4
*Starting Common Unix Printing System: cupsd              [OK]

Then a blinking cursor.

I'm not really sure what the problem is. Has anyone seen this before? Thanks in advance for any help.


[/COLOR][/COLOR]

---

### Post by migs73 on 2010-05-05
I was having a very similar problem on booting into Karmic.
Would stop at TTY and request login. If I left it it would eventually boot up after coming up with *Stopping Firestarter Firewall
*Restarting NMBD

and other stuff.

If I logged in at the TTY prompt, and did startx then I could get in but after a minute or so I would get jumped back to the graphical login screen. If I then logged in from there I would just get a blank screen.
Unlike you, I have had no problems since going to Lucid (also RC and then upgrade to final). I would link you to my thread, but nobody had anything to say about the boot problem, and I have marked it as solved now.
One thing you could look at is your log file viewer, it logs what occurs during boot and may highlight where the boot stops.
System > Admin > Log File Viewer
Maybe somebody will know what to do with the info, but not me!!! I am still a bit of a noob.

---

### Post by Gallienus215 on 2010-05-13
bump....I'm still having this problem....anyone have any ideas?

---

### Post by anglican on 2010-05-14
> **Gallienus215 said:**
> bump....I'm still having this problem....anyone have any ideas?
Sounds like a problem with gdm (you don't mention kubuntu etc... so I'll assume it's gdm). What happens if instead of startx you try running gdm (sudo gdm-binary)? If gdm fails to start you could try reconfiguring it (sudo dpkg-reconfigure gdm).

H

---

### Post by switchlives on 2010-05-27
I have the same problem. I am running karmic and on startup i press alt+f1 and it just says stopping firestarter firewally and the screen goes blank. I cant get to the CLI to login or do anything before it goes blank. plz halp :(. ive searched all over for a solution and the only thing i come up with is dead ends or solutions that involve logging in.

---

