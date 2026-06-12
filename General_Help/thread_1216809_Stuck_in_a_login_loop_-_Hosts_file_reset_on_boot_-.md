---
title: "Stuck in a login loop - Hosts file reset on boot - no network access - no sound - hmm"
date: 2009-07-18
forum: General Help
---

### Post by AzT3K on 2009-07-18
So one day I got up and my desktop decided it wasn't going to play fair any more.

I'm running ubuntu / kubuntu 9.04 amd64.

My system was running fine and I'm unsure if it was due to a recent update, or what, I'm guessing that's what happened, but I switched it off and was away for two days. 

When I came back and switched it on again I saw that my usual login in screen - the default kde login now said:

"welcome to localhost.localdomain"
 
rather than:

"welcome to computer-name" 

I tried logging in -> the screen went blank for a couple of seconds like it was going to log in then it just went straight back to the login prompt.  I tried changing the session to gnome, but got the same result.

I tried the console login, I got a prompt that said:

"computer-name login:"

I logged in

once logged in the prompt was:

"user@localhost:~$"

I started GDM with:

sudo gdm

it loaded the gdm login prompt -> the default ubuntu graphical login, I logged in again and it started KDE, I'm presuming this was because I had KDE as my default session.

When it loaded I noticed two things immediately - the system clock was set to the 1st of jan 2005 and I had no network access - also no sound - it seemed as though my hardware drivers hadn't loaded or something.  When i tried to use the network configuration tools it told me I didn't have sufficient privileges.

I thought okay maybe gnome will be different - I restarted the computer and got myself to the graphical gnome login prompt - i changed the session to gnome and logged in - gnome loaded up fine but had exactly the same issues as kde - no sound, no network, but the system did retain the time that i had reset in kde.

I found someone complaining of a similar problem:

[http://ubuntuforums.org/showthread.php?p=7164508](http://ubuntuforums.org/showthread.php?p=7164508)

A solution someone provided was based on the /etc/hosts file:

```

127.0.0.1 computer-name localhost.localdomain localhost
127.0.1.1 computer-name

```

mine looked like this:

```

127.0.0.1 localhost.localdomain localhost
127.0.1.1 computer-name

```

so I changed it to match the example above - however no matter which way i edit the file it gets reset on boot.

I'm thinking that my hardware issues are permission based and are derived having to log in twice to get to a display manager.

This having been said however when loggged into the command prompt i dont have network access either - "sudo apt-get update" yields a series of could not resolve host errors.

Any Ideas???

---

### Post by doas777 on 2009-07-18
try:
```
127.0.0.1 localhost localhost.localdomain
127.0.1.1 computer-name
```

---

### Post by AzT3K on 2009-07-23
Doesn't work hosts file gets reset on boot.

---

### Post by AzT3K on 2009-07-23
So I managed to solve this one, not exactly sure the technical reasons why - however here's what i did:

Booted up as per normal, got:

"welcome to localhost.localdomain"

I accessed the console login option and I got a prompt that said:

"computer-name login:"

I logged in and at the "user@localhost:~$" prompt typed:

```
sudo shutdown now
```

the system displayed a menu with a series of options one of which was called "netroot" - root logged in with network access - I selected that and got a prompt "root@localhost:~$" then ran:

```

apt-get update
apt-get upgrade

```

It updated/upgraded the system. I probably should have restarted at this point to see if it worked, but thought hey lets see if editing the hosts file works now.  So I edited /etc/hosts via:

```
nano /etc/hosts
```

and changed its contents to:

```

127.0.0.1 computer-name localhost localhost.localdomain
127.0.1.1 computer-name

```

I'm unsure if it was because I was accessing the system via netroot or if it was due to the system update or due to using the slightly altered syntax, but I rebooted the system and I got the login box again only this time it said:

"welcome to computer-name"

Hooray!! - so I logged in and worked!! - computer is back to normal - everything works*.  I'm inclined to think that I had a broken package / program before because of the fact that editing the file via sudo should yield the same result as editing it via root, and no changes would stick before - however something I did worked.

*(Well almost, I have an old NF4 FakeRAID controller which has issues with dmraid and jaunty and a TC powercore card which has never worked under ubuntu, but those are kind of less than mainstream components and another story)

---

