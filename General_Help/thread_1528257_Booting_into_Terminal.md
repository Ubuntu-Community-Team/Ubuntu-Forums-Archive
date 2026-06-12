---
title: "Booting into Terminal"
date: 2010-07-10
forum: General Help
---

### Post by Hman242 on 2010-07-10
Ubuntu has spontaneously decided to start booting into a black and white terminal. [I took a screenshot of what it looks like.]("http://img687.imageshack.us/img687/1654/pict0042z.jpg") I have no idea what could have caused this and therefore have no idea how to fix this. Please help.

---

### Post by iponeverything on 2010-07-10
If you can get to a terminal with Ctrl-F2

login do a "sudo -i"

What we want to do is kill off the existing X session and restart it form the command line so that we see the errors.

Kill of the existing session:

```
sudo killall gdm
```

restart with:

```
startx
```

Then go back to the terminal with Ctrl-F2 and note what you see on the screen.

---

### Post by Hman242 on 2010-07-10
Sorry, but I can't copy and paste my result from the Terminal and I don't have anything to wright with, so I'll describe what the outputs to the best of my ability.

It said something like, process "gdm" not found.

---

### Post by rogerdg on 2010-07-10
Did you type
     startx
after typing
     killall gdm

gdm not found means the graphics manager is not running.  Try starting it with "startx" to see what the results are.  This may indicate why the graphics manager is not starting.

---

### Post by Hman242 on 2010-07-11
Here was what the command "startx" gave.

```
Fatal Server Error:
Sever is already running for display 0.
          If this sever is no longer running, remove **/tmp/.X0-lock** and start again.
```

---

### Post by WorMzy on 2010-07-11
X is already running xterm (for some bizarre reason), press Ctrl+Alt+F1 to switch to a tty/virtual terminal, login and run:
```
sudo pkill xterm
```
followed by
```
sudo /etc/init.d/gdm start
```

Once you've done that, you should be presented with the login window. I'm not sure what file has been changed to cause this behaviour, but I'll have a look and see if I can find anything. In the meantime, try running 'gksu gedit' and looking at the list of recently opened files.

---

### Post by Hman242 on 2010-07-11
I do know I deleted some hidden folders in my Home directory, but as far as I know I only deleted ones that were used by some old apps I don't have anymore. Maybe that will help. I will post the output in a few minutes, switching from Windows to Ubuntu on the same computer is a pain.

---

### Post by Hman242 on 2010-07-11
Alright, "sudo /etc/init.d/gdm start" gave me this.

```
Rather than invoking init.d scripts, use the service(8) utility,
e.g. service gdm start

Since the script has been converted to an upstart job, you may want to 
use service(8) utility, e.g. start gdm
```

---

### Post by WorMzy on 2010-07-11
Try 'sudo service gdm start' instead then.


The only files in your home directory which may make a difference would be ~/.xprofile and ~/.Xclients; and possibly ~/.Xsession. If you have any of these files, posting their content here may help to figure out what's happening.

---

### Post by Hman242 on 2010-07-11
I did try to run "sudo service gdm start", but it gave me a paragraph worth of an error. I'll go run it again, but It will take awhile. I'm using small notepads to write what the results are.

---

### Post by WorMzy on 2010-07-11
If your network is working once you've booted Ubuntu, switch to the virtual terminal as you have been doing and install w3m (sudo apt-get install w3m), it's a terminal based internet client. Switch to a second virtual terminal (e.g. Alt+F2), login, and run 'w3m [http://ubuntuforums.org](http://ubuntuforums.org)', login to the forums and relay any errors you get in the first virtual terminal. You can switch between them at any time with Alt+F1/2. It'll save you having to make notes and reboot every five minutes. :)

---

### Post by Hman242 on 2010-07-11
This time instead of giving me an error, it said the job was already running. I'm still having my problem though, expect instead of having a black background behind the Terminal it's the default Ubuntu background.

---

### Post by WorMzy on 2010-07-11
Try ```
sudo killall gdm
``` followed by ```
gnome-session
```

---

### Post by Hman242 on 2010-07-11
When I try to run "sudo killall gdm" is said that he process gdm was not found. Using the command "gnome-session" brings up just about everything, but it doesn't bring up any panel. I'm currently typing from Ubuntu so this should be alot easier.

---

### Post by WorMzy on 2010-07-11
So it won't let you start gdm because it's already running, but it won't let you kill gdm because it's not running? Colour me confused.

Instead of trying to recover, let's focus on trying to prevent the problem in the first place. Can you post the output of
```
ls ~/.x*
```

---

### Post by Hman242 on 2010-07-11
I would but I believe that the "gnome-session' command is still running and give output(slowly).

---

### Post by WorMzy on 2010-07-11
If that virtual terminal is locked up you can just use another Alt+F1-6 are all virtual terminals.

---

### Post by Hman242 on 2010-07-11
The only one of those that gave any result was Alt+F4. It closed out my current window and continued pressed let me back to square one. I'm back at having the session up but still no panel.

---

### Post by WorMzy on 2010-07-11
Sorry, I thought you were already in a virtual terminal. If you're not in a virtual terminal then you need to append Ctrl to the start of that statement (e.g. Ctrl+Alt+F1 = virtual terminal 1)

---

### Post by Hman242 on 2010-07-11
Is there a way to return to my gnome session from the virtual terminal?

---

### Post by WorMzy on 2010-07-11
Yeah, Alt+F7 (or possibly F8 ) should bring you back to it.

---

### Post by Hman242 on 2010-07-11
It was Alt+F8

Here is the output.
```
/home/hunter/.xsessions-errors  /home/hunter/.xsessions-errors.old

/home/hunter/.xine:
catalog:cache
```

---

### Post by WorMzy on 2010-07-11
Okay, and what about

```
ls ~/.X*
```

---

### Post by Hman242 on 2010-07-11
No such file or directory.

---

### Post by WorMzy on 2010-07-11
Okay, you seem to be missing .Xauthority but that's the only difference between my output any yours, and I doubt that that is causing this behaviour.

Can you try logging out of gnome-session and see if it presents you with the gdm login screen? (I'm guessing that it won't, but if it does, you should be able to check your default session there)

---

### Post by Hman242 on 2010-07-11
It does, but I don't seem to be able to see anything involving my session 0.o

---

### Post by WorMzy on 2010-07-11
Okay, and what is the default option set to? Is it xterm? If so, switch it to GNOME and re-login. Hopefully that setting will persist after you next reboot.

Edit: Oh. The session controller should be along the bottom, next to Universal Access tools and Language settings. If it's not there, then there's not much you can do there.

I'm not sure what else to suggest.

---

### Post by Hman242 on 2010-07-11
Yeah, it's not down there.

I was thinking about just reinstalling the OS, I have already backed up all my files. Reinstalling isn't that big of a problem, I just wish I knew what made my system spontaneously do this.

---

### Post by WorMzy on 2010-07-11
Sorry we couldn't figure this one out. :(

Hopefully the info about virtual terminals and w3m will help you out in the future though. :)

---

### Post by Hman242 on 2010-07-11
I'm sure it will. Thanks for trying though, even if we couldn't find the solution. Ubuntu is easily customizable so I've almost got my computer exactly the way I had it before.

---

