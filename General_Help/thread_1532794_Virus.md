---
title: "Virus?"
date: 2010-07-16
forum: General Help
---

### Post by thabstract on 2010-07-16
I tried sending some stuff to the trash can and it says that I can't and ask to delete permanently. I click to do so but nothing happens. Also in the terminal, it just shows up $ instead of all the regular stuff like the comp name and user and all. Anyone know whats up?

---

### Post by thabstract on 2010-07-17
I was looking in disk usage and went to  the file dev>udev>db and it has block:fdo block:loop0 block:loop1 and so on to loop7 then block:ram0 to ram15 then block:sda1 to sda6 and a bunch of other stuff. Is this normal?

---

### Post by thabstract on 2010-07-17
And now my sound doesn't work.

---

### Post by thabstract on 2010-07-17
Nevermind the sound. Wrong output setting. Is there anyone on? WTF.

---

### Post by hansdown on 2010-07-17
Hi thabstract.

What command did you put in the terminal?

---

### Post by thabstract on 2010-07-17
I haven't used it for anything. I just opened the terminal to update and I saw that all that showed up was $ instead of the normal stuff it shows. Are the files I said were in the db normal?

---

### Post by v1ad on 2010-07-17
well do ls and then pwd what does it show or tell u.

---

### Post by bodhi.zazen on 2010-07-17
My guess is you put some things in the trash or deleted some configuration files from your home directory.

.bashrc for one, which is why your prompt is a $

You can enter```
nautilus ~/.local/share/Trash
```And see what you removed. You may be able to restore from there as well. Keep in mind , . (dot) files are hidden, so you may need to show hidden files.

Did you use any other application such as the Janitor or BleachBit ?

---

### Post by thabstract on 2010-07-17
/home/justin

---

### Post by hansdown on 2010-07-17
I forgot to welcome you to the forum, thabstract.

Please do the following in the terminal;

```
sudo apt-get update
```

Please use this, if you wish to do terminal updates.

Or, you can click, system> administration> update manager.

It is safer.

---

### Post by v1ad on 2010-07-17
recently i had an issue where my .bashrc got deleted and the .local

what i did was coppied it from root and then chowned it to my name

first do ls -al and see if you see .local or .bashrc if you do do not do the following steps.

```

sudo cp /root/.bashrc /home/justin

sudo chown justin /home/justin/.bashrc


```

after copping restart shell.

---

### Post by thabstract on 2010-07-17
expunged, files, and info are all that are in the trash that it pulled up. But nothing is in the expunged and files folder. Info has a game i deleted and whats called cautious launcher. When I was trying to open a game I downloaded, it tried to open it with the cautious launcher. Idk where it came from... but I ran the disk janitor and it removed some stuff. I remember Python being some of them.

---

### Post by v1ad on 2010-07-17
never run disk janitor ....

---

### Post by thabstract on 2010-07-17
.local and .bashrc are both in the list.

---

### Post by v1ad on 2010-07-17
oh so your name is missing let me seewhat the issue can be/

---

### Post by thabstract on 2010-07-17
lol I didn't know not to use it :/ I was trying to find an add/delete program but no luck. I don't really know what to look for. I little experience with Ubuntu. I have only had it for a week..  I just follow instructions I research for and get. But this is beyond me...

---

### Post by thabstract on 2010-07-17
It used to show something like justin @ justinpc $ or something like that if im not mistaken.

---

### Post by hansdown on 2010-07-17
> **v1ad said:**
> never run disk janitor ....

Agreed.

And, never remove python.

It will screw your system.

---

### Post by bodhi.zazen on 2010-07-17
Just restore all the files from trash and you should be fine.

Use the Janitor with caution (as you can see).

---

### Post by thabstract on 2010-07-17
In my Other Software in software sources I have cdrom://Ubuntu 10.04 (unchecked)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid (checked) <-------------------|
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid [source code] (checked)      |
Opera Browser (checked)                                                                 |----??same??
[http://ppa.launchpad.net/example/ppa/ubuntu](http://ppa.launchpad.net/example/ppa/ubuntu) lucid (unchecked)         |  both "partner"
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid (unchecked) <----------------|     status
[http://ppa.lauchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.lauchpad.net/ubuntu-wine/ppa/ubuntu) lucid (checked)
[http://deb.playonlinux.com/](http://deb.playonlinux.com/) lucid (checked)

Is something with this bad??

---

### Post by thabstract on 2010-07-17
when I did the command to see what was in the trash bin, nothing was there. just a game I deleted and a program called cautious launcher. What should I do?

---

### Post by thabstract on 2010-07-17
Here is what is in my dev>udev>db file if the image attached. Is that normal?

---

### Post by bodhi.zazen on 2010-07-17
> **thabstract said:**
> when I did the command to see what was in the trash bin, nothing was there. just a game I deleted and a program called cautious launcher. What should I do?

Depends on how much of your system files were deleted. Most of the configuration files in your home directory are not that important.

Try this

```
cp /etc/skel/.bashrc ~/.bashrc
```

Then log off and back on.

See what is working and what is broken. If it is minor we can fix it, if it is major, it may be easier to reinstall.

---

### Post by thabstract on 2010-07-17
> **bodhi.zazen said:**
> Depends on how much of your system files were deleted. Most of the configuration files in your home directory are not that important.

Try this

```
cp /etc/skel/.bashrc ~/.bashrc
```Then log off and back on.

See what is working and what is broken. If it is minor we can fix it, if it is major, it may be easier to reinstall.

I did this but nothing happened :/

---

### Post by thabstract on 2010-07-17
Hello?

---

### Post by bodhi.zazen on 2010-07-17
> **thabstract said:**
> Hello?

Did you log off and back in ?

Open a terminal, do you have the command prompt you expect ?

Is anything broken ?

---

### Post by thabstract on 2010-07-17
smb2 It used to show up justin@justin-pc:/ $ I think, but it's now still just $. I logged off the user and back on, but it started logged in normally. But, I just restarted my comp. and got error probing smb2, and saw something about nvidia or nforce or something.

---

### Post by bodhi.zazen on 2010-07-17
What do you get when you 

```
echo $SHELL
```

Or if you just run bash

```
bash
```

---

### Post by thabstract on 2010-07-17
echo $SHELL brings up the line /bin/sh and bash shows what my line should be justin@Justin-PC:~$ but when I exit it says there is a process running and closing will kill it. I clicked to end it and opened the terminal back up and it went back to just $.

---

### Post by jocko on 2010-07-17
> **thabstract said:**
> echo $SHELL brings up the line /bin/sh and bash shows what my line should be justin@Justin-PC:~$ but when I exit it says there is a process running and closing will kill it. I clicked to end it and opened the terminal back up and it went back to just $.
I think this indicates that the terminal is using dash instead of bash.
Unfortunately I don't know how to change that.
Edit: Seems like you can change it in the "users and groups" manager (System-->Administration-->Users and groups). Select your user, click "Advanced settings", and on the "Advanced" tab, change the shell to /bin/bash (which is the default). Log out and back in.

---

### Post by thabstract on 2010-07-17
Know whats funny? I remember changing that............ I need to learn how to quit making problems. Can you help me with one more thing though. I haven't got an answer for this... In my dev>udev>db file, I have all this and more in it. Does this look normal, since it says block to all that stuff and all?

---

### Post by jocko on 2010-07-17
> **thabstract said:**
> Know whats funny? I remember changing that............ I need to learn how to quit making problems. Can you help me with one more thing though. I haven't got an answer for this... In my dev>udev>db file, I have all this and more in it. Does this look normal, since it says block to all that stuff and all?
Looks perfectly normal to me.

---

### Post by thabstract on 2010-07-17
For real last thing.

In my Other Software in software sources I have cdrom://Ubuntu 10.04  (unchecked)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  lucid (checked) <-------------------|
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  lucid [source code] (checked)
Opera Browser (checked)
[http://ppa.launchpad.net/example/ppa/ubuntu](http://ppa.launchpad.net/example/ppa/ubuntu)  lucid (unchecked)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  lucid (unchecked) <----------------| are these not the same?
[http://ppa.lauchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.lauchpad.net/ubuntu-wine/ppa/ubuntu)  lucid (checked)
[http://deb.playonlinux.com/](http://deb.playonlinux.com/)  lucid (checked)

thats whats all in my Other Software area of the software sources. Is whats unchecked and checked ok to have, like the playonlinux and launchpad. Or cdrom?

---

### Post by thabstract on 2010-07-17
> **jocko said:**
> Looks perfectly normal to me.

Phew... I thought since it said blocked, something was BAD. I've only been using Ubuntu for less than a week. Sorry for being a MAJOR noob :/

---

### Post by jocko on 2010-07-17
> **thabstract said:**
> For real last thing.

In my Other Software in software sources I have cdrom://Ubuntu 10.04  (unchecked)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  lucid (checked) <-------------------|
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  lucid [source code] (checked)
Opera Browser (checked)
[http://ppa.launchpad.net/example/ppa/ubuntu](http://ppa.launchpad.net/example/ppa/ubuntu)  lucid (unchecked)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  lucid (unchecked) <----------------| are these not the same?
[http://ppa.lauchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.lauchpad.net/ubuntu-wine/ppa/ubuntu)  lucid (checked)
[http://deb.playonlinux.com/](http://deb.playonlinux.com/)  lucid (checked)

thats whats all in my Other Software area of the software sources. Is whats unchecked and checked ok to have, like the playonlinux and launchpad. Or cdrom?
Feeling a little bit paranoid?
cdrom is the cd you installed ubuntu from, so obviously if you trust ubuntu/canonical enough to install their os, you should be able to trust the rest of the packages on that cd (but it is usually just annoying to have the cdrom enabled, as apt/synaptic would start asking you to put in the cd whenever you want to install something that can be found on the cd. And with a decent internet connection it's probably faster to get the packages from the online repos instead of from the cd anyway, at least if you include the time it takes to find the cd, insert it, let it spin up, mount the cd, search for and copy the files and so on...).

The two lines with archive.canonical.com are identical, so you can safely remove one (but one is already disabled so it doesn't do anything, removing it would make no difference).

I don't think this one is a real repo (it should have something else instead of "example" in it):
```
[http://ppa.launchpad.net/example/ppa/ubuntu](http://ppa.launchpad.net/example/ppa/ubuntu)   lucid
```
It is safe to remove that line, but since it is already disabled, it doesn't cause you any trouble.
As for the others, it's up to you which ppa's or other third party repos you need and trust. If you use playonlinux it's probably a good idea to keep the repo enabled to make sure you get updates, but if you don't use it you don't need to keep the repo enabled...

---

### Post by thabstract on 2010-07-17
Thanks alot for your help :D I learned a little bit tonight. well im off to bed. I've had enough Ubuntu for a week.. gnight and thanks again.

---

### Post by bodhi.zazen on 2010-07-17
To change your shell, use the command chsh

```
chsh
```

After entering your password, when it asks what shell you would like, enter "/bin/bash" , without quotes.

Then close the terminal and start it again.

My guess is you cleaned a bit too much and most of your problems are minor and easily fixed.

---

