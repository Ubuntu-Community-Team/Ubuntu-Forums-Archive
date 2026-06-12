---
title: "Problems logging in (again)"
date: 2006-04-12
forum: General Help
---

### Post by silhouette on 2006-04-12
About a month ago I posted a [thread](http://www.ubuntuforums.org/showthread.php?t=140730) explaining how I couldn't log in to GNOME. Well, after having installed Kubuntu I'm having the exact same problem. For those of you too lazy to look :), I'll reiterate what's going down: The login screen pops up, I enter my user name and password, I see the X busy cursor, and I'm right back to the login screen. After encountering this problem in two different DE's, logic would say that the problem is not with `kdm` or `gdm` but with X, no? Having gained a bit more Linux experience by now, I switch to tty1 (Ctrl+Alt+F1) and run `tail -f /var/log/syslog`. Then I restart X (Ctrl+Alt+F7), and try logging in again. After waiting for the failure I switch back to tty1 to see if anything shows up in /var/log/syslog. Sure enough, something does:

> 
kdm_greet[9070]: Internal error: memory corruption detected
...
kdm_greet[9141]: Can't open default user face


So maybe the problem's with `kdm` after all? I try running `apt-get --purge remove kdm`, restarting, then `apt-get install kdm`. No dice.

I decide to reinstall Kubuntu, 'cause that worked last time. **However**, my setup has changed from last time: I've got two hard drives, where / is on the master and /home is on the slave. So I reformat the master and reinstall Linux, and at last I'm met with KDM. In confidence I attempt to log in . . . but I'm kicked back again?! ](*,)

So, :-k my theory is that some file in one of the dot-folders (.kde, .Xauthority... I'm really not sure) in my home folder is corrupted, and KDM is detecting this (hence the line about "memory corruption", whatever 'memory' means) and dying. **SURELY** someone has had this problem before and is willing to take a stab at this? :neutral:

---

### Post by gerbman on 2006-04-12
Hey there. Yes, I had the exact symptoms you're having (being kicked back to the login screen after entering username/password). However - and this is where our situations might differ - I was also getting an error message about the .ICEauthority file in my home directory...something about it not being writable. I'm not sure how this happened, but after chown'ing that file I was able to log in again. So, my first thought it to make sure that all the files have appropriate permissions in your home directory.

---

### Post by alamba on 2006-04-12
Can you do a mem test from grub before booting please and see if it comes up with any abnormalities?

A

---

### Post by silhouette on 2006-04-12
[QUOTE=alamba]Can you do a mem test from grub before booting please and see if it comes up with any abnormalities?[/QUOTE]
Sure. How do you do this exactly?

---

### Post by alamba on 2006-04-12
Press esc during boot when it says booting with grub or something similar...then you'll see a list of kernels to boot of from, the bottom most entry would be for a memory test. Select that.

A

---

### Post by Sef on 2006-04-12
That is a memtest86.  It takes while to do.  You need to let it run about eight to ten times, so it can pick up any errors.  It will keep doing the test.  After letting it run over night, you can check it by pushing F4, I believe and see the results.  Then just stop it.  It will keep on running and running.

memtest86 site:

[http://www.memtest86.com/#philo]("http://www.memtest86.com/#philo")

You can also burn a cd there for the test.

---

### Post by silhouette on 2006-04-12
Sounds good. I'll try that and post an update tomorrow, then.

---

### Post by silhouette on 2006-04-12
Okay, I did a memtest (I ran it for about 9 times) but it didn't come up with any errors. I was going to save the output, but my keyboard mysteriously failed (or so I thought, until I pressed the Escape key, which of course caused a reboot). I can run the test again, though, if you really need the output.
 
FYI, I checked /var/log/syslog again and that error about memory corruption hasn't come up.
 
There's another detail from the last time this happened that I forgot to mention: If I switch to tty1 and make a new user (I did `adduser`; I guess that's the right way) and then switch back to KDM, I can log in to the new account. I just can't log into my account. In response to Gerbman's suggestion, I don't think this isn't a permissions problem -- if you read the thread I linked to, you'll see I tried deleting .Xauthority and .ICEauthority and it didn't seem to do anything. I would still guess something's up with my home directory, though.
 
One more thing: when I checked /var/log/syslog after I logged in to the new account, that error about not finding the "default user face" was still there. So I suppose both those messages in /var/log/syslog (this one and the memory corruption one) are just glitches. -- **EDIT:** Sorry, this is not true. The "default user face" error shows up only when the bad user account fails. Therefore, this must be the error?
 
I guess it's back to looking at log files, then...

---

### Post by silhouette on 2006-04-12
Okay, I just did a Google search for "Can't open default user face" and that led me to [this mailing list e-mail](http://lists.debian.org/debian-kde/2005/09/msg00082.html). Specifically it gives these instructions:

> > I had the same problem, and traced it to the following in
> my .bash_profile (which is now sourced by /etc/kde3/kdm/Xsession):
> 
> if [ -z "$SSH_AGENT_PID" ]; then
>     exec ssh-agent bash --login
> fi
> 
> This was turning my X session into a vanilla bash login shell which was
> exiting immediately (I'm guessing because there was no stdin or
> something, but this is where my knowledge fails me).
> 
> So check your shell's login scripts.

Yup, that was it! I just commented out all my bastard login scripts
and it works now!

"Login scripts"... where might these be found? (And yes, I am using bash.)

---

### Post by silhouette on 2006-07-31
For those of you who have come to this thread via search, this problem has been solved since my last post. I know they say you can install fonts by just copying them to your .fonts folder, but this seems to have been a direct cause of the "Can't open default user face" error that KDM returned. Since then I tried copying my fonts to /usr/local/share/fonts/truetype (which I created), cd'ing to there, running "mkfontscale", "mkfontdir", and "fc-cache", then symlinking to there from .fonts, and this worked without a hitch.

---

