---
title: "GUI not working!"
date: 2010-11-21
forum: General Help
---

### Post by smeelkin on 2010-11-21
So I was playing around with themes and stuff like that. Then I was moving a panel up where I already had one. Then the computer froze (I had been playing around for quite awhile). As a usual windows user, i forced a shutdown (that was probably my mistake). 

Now, after logging in, nothing works. The terminal works just fine, but the actual GUI is not working. Windows won't open, there's a small panel-bar that kinda jumps a little in position. Any idea's the problem?

---

### Post by Verbeck on 2010-11-21
could you give a screen-shot?

---

### Post by matt_symes on 2010-11-21
Hi

> i forced a shutdown (that was probably my mistake)Yes, not a good idea. Try the magic key combination to shutdown.

Press and hold 

Alt SysRq

Keep pressing the 2 keys above and then type the keys

r  e  i  s  u  b

one after another. This is _busier_ backwards. This should close Ubuntu gracefully assuming the kernel has not crashed or something else has not happened. Try it with both Alt keys as one should work.

Kind regards

---

### Post by sikander3786 on 2010-11-21
Try these commands,

```
sudo service gdm start
```

If it says it is already running, try

```
sudo service gdm restart
```

What does it report?

Also try to fix any broken packages/dependencies (if any)

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

Which graphics card is it? And were any proprietary drivers installed?

Which version of Ubuntu?

---

### Post by smeelkin on 2010-11-21
> **Verbeck said:**
> could you give a screen-shot?

that depends... first time i couldnt get in, im not sure i can this time

EDIT: i mean, i can log in, it changes the cursor to the one I've chosen, but then it stops (it still heats quite up though)

---

### Post by smeelkin on 2010-11-21
> **matt_symes said:**
> Hi

Yes, not a good idea. Try the magic key combination to shutdown.

Press and hold 

Alt SysRq

Keep pressing the 2 keys above and then type the keys

r  e  i  s  u  b

one after another. This is _busier_ backwards. This should close Ubuntu gracefully assuming the kernel has not crashed or something else has not happened. Try it with both Alt keys as one should work.

Kind regards

thanks! that will probably prevent many problems in the future! :D

---

### Post by smeelkin on 2010-11-21
> **sikander3786 said:**
> Try these commands,

```
sudo service gdm start
```

If it says it is already running, try

```
sudo service gdm restart
```

What does it report?

Also try to fix any broken packages/dependencies (if any)

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

Which graphics card is it? And were any proprietary drivers installed?

Which version of Ubuntu?

tried the first one, nothing happened, and the second, im not connected to the internet yet. how to do that in a terminal?

plus, my graphics card is gma 3150

---

### Post by sikander3786 on 2010-11-21
You don't need to be connected to the internet yet. Carry on with those commands.

And you didn't mention which version of Ubuntu is it?

---

### Post by smeelkin on 2010-11-21
ubuntu 10.10 desktop

---

### Post by smeelkin on 2010-11-21
> **sikander3786 said:**
> You don't need to be connected to the internet yet. Carry on with those commands.

And you didn't mention which version of Ubuntu is it?

ok, so nothing really happened, it just said 0 to all in sudo apt-get install -f

and the next one just went smoothly

i think im going to add a new user adn try there
how should i do that properly in a terminal? im still pretty new to ubuntu :)

---

### Post by sikander3786 on 2010-11-21
In my opinion, you don't need to add a new user. However if you want to, here are the instructions.

[https://help.ubuntu.com/community/AddUsersHowto#Command-line](https://help.ubuntu.com/community/AddUsersHowto#Command-line)

Instead of that, try to reconfigure your graphics.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot

```
sudo shutdown -r now
```

---

### Post by smeelkin on 2010-11-21
still the same...

---

### Post by smeelkin on 2010-11-21
ok, so now i got a new user, and everything works fine there
the problem is with my own user.

---

### Post by sikander3786 on 2010-11-21
Can you plese post the output of

```
sudo service gdm stop
```

```
sudo service gdm start
```

**[COLOR="Red"]Edit:[/COLOR]** How was the problem related to your user, I can't figure that out :-)

Glad you got it working.

---

### Post by matt_symes on 2010-11-21
Hi

You could look at the gnome settings in your home folder. Maybe, they have become corrupted. 

It is a hidden folder. 

~/.gnome2

You could try renaming it, so you still have the old settings. There are other hidden folders in there are well that might be causing the issue.

Type, at the command line,

ls -al 

to see them all

Kind regards

---

### Post by smeelkin on 2010-11-21
> **matt_symes said:**
> Hi

You could look at the gnome settings in your home folder. Maybe, they have become corrupted. 

It is a hidden folder. 

~/.gnome2

You could try renaming it, so you still have the old settings. There are other hidden folders in there are well that might be causing the issue.

Type, at the command line,

ls -al 

to see them all

Kind regards

exactly the problem.  i now removed the .gnome2 and .gconf, and now my user works. Thanks alot for the help.

---

### Post by matt_symes on 2010-11-21
Hi

Glad its fixed :) Please mark the thread as solved for other people to search against.

Kind regards

---

