---
title: "numlockx Not Getting Executed At Startup"
date: 2011-12-13
forum: General Help
---

### Post by hypertyper on 2011-12-13
I've installed numlockx, I tried putting 'numlockx on' into startup applications but it doesn't work. 

Which files get executed late in the login process? Is that where I should put it?

I looked here:
[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

but the path must have changed. I'm using Xubuntu 11.10.

Thanks

---

### Post by lechien73 on 2011-12-13
Do you have the /etc/gdm/Init/Default file?

If so, add:

```
numlockx on
```

before the line that says [FONT="Courier New"]exit 0[/FONT]

Use:

```
gkdu gedit /etc/gdm/Init/Default
```

to edit it.

---

### Post by hypertyper on 2011-12-13
Xubuntu uses lightdm (?) so I don't have that path. Looking at etc/lightdm but that doesn't have anything Default-looking.

I did read the link I posted which I think suggested what you did.

If someone can generally tell me in which order things get loaded, which modules, which files/configs, then I'll try and work from there. I don't know where to look for that kind of information.

I've had some peculiar things going on trying to get my dual monitor setup working where files didn't seem to get executed at the usual time or with the usual effect. 

I've added this line "setxkbmap -option terminate:ctrl_alt_bksp" to my .profile but adding numlockx to the same file doesn't do the trick.

Thanks

edit:
This solved the problem for some people:
[https://answers.launchpad.net/lightdm/+question/173666](https://answers.launchpad.net/lightdm/+question/173666)

It seems that on my machine this conf file doesn't work properly. I tried using it to sort out my monitors and the scripts I put there didn't seem to get executed, or at the wrong time... Man I hate it when a solution exists but doesn't work for me. Grrr

---

### Post by lechien73 on 2011-12-13
Was just about to post the same response about the greeter-setup-script=/usr/bin/numlockx line :)

Maybe you might need to restore your configuration files - if that wouldn't mess up your dual monitor setup.

---

### Post by hypertyper on 2011-12-13
I currently have no idea at all why my dual monitor setup is working. I've removed all the files I had created because I wanted to know what made it work when it suddenly did. I've deleted them all and it's still working...

I have absolutely no clue why my machine is doing what it is. It's driving me crazy!

The NumLock light comes on during login, but then goes off. Something must be overriding lightdm...

---

### Post by lechien73 on 2011-12-14
Hmmmm...very strange.

The only suggestion I have left is to Ctrl+Alt+F1 to tty1, and then stop lightdm:

```
sudo stop lightdm
```

Start it again in test mode:

```
sudo start lightdm --test-mode
```

Check the verbose log in /var/log/lightdm to see if there are problems with any of the config files, and which files it's using.

You can get back to the normal lightdm by stopping it and starting it again without any command line switches.

---

### Post by hypertyper on 2011-12-14
Since the numlock light did come on briefly when I put it into startup applications I tried something different:

I created a bash script:
```
#!/bin/bash
sleep 5
numlockx
```

and entered this into session and startup applications:
bash -c ~/numlock

And that is working!

Somewhere in the login process XFCE must mess with things so the sleeping script and whack it from behind so to speak ;)

---

