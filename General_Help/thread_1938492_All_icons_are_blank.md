---
title: "All icons are blank"
date: 2012-03-09
forum: General Help
---

### Post by louisgonick on 2012-03-09
I was trying to install some new icons, but ubuntu wouldn't let me. I looked online for any commands that may help me. I was trying to figure out how can I open usr/share/icons as root, and in the process I typed in this command: 
```
sudo rm -r /usr/share/icons/
```

Now most of my icons are blank. I can barely use my computer now. 
Help!

I'm starting to think that I just deleted all my icons.

---

### Post by MSPdwalt on 2012-03-09
Linux Rule #1

Any time you use the rm command make sure you have a backup.  ESPECIALLY if you're using it as root.

You'll need to copy the files back from a live CD, at least that's what I would do.

---

### Post by louisgonick on 2012-03-09
> **MSPdwalt said:**
> Linux Rule #1

Any time you use the rm command make sure you have a backup.  ESPECIALLY if you're using it as root.

You'll need to copy the files back from a live CD, at least that's what I would do.

I guess I just learned the lesson...

---

### Post by louisgonick on 2012-03-09
Update:
Now ubuntu will simply freeze after a few seconds of booting up.

---

### Post by winh8r on 2012-03-09
As suggested by MSPdwalt above, probably best to use a live cd and just copy the directory over into /usr/share.

there is a good quick reference guide for commands here:

[http://www.pixelbeat.org/cmdline.html]("http://www.pixelbeat.org/cmdline.html")

to check exactly what a command does and what options are available just type:

```
man <name-of-command>
```

Hope this helps you.

---

### Post by louisgonick on 2012-03-09
> **winh8r said:**
> As suggested by MSPdwalt above, probably best to use a live cd and just copy the directory over into /usr/share.

there is a good quick reference guide for commands here:

[http://www.pixelbeat.org/cmdline.html]("http://www.pixelbeat.org/cmdline.html")

to check exactly what a command does and what options are available just type:

```
man <name-of-command>
```

Hope this helps you.

I cant even do anything in Ubuntu now, it just freezes as soon as I boot up. Most icons don't even work.

---

### Post by MSPdwalt on 2012-03-09
Yeah,

I just did:

```
ls -aR /usr/share/icons/
```

there is a ton of stuff there.  How long have you been using this machine?  You may just wanna do a full out re-install. Especially if you don't have a recent backup.

---

### Post by louisgonick on 2012-03-09
> **MSPdwalt said:**
> Yeah,

I just did:

```
ls -aR /usr/share/icons/
```

there is a ton of stuff there.  How long have you been using this machine?  You may just wanna do a full out re-install. Especially if you don't have a recent backup.

I have many important files in Ubuntu, is there a way I can recover them? I cant afford losing them. I've been using Linux for almost a year. 

Are you sure there isn't any solution for my problem?

---

### Post by MSPdwalt on 2012-03-09
It's not is there a solution?  It's how much work are you willing to sink into it?

You can boot to a live, copy the contents of the folder from the live cd into the folder on your drive. (this should restore your default stuff)

Then you'll probably need to re-install every package you installed after the first time you booted it into Ubuntu.

Or you boot to a liveCD, copy your important data off, and re-build.

---

### Post by louisgonick on 2012-03-09
> **MSPdwalt said:**
> It's not is there a solution?  It's how much work are you willing to sink into it?

You can boot to a live, copy the contents of the folder from the live cd into the folder on your drive. (this should restore your default stuff)

Then you'll probably need to re-install every package you installed after the first time you booted it into Ubuntu.

Or you boot to a liveCD, copy your important data off, and re-build.

Thanks, I am starting a new thread. 

[http://ubuntuforums.org/showthread.php?p=11752868#post11752868]("http://ubuntuforums.org/showthread.php?p=11752868#post11752868")

---

### Post by MSPdwalt on 2012-03-09
Dude...this isn't a support queue.  You don't like the response don't mess up your machine and depend on the help of others.

1. Download an Ubuntu iso (burn iso to a CD)

2. Boot the computer you just bricked to the LiveCD

3. Plug in some kind of external storage (thumb drive, external hard drive, something that will hold your data that is so precious that you didn't back up, but wanna have a breakdown on the internet about)

4.  The hard drive your bricked install is on should be visible from the liveCD environment, find your data and copy it to your external storage.

5. Install Ubuntu again on your bricked machine.

6. Copy data back.

7. [http://www.crashplan.com/](http://www.crashplan.com/)

---

### Post by louisgonick on 2012-03-09
> **MSPdwalt said:**
> Dude...this isn't a support queue.  You don't like the response don't mess up your machine and depend on the help of others.

1. Download an Ubuntu iso (burn iso to a CD)

2. Boot the computer you just bricked to the LiveCD

3. Plug in some kind of external storage (thumb drive, external hard drive, something that will hold your data that is so precious that you didn't back up, but wanna have a breakdown on the internet about)

4.  The hard drive your bricked install is on should be visible from the liveCD environment, find your data and copy it to your external storage.

5. Install Ubuntu again on your bricked machine.

6. Copy data back.

7. [http://www.crashplan.com/](http://www.crashplan.com/)

I'm downloading ubuntu right now, it must not take too long. 
I just started a new thread because I thought it would be better to begin by stating all of my problems. Thanks for the help.

---

### Post by pqwoerituytrueiwoq on 2012-03-09
[FONT=Courier New]sudo apt-get remove humanity-icon-theme human-icon-theme gnome-icon-theme hicolor-icon-theme
sudo apt-get install humanity-icon-theme human-icon-theme gnome-icon-theme [/FONT][FONT=Courier New]hicolor-icon-theme[/FONT]
that should get the default icons sets back (the ones that are in use by default)

---

