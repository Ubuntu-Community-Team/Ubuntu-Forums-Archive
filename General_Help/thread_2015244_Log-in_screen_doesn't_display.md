---
title: "Log-in screen doesn't display"
date: 2012-07-03
forum: General Help
---

### Post by RogerDavis on 2012-07-03
When I hear the drums, I type my password, and it logs me in.  

But the screen is black, I can't make any choices or whatever, I'm working blind!

The display is ok after the log-in.

How do I get the regular log-in screen back?

---

### Post by cipherboy_loc on 2012-07-03
Switch over to a TTY (Ctrl+Alt+F1) and log in. Run the following, write down the response, and post back:

```

status lightdm

```
That will tell you the status of the lightdm service. It should say start/running. If it is, run:
```

restart lightdm

```
And flip back to the graphical display (Ctrl+Alt+F7). 

If it says stop/waiting, then run:
```

sudo start lightdm

```
and flip back to the graphical display (CtrL+Alt+F7).


What graphics card are you using? If you don't know, 
```

lspci | grep VGA

```


Cipherboy

---

### Post by RogerDavis on 2012-07-03
roger@roger-desktop:~$ status lightdm
lightdm start/running, process 1200
roger@roger-desktop:~$ restart lightdm
restart: Rejected send message, 1 matched rules; type="method_call", sender=":1.61" (uid=1000 pid=2582 comm="restart lightdm ") interface="com.ubuntu.Upstart0_6.Job" member="Restart" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
roger@roger-desktop:~$ sudo start lightdm
[sudo] password for roger: 
start: Job is already running: lightdm
roger@roger-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV370 5B60 [Radeon X300 (PCIE)]
roger@roger-desktop:~$ 

Thanks!

---

### Post by cipherboy_loc on 2012-07-03
Whoops, meant:
```

sudo restart lightdm

```

What drivers are you using?


Cipherboy

---

### Post by RogerDavis on 2012-07-03
I'm using whatever drivers Ubuntu automatically loaded, so I don't know.
Thanks!

---

### Post by cipherboy_loc on 2012-07-03
When did this start happening?

---

### Post by RogerDavis on 2012-07-03
Yesterday - long after installation.

Actually, there are more problems.  Now none of the "system trays / bars" appear at all, and I can't task switch except by starting one app or instance on top of another, then backtracking by closing the app on top.  If I minimize it, it just goes into a black hole, can't get back to that one.

You've been responding very quickly, and I appreciate that, so I'll let you know that I'll be out of the house for about an hour or a bit longer.

Thanks!

---

### Post by cipherboy_loc on 2012-07-03
Ideas:

Check for drivers. Most AMD chipsets out there require some sort of additional drivers. I am not sure where to look on the latest 12.04 with unity (I run fluxbox), but there are a [few tutorials out there. ]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

It could just be a faulty installation. Did you check the ISO you downloaded before installing? 

Lastly, try running the following command and post the output. It could just be your system is unable to run Unity.
```

/usr/lib/nux/unity_support_test -p

```

Cipherboy

---

### Post by RogerDavis on 2012-07-03
I have to say it was working ok for at least a month, though the 3D quit working (didn't appear as a choice) about 3 weeks ago, so it seems that the system is capable, just something went sour.

Also, I was using Gnome from the apps section until I got trapped in Unity when I could no longer see the login screen to select which to use.

roger@roger-desktop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV370
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
roger@roger-desktop:~$ 

Thanks!

---

### Post by cipherboy_loc on 2012-07-03
Try re-installing lightdm:
```

sudo apt-get purge lightdm
sudo apt-get install lightdm

```

Edit: make sure you reboot after this.

Cipherboy

---

### Post by RogerDavis on 2012-07-03
The terminal gave me two choices, lightdm and something that started with G (GDM ?) that was already selected.  I went with the GDM (or whatever) since it was selected.  Should I try it again with the lightdm?

Instead of the regular drum roll, it had that and then a dull thump, no display at all.  Then because I got frustrated I hit several Ctl Alt Fcn(whatever) keys too.

I did the above, maybe or maybe not got a log-in screen back permanantly, at least got one this time, but it looks way different from the regular 12.04 one... no choices, etc.  Just user choice, then enter password.

Thanks!

---

### Post by cipherboy_loc on 2012-07-03
Run it again and choose lightdm. You can remove gdm with:

```

apt-get remove gdm

```

I would do this after purging lightdm. 


Cipherboy

---

### Post by RogerDavis on 2012-07-03
New developments - good ones.

Like I said, I got a login screen.  I figured out how to select Gnome, with no effects.  IT WORKS, I can access all menus, etc!!!  For a few days at least, I'm pretty happy.  I can worry about details after the 4th.

I was only trying Unity to see if it worked any better than the Gnome that had some slight glitches, then Unity bombed and stuck me there in a minimal functional state.  You got me out of that!!!

For my education, should I try the purge / install lightdm in a couple of days, or might that screw up the Gnome side of things?

T H A N K S  ! ! !

---

### Post by msammels on 2012-07-03
Nope, you can safely remove, purge and reinstall lightdm without affecting GNOME. LightDM is a login manager... just make sure you have GDM installed... if you need help on setting GDM as the default login manager, just say :)

---

### Post by cipherboy_loc on 2012-07-03
> **msammels said:**
> Nope, you can safely remove, purge and reinstall lightdm without affecting GNOME. LightDM is a login manager... **just make sure you have GDM installed...** if you need help on setting GDM as the default login manager, just say :)

Why do you need GDM installed for LightDM to work? LightDM has no dependencies on GDM. On top of that, you can only use either GDM or LightDM at any given time. You cannot run both at the same time, so it is pointless to have both installed. In other words, choose the one that works the best for you and remove the other.



Cipherboy

---

### Post by msammels on 2012-07-04
Yes I know, but I was saying that if you remove LightDM, then reboot, you'll be left with a terminal. So it's better to remove LightDM, install GDM, then reboot.

---

### Post by RogerDavis on 2012-07-04
Now I'm on the other side of town, using a Windoze machine, but I'm still following this trying to learn and figure out what to do about it later this week.

I see that GDM is the Gnome Login Manager.  I see that LightDm is mostly for Unity?  Anyway, either works for both?  I almost always use Gnome.

What are the advantages to either?  Or is just a matter of appearance?

If I want to set GDM as the default, how do I do that?

Thanks!

---

