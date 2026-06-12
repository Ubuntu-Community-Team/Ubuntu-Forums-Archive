---
title: "Questions on virus scanning in Ubuntu"
date: 2010-02-10
forum: General Help
---

### Post by Rytron on 2010-02-10
Hi.
Would I need to scan the (root /) directory with [COLOR="Indigo"]sudo clamtk[/COLOR] or would running [COLOR="Indigo"]clamtk[/COLOR] be sufficient?

Theoretically, if Ubuntu did get a virus; would this virus try to establish itself in / rather than /home?

Also is it correct to presume that to scan the /home directory; running  [COLOR="Indigo"]sudo clamtk[/COLOR] wont do any more than just running [COLOR="Indigo"]clamtk[/COLOR]?

---

### Post by jken146 on 2010-02-10
Don't bother with virus scanning in Linux. Seriously, don't bother.

---

### Post by K7522 on 2010-02-10
Virus scanning in ubuntu is about as needless as planting a palm tree in the arctic. Waste of resources and you get nothing out of it. Linux isn't Windows, and doesn't have the vulnerabilities. Hell, you can go download virii on purpose just to laugh at them if you wanted.

---

### Post by jamesisin on 2010-02-10
If you are scanning your Ubu machine in an effort to protect a connected Windows machine, there is a small motivation.  You'll be better off protecting the Windows machine directly (by installing on it viral protection).

If you are working to protect your Ubu machine from a virus, just be mindful about when you enter your password to install anything.

---

### Post by Kevbert on 2010-02-10
The only viruses you might pick up are presently only Windows viruses which you may get if you run a DOS/Windows emulator such as DosBox or Wine. It will not affect any of the Linux files (and definitely not the root files). Antivirus software is currently irrelevant for Linux (as it will only find DOS/Windows viruses) and will just slow the system down for no gain at all.

---

### Post by jamesisin on 2010-02-10
This is a good read:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

It will give you a fair picture of the current state of malware in Unix environments.

---

### Post by hwttdz on 2010-02-10
And a more in depth description of the items of that list is given here:
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

You'll note that most things boil down to "this does nothing, unless run with sudo/root permissions in which case you're SOL".  Or another way to look at it is the less you give root permissions to the safer you are.  I would feel uneasy giving a virus checker root/sudo permissions because it would be just one more possible vector of infection as well as the virus checker now having the power to demolish your system on its own.  i.e. "this /boot/ folder looks like this windows virus, I'll delete it to disinfect the system", next thing you know your system is gone.

There are also a fair number of "this was a proof of concept virus to show the security hole patched by X.X.XX, published (3 months|2 years) after update was released".  Or so long as you kept your system up to date you were never vulnerable. 

But the biggest threat to a linux box, "rm *" on the home directory (DON'T RUN THIS COMMAND), or some other equally destructive command.  Remember there are no "are you sure"'s on the command line and far fewer in the linux gui than the windows gui.

In sum, to be safe:
1) don't run unknown commands as root
2) keep your system up to date

---

### Post by hwttdz on 2010-02-10
Looking at the list, one of the virusus even has complicated compilation instructions.  I feel like that makes people pretty safe, there are those folks who are like, "I don't want a virus, why would I compile and install that", and those folks who are like "this is a cool program, I should install it, now what's this compile they speak of", neither of whom is at terribly high risk for infection.  (unfortunately documentation is in german only, so I find myself in the "unable to get infected even if I wanted to category", which is marginally humiliating after my prior remark) (also I'd probably have to go back and install an older OS and not update it to even have the possibility anyways, which is too much work just to be able to say "I got a virus!")

Also raises the question, if you can only be infected intentionally is it still a virus?

---

### Post by VinyMac on 2010-02-26
> **K7522 said:**
> Virus scanning in ubuntu is about as needless as planting a palm tree in the arctic. Waste of resources and you get nothing out of it. Linux isn't Windows, and doesn't have the vulnerabilities. Hell, you can go download virii on purpose just to laugh at them if you wanted.

How do you explain that ?

[IMG]http://ubuntuforums.org/picture.php?albumid=1687&pictureid=5672[/IMG]

---

### Post by jamesisin on 2010-02-26
Abject paranoia?

Seriously, that screen shot is utterly meaningless.

What did it find and what are the contents of that finding?

A Windows only virus no doubt.  Not likely to effect any Unix system in a meaningful way.

---

### Post by NefariousNobo on 2010-02-26
You people are falling into the blindness of "Linux doesn't get viruses". If you want to be technical, Linux can get some malware. There isn't much out there, but there are a few viruses and more commonly malicious shell scripts. How many of you sudo and install.sh file from a reputable package distributor? There is potential danger everywhere, and the only way to avoid it is to go through the source code of any package you install and then compile it from source. That being said, I find Linux to be fairly secure (although I use NetBSD primarily) and unlikely to be infected. Just recognize that it can happen. 

Now to actually answer the question:

If you were scanning the root directory, sudo is probably the way to go. I believe you as a regular user would not have write access to most of the more sensitive parts (where a virus might hide...) and that sudo would be necessary to be thorough.

If Ubuntu did get a virus, / is a better hideout that /home. You can reformat /home (if it's a different partition) without losing your OS (in theory*), but lose / and you lose the OS (in theory*). Therefore, a virus would want to hide in /.

Lastly, it is likely that you could scan your home directory safely without sudo. However, using sudo would be better (I know in my NetBSD, ~/.xinitrc is read-only for regular users, and only root can write to it) so if you want to insure you can remove and scan every file, using sudo would be best. That being said, you should probably be able to manage without sudo if it's just your home directory.

Bottom Line: Use sudo if you wish to be certain you get proper results

Sorry for my essay...

*I would like to make it clear that I always install my entire Linux to one partition and have never tested this. Don't quote me on it or anything, and if you can prove me wrong (or back me up) please do. I'm not sure at all what I'm saying here...

---

### Post by jamesisin on 2010-02-27
> **NefariousNobo said:**
> You people are falling into the blindness of "Linux doesn't get viruses".

Have you ever had a virus (or other malware) on a Linux system?  I've worked with Unix systems for over ten years and never seen any system (in business or otherwise) thus infected.  It may be *possible*, but if it is not practical I just don't see your point.

Working with Windows systems is a very different story.  In any given year I will see many Windows systems infected with all manner of malware.  This is par for the course.  And of course Windows malware will have zero effect on Unix systems.

What you say about / being a better location for a virus to hide is valid enough, but you neglect to articulate how a virus is going to get there.  The problem is that this would require an important kind of participation by the user (and not just any user, but a user with root privs).  It is much easier to break a Unix system than it is to infect it.

This hardly qualifies as a kind of blindness.

---

### Post by 3rdalbum on 2010-02-27
> **NefariousNobo said:**
> You people are falling into the blindness of "Linux doesn't get viruses". If you want to be technical, Linux can get some malware. There isn't much out there, but there are a few viruses and more commonly malicious shell scripts.

If there were Linux viruses that you could actually get, there would be some kind of press about them. The old viruses do not work on modern Linux systems.

And anti-virus programs don't pick up malicious shell scripts. Run AVG Free on that Gnome-look screensaver trojan and it'll report nothing out of the ordinary.

---

