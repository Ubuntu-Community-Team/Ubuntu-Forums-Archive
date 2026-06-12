---
title: "Ubuntu 10.10 different login screen, cannot boot to grub!"
date: 2011-12-06
forum: General Help
---

### Post by deadprez012 on 2011-12-06
My Acer 5520 has been running Ubuntu 10.10 for one month; before it ran 10.04 for a while; before that, Windows Vista.

Before today, never a single problem. I had the laptop with me at work, logged in several times, just fine. Came home, started up, and got a different login screen.

It says "user-laptop" where a username field might go, and asks for a password. I know my password, and have been logging in with it all day. Now, this odd login screen won't accept it; I get "Authentication Failed".

Every alternate attempt at logging in, it SHOWS what I'm inputting to the password field.

Bottom of the screen sometimes has "Language," "Keyboard," and "Session" icons. It always offers Universal Access Options and shows the time.

I restarted and watched for a chance to press escape; a terminal-like screen with a flashing underscore shows for about 30 seconds (ESC, SHIFT do nothing here), then it goes to this login screen.

I have booted from my 10.04 Live disc but cannot access folders in my documents because I am not user 1000 (root).


What is the problem and how do I fix it tonight? I've been working on major projects all day and need to get back to them urgently!

---

### Post by gennatolls on 2011-12-06
I know this isn't a fix for the problem but may allow you access to your files. Can you boot the recovery mode kernel? Or another previous kernel image for that matter?

---

### Post by deadprez012 on 2011-12-06
I don't get any prompt to boot any way other than what it's doing. I read to press ESC at a prompt to access GRUB, but that prompt never appears. It seems like I don't have access to anything but that login screen. Is there a force-open for a terminal?

---

### Post by vijushimpi on 2011-12-06
temp. solution.


from live cd/USB
to get your imp. files
```
sudo cp /your/home/* /a/safe/location
```

to get your already installed packages
```
sudo cp /your/filesystem/var/cache/apt/archives /to/a/safe/location
```

after that in live distro. or in fresh install to install the above packages
```
cd to folder
sudo dpkg -i *.deb
```

---

### Post by deadprez012 on 2011-12-07
(kinda) SOLVED and bump:

Copied all my really valuable files to a flash drive and installed a fresh 10.04. I'd like to know why the system just locked to the log in screen and kicked me out of root priveleges? Particularly, when I'd been using my system all day already with no issues!

---

