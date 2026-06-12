---
title: "Firefox 3.5 won't start on 9.10"
date: 2009-10-29
forum: General Help
---

### Post by Butterknife on 2009-10-29
I just did a fresh install of Koala after being incredibly satisfied by 9.04. However, this proved to be a great disappointment for this one reason - Firefox 3.5 will NOT start no matter what! I've been using this browser on a daily basis for 9 years now and cannot imagine using anything else unless, like in this case, I can't help it.
I removed it through Synaptic, downloaded a fresh package from Firefox web, tried to install that instead, but for some reason, the terminal isn't reporting anything at all, whenever I try to do anything in it, like untar/install. Usually there used to be lines of detail after untar process but this time - nothing. So I don't know if any of it is even successful.
I'm considering going back to Jackalope but not if I don't have to, if I can get Firefox to work.

If anyone at all can help me out, please do! I'm going nuts here by now, having spent a good portion of my evening wasting time on trying to get things to work on 9.10 and failing.

(Bear in mind, simple talk will help - I am a beginner)

---

### Post by andrewabc on 2009-10-29
Open up terminal
applications->accessories->terminal

Type in firefox-3.5 (or maybe firefox) and see what errors are there.

right click on your firefox icon to see what the launch comand is (firefox-3.5 I think).

Maybe it has
firefox-3.5 %u  which my Jaunty has. Try getting rid of the %u or anything other than firefox-3.5

---

### Post by meinvateristnein on 2009-10-29
it is probably set to start using a terminal (prolly set by you by accident) go into configuration editor g-conf-editor and search firefox then through the results you should find one that has a key saying Terminal and a check box, uncheck it and your good to go if that doesnt work then try downloading a older verison and get back to me

---

### Post by Butterknife on 2009-10-30
@andrewabc: Tried entering any of those into terminal, and it's saying absolutely nothing at all. After clicking enter, there is nothing but my profile name@my computer. It makes me think terminal doesn't even work the way it should, in addition to not being able to make install through terminal for any tar I download. So I don't know what the errors with Firefox are. When I right clicked the icon, just as you said - there was %u appended to "firefox". I removed that, but now I don't even get the "Starting Firefox" dialogue.
Sorry if this sounds a bit confusing. I'm confused myself.

@meinvateristnein: Sorry, I couldn't read your entire reply because page coding for any website is screwed in Konqueror. The box for terminal was the first thing I checked and I tried it with both checked and unchecked - doesn't work either way. Tried downloading Firefox 3.0, it came as a tar, managed to use terminal to untar it, but make install commands don't work at all, so nothing installed.

---

### Post by Barafu Albino Cheetah on 2009-10-30
Try installing firefox **from repository** again. 
Try moving somewhere away your /home/user/.mozilla folder.
Konqueror shows this page flawlessly for most people.

---

### Post by Butterknife on 2009-10-30
@Barafu Albino Cheetah: It may show the page flawlessly for most people, but no website is displayed correctly for me.
If you mean installing Firefox from the package manager, I tried that at least 10 times since the installation last night, to no avail.

---

### Post by phillw on 2009-10-30
::GULP::

try ....

```
gksudo firefox
```

Be careful, I only want to see if it loads !!!

Phill.

---

### Post by Butterknife on 2009-10-30
@phillw: It loaded! A million thanks! Now, do I have to do that every time I want to use Firefox or is there a workaround? Also, any idea why make install commands do nothing in terminal?

EDIT: Hang on - I opted for the encryption of the home folder during installation, could this be the source of Firefox issue? And if so, can I remove the encryption and how?

---

### Post by dentharg on 2009-10-30
> **Butterknife said:**
> @phillw: It loaded! A million thanks! Now, do I have to do that every time I want to use Firefox or is there a workaround? Also, any idea why make install commands do nothing in terminal?

EDIT: Hang on - I opted for the encryption of the home folder during installation, could this be the source of Firefox issue? And if so, can I remove the encryption and how?

Try starting profile manager 

```
firefox -ProfileManager
```

and create fresh profile.

Otherwise you can purge firefox installation

```
sudo aptitude purge firefox-3.5
```

and reinstall it again.

EDIT: Don't know about encryption.

---

### Post by phillw on 2009-10-30
> **Butterknife said:**
> @phillw: It loaded! A million thanks! Now, do I have to do that every time I want to use Firefox or is there a workaround? Also, any idea why make install commands do nothing in terminal?

EDIT: Hang on - I opted for the encryption of the home folder during installation, could this be the source of Firefox issue? And if so, can I remove the encryption and how?

Re: getting rid of the encryption - I'd say do it.

Running firefox as sudo is NOT good. But, it points to Firefox not having access (permissions) to a critical part that it needs.

Post what you have found out to here .....

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

and what you have done, etc.

Lovinglinux is logged on, so he should be able to guide you from here on in.

Regards,

Phill.

---

### Post by Butterknife on 2009-10-30
@dentharg: Terminal isn't working almost at all, and in this instance nothing happens when I try loading the profile manager like you suggested or even when I try removing Firefox.

@phillw: Thanks, I'll give that a go! Also, any idea on how to remove said encryption?

---

### Post by andrewabc on 2009-10-30
If you need lots of security use encryption. If you used it because it sounded like fun for the extra security get rid of it.

Encryption will slow your computer down.

Look at benchmarks
[Ubuntu 9.10 Home Encryption Performance](http://www.phoronix.com/vr.php?view=14187)

Dunno how to get rid of it. Best and easiest solution is to format and reinstall ubuntu.

Sounds like you recently just formatted, so reinstalling ubuntu should only take 30 minutes since you shouldn't have anything to backup.

---

### Post by wgg on 2009-11-21
I was having this same problem.  Starting firefox always failed, from the command line or from the menu, any there was never any message explaining why.  I tried reinstalling and purging but nothing would work.

So then I decided to manually purge by deleting my ~/.mozilla directory and discovered that it was owned by root.  Not sure how that happened, but I removed it, then reinstalled firefox fresh and it works again.

I know it's been a few weeks since you've posted this, but for you (and anyone else with this problem) hopefully this is the solution.

~ Patrick

PS: I don't have encryption on my home directory

---

### Post by phillw on 2009-11-22
if you use sudo to start FF, it will royally mess up the permissions - you need to use gksudo, this protects the permissions. I've only just read that bit !!!!

Fortunately the spare brain cell that guards over me, kicked in and that is what I would use anyway ;-)

Phill.

---

### Post by obenauer on 2009-11-25
I had the same problem with firefox not starting.  For some reason, the permissions of my ~/.mozilla directory were owned by root and set to 700.  I changed that:

sudo chown -R johno:johno ~/.mozilla
chmod -R 755 ~/.mozilla

Obviously, substitute your own user account where I have "johno:johno".  This solved the problem for me.

---

