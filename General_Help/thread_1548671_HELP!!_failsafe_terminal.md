---
title: "HELP!! failsafe terminal"
date: 2010-08-08
forum: General Help
---

### Post by funkyguy4000 on 2010-08-08
Okay so I have a problem. 
Once I turned my laptop off my force, holding down the power button, because it had frozen and wasn't responding for days.

SO when i did that, I turned it back on, and well I had this huge huge problem, i've made a few threads about it.  So I had to go through a manual FSCK.  

I did all that and I do have the cd, although when I try to boot off of the live cd, it gives me a bunch of buffer errors,  I have a thread or two about that problem too.  So i can't boot off a live cd and fix it through that. 

Now i've gotton to the point where I can get to the login screen, it looks normal and everything but when I log into a normal session it greets me with this

Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.  View details (~/.xsession-errors file)
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
mkdtemp: private socket dir: Permission denied
```


So i have no idea what that all means but i did understand failsafe terminal.  So when I go to the failsafe terminal to try and fix things, I'm completely lost.  I don't know what to type at all. I'm a windows user most of the time.  I believe I am using Ubuntu 9 but i'm not sure.  I am also not the full admin at least to my knowledge, i was not given full rights, although any solution at all would be greatly appreciated!!

Just please help me!!!

---

### Post by chopinhauer on 2010-08-08
> **funkyguy4000 said:**
> 
So i have no idea what that all means but i did understand failsafe terminal.  So when I go to the failsafe terminal to try and fix things, I'm completely lost.  I don't know what to type at all.

The permissions on your /tmp directory are probably wrong. When you are in the terminal type:
```

sudo chown root.root /tmp
sudo chmod 1777 /tmp

```This should reset the permissions to the correct value.

---

### Post by funkyguy4000 on 2010-08-09
nah that didn't do anything.

When I enter the first command into the failsafe terminal it comes up with a sudo password prompt, so when i'm typing it in.  I'm clearly pressing the keys down but nothing on the screen shows up, no asterisks to hide it, not even the actual password shows.  

And then every sudo command after word just, after hitting enter, shows <myname>@silence

I went and tried to log in normally and it's the same error message about 10 seconds as before.

---

### Post by funkyguy4000 on 2010-08-09
OH WAIT nvm,
I thought that the chmod was a chown. 
It works now!! 
THANK YOU!!!!

---

