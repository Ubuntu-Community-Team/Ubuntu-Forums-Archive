---
title: "Cannot resolve &quot;Login Loop&quot;"
date: 2010-05-12
forum: General Help
---

### Post by Ambidextrous on 2010-05-12
I am unable to log in graphically.  When I enter my user name and password, the screen blanks briefly, then returns me to the same screen, with the same log in prompt.

If I enter an incorrect password I get an "Authentication Error"

Here's what I've tried so far:

Ctrl/Alt/F1 and log in on TTY1
```
sudo pkill gdm
startx

```I get a fatal error:  X-Server is running.  I tried 
```
sudo rm /tmp/.X0-lock
```which didn't help.

I read in another thread that ~.Xauthority and ~.ICEauthority could cause the problem, so I deleted both.  No change.  In the same thread the original poster reported that he had solved the problem by creating a new user and that ~.profile had been the problem.  I'd rather not duplicate all the customization I've done so I renamed .profiles to ~.profile_old and tried again.

This time I got a black screen with a mouse cursor.  Not really the solution I'd been hoping for.

I used nano to examine ~.profile_old.  I found no smoking gun, so I renamed it back to ~.profile and tried again.  I'm back where I started in the "Login Loop"  :(

I welcome your input.

---

### Post by Ambidextrous on 2010-05-15
It's very disheartening to receive no response, especially when this seems to be a known problem.

---

### Post by iponeverything on 2010-05-15
> **Ambidextrous said:**
> It's very disheartening to receive no response, especially when this seems to be a known problem.

Don't take it like that, its just the shear volume of messages. Lots of things get lost in the shuffle, its not just you ;)

open a vtty with ctrl-alt-F2 and log in. Then run

```

sudo -i 
cd /var/log
tail -vF messages syslog debug Xorg.0.log dmesg > /tmp/log-messages

```

Then switch back to gdm with ctrl-alt-F7 and try to log a couple of times. Go back, kill off the tail and look at the contents of /tmp/log-messages

---

### Post by lykwydchykyn on 2010-05-15
Log in at the terminal and try "df -h".  Sometimes if the disk is full this happens.

Also check permissions on your home directory.

Also check ~/.xsession-errors for clues.

I know other things can cause it too, but those are the things I've personally encountered.

---

### Post by Ambidextrous on 2010-05-15
Too late.  I followed some advice in another thread:

```
sudo apt-get purge nvidia-*
```after which nothing worked... not even recovery mode.  I just finished re-installing Lucid.  I didn't reformat, so most of my config files survived.

I left a reply in the other thread describing the effect purging the nvidia display drivers had...perhaps I can save someone else from re-installation.

Thank you for making the effort.

---

### Post by lavinog on 2010-05-15
You could try and make a second profile just for testing.  .profile might not be the only issue, but it would be tough to find out unless you try.
EDIT: Didn't refresh to see the new posts.

---

