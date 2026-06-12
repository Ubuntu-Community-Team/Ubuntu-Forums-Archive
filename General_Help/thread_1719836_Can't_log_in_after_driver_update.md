---
title: "Can't log in after driver update"
date: 2011-04-02
forum: General Help
---

### Post by Jinx13 on 2011-04-02
Heyy :) I finally got kubuntu installed and was running great till...
I decided to install a driver :(
The driver to install was graphics card driver.
So I installed rebooted and boom, it's asking for log-in on the black screen.
I try to enter something and it won't let me type anything in :(
Anyone know why it's done this and how I can get past this screen?

Thanks in advance,

Regards,

Jinx13

---

### Post by andrewthomas on 2011-04-02
You need to provide more info:

What graphics card?

What driver did you try to install?

Where did you get the driver?

What instructions were you following (post link) ?

---

### Post by Jinx13 on 2011-04-02
My graphics card is ATI Radeon HD 4670 1GB

I wasn't following any instructions the process was quite automatic.
I don't remember the driver but here's what I did.

I used the onboard driver installation program.
Not sure what it's called being a linux n00b

It's in the settings (i think)

So I ran the program installed with kubuntu and it said "search for available drivers"

A little like windows update lol

It found a driver and I pressed install :( Was as easy as that.

But for some reason now I can't get past the black screen :(

Thanks for your reply,

Regards,

Jinx13

---

### Post by andrewthomas on 2011-04-02
You should be fine with the OSS ati driver.  I have a 3870 and it works great.

When you can't log in, press <CTL>+<ALT>+<F2> to get to a terminal

log-in with username and password then 
```

sudo apt-get purge fglrx
```let it remove the restricted drivers then

```
sudo apt-get update && sudo apt-get upgrade
```to update then 

```
sudo reboot
```

---

### Post by Jinx13 on 2011-04-03
Heyy thanks for your reply :)

I tried what you said <CTRL>+<ALT>+<F2> but nothing happened, I think it's to do with the screen i'm on.

Have attached an image to show. It will let me put in my name but win't let me put in a password at all

Regards,

Jinx13

---

### Post by andrewthomas on 2011-04-04
The screen looks fine to me.  

Did you actually type your password in when prompted?

It does not give you any feedback when typing, just type the password and hit enter.

---

### Post by Jinx13 on 2011-04-04
LOL!!! Your right haha made me chuckle so I finally entered my password and logged in thanks so much for that :)

I entered all the information in you said in post 4 above and as expected my laptop rebooted.
I was asked to log in again (which I did)

But all I get is the screen attached :(
How do I het it back to the blue kubuntu screen which then takes me to my desktop :(

I have given up on linux so many times but this time i'm determined for it not to beat me lol

Regards,

Jinx13

---

### Post by andrewthomas on 2011-04-05
According to that screen you are on tty2 for some reason. 

Your kdm should be running on tty7 or tty8, try to <CTL>+<ALT>+<F7 or F8> to see if it is there.  

I have no idea why you would be getting dropped to tty2.  

You could also try to log-in and type

```
startx
``` and then reinstall kdm and kubuntu-desktop from synaptic or in the terminal
```

sudo apt-get update && sudo apt-get install kdm kubuntu-desktop
```

---

### Post by Jinx13 on 2011-04-05
Right ok lol i've decied i'm gonna re-install kubuntu then try install that driver noting everything I can.

I tried everything you said with no luck :(
I even of my own back tried
```
sudo apt-get remove kdm kubuntu-desktop
```Then
```
sudo apt-get update && sudo apt-get install kdm kubuntu-desktop
```Which gave more promising results as pressing <CTRL>+<ALT>+<TAB> Put me onto the kubuntu loading screen nothing happened after that though just stuck lol

As I have no idea atm what tty2/7/8 is/does then gonna cut my losses and try re-install lol.

Want to thank you lots for using your time and helping me as much as you have done I have learnt a lot about "sudo" command believe it or not lol And was even brave enough to try a different command I didn't even know existed haha

Thanks again I will be back with my driver details after I installed kubuntu :)

Regards,

Jinx13

---

### Post by Jinx13 on 2011-04-05
Sorry for double post but wanted to keep it seperate :)

Here is the image of the driver screen after re-install of kubuntu 10.10

I want to press activate but i'm gonna be back to square 1 with the tty2 thing again and black screen

Regards,

JInx13

---

### Post by andrewthomas on 2011-04-06
Why do you want to activate the proprietary drivers?

The open-source radeon driver works just fine.

---

### Post by Jinx13 on 2011-04-07
How do I install the open-source radeon driver?
And you happen to have a link?

---

### Post by andrewthomas on 2011-04-08
> **Jinx13 said:**
> How do I install the open-source radeon driver?
And you happen to have a link?
[http://packages.ubuntu.com/maverick/xserver-xorg-video-radeon](http://packages.ubuntu.com/maverick/xserver-xorg-video-radeon)

It is in the repos and you probably already have it installed.

---

### Post by Jinx13 on 2011-04-08
LOL yeah I have thanks for all your help :D

Regards,

JInx13

---

