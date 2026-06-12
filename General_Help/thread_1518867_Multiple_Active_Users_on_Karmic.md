---
title: "Multiple Active Users on Karmic"
date: 2010-06-27
forum: General Help
---

### Post by Underdosed on 2010-06-27
I've read this is all but impossible with pretty much any kind of system, I want to split remote access to a single computer among separate users who would be utilizing multimedia content and web browsing under different accounts.

If the above is not possible, what if I had USB zip drive OS's plugged into that single computer, could I do anything with that?

Be creative please.

---

### Post by dragos240 on 2010-06-27
Remote access? You may be able to get VNC working if you want multiple users remotely.

EDIT: But first, note that setting up VNC may be tedious, you will also have to port forward.

---

### Post by Underdosed on 2010-06-27
I think that "may" part is kind of funny.

I have a new set of flat panel televisions that I'm looking to set up, I want to connect them to a pvr system which will be individualized while having them share the artwork folder where I have an enormous amount of stills and pretty images.

I will need some I/O cabling and crap which I have covered for the most part.

I will need to know how to create different user areas for the different rooms.

---

### Post by dragos240 on 2010-06-27
> **Underdosed said:**
> I think that "may" part is kind of funny.

I have a new set of flat panel televisions that I'm looking to set up, I want to connect them to a pvr system which will be individualized while having them share the artwork folder where I have an enormous amount of stills and pretty images.

I will need some I/O cabling and crap which I have covered for the most part.

I will need to know how to create different user areas for the different rooms.

Sounds like you're creating a media center, if not, what are you trying to accomplish?

---

### Post by Underdosed on 2010-06-27
What we're accomplishing is theres no boxes per se, theres the cabling and the hub.

---

### Post by dragos240 on 2010-06-27
> **Underdosed said:**
> What we're accomplishing is theres no boxes per se, theres the cabling and the hub.
I'm sorry, but you're not telling me the overall goal of what you want to do. I'm asking you this because there are certain setups, and applications to do different things.

---

### Post by Underdosed on 2010-06-27
The goal is for each of the flat panels to use the hub itself instead of each needing its own box. So you have remotes, IR receivers, HDMI cables and some type of software configuration thats going to allow that to happen (hopefully).

---

### Post by dragos240 on 2010-06-27
> **Underdosed said:**
> The goal is for each of the flat panels to use the hub itself instead of each needing its own box. So you have remotes, IR receivers, HDMI cables and some type of software configuration thats going to allow that to happen (hopefully).

Ah I see, you want to output multiple things onto different monitors with 1 box and a hub. Alright, thanks for clearing that up. For what you want, it looks like a media center to me, you can get the same user to display many things on different monitors. Can you tell me how you're setting up your hub? Are you just plugging the VGA cable directly into the hub? If you could tell me/show me your setup, that would help me help you help us all.

---

### Post by Underdosed on 2010-06-27
I apologize, I am setting up five flat *screen* televisions. These are meant to communicate with the hub through USB IR Receivers and HDMI Cables. Whatever is going on software side is what would be going on if it were just an additional pvr frontend. This includes personal settings, web browsing and multimedia functions.

---

### Post by dragos240 on 2010-06-27
> **Underdosed said:**
> I apologize, I am setting up five flat *screen* televisions. These are meant to communicate with the hub through USB IR Receivers and HDMI Cables. Whatever is going on software side is what would be going on if it were just an additional pvr frontend. This includes personal settings, web browsing and multimedia functions.
I see what you're trying to do now. What you're suggesting is possible, but not feasible. If you want 5 users at once, running daily applications, each user is going to experience slowdown to compensate, you will need a very powerful box if you want to do this. However you might also want to try a light desktop environment or window manager for each, it will use less ram, and less CPU power. As for the setup itself, I'm not exactly sure how to do it, but it seems possible.

---

### Post by Underdosed on 2010-06-27
Guess a little, you will do better than me I think.

Edit:
Two of the rooms are for children and they really won't be doing much with it, the third is for guests. The other two would see general use.

---

### Post by dragos240 on 2010-06-27
> **Underdosed said:**
> Guess a little, you will do better than me I think.


I have 1 idea. You can have multiple X sessions, but you will need to set them up manually, you should be able to use something like grandr to set up each session to a monitor. In theory, that'll work. If you need help doing this, I can help.

---

### Post by Underdosed on 2010-06-27
What can you do specifically?

---

### Post by dragos240 on 2010-06-27
> **Underdosed said:**
> What can you do specifically?

Wait about 30 mins, I have to go right now, but I'll tell you a bit later.

---

### Post by dragos240 on 2010-06-27
Sorry. I'm back. You know how to startx right? Alright, for this, you need to have a dedicated machine, but I'm sure you know that already. Try to start multiple X sessions. Kill everything Xorg and GDM. First, we can continue from there. Again, Sorry I'm late.

---

### Post by Underdosed on 2010-06-27
It tells me I'm not authorized to the run the X Server and that its aborting.

What is "everything Xorg and GDM"?

---

### Post by dragos240 on 2010-06-27
> **Underdosed said:**
> It tells me I'm not authorized to the run the X Server and that its aborting.

What is "everything Xorg and GDM"?

Okay. Do this in a terminal:
```
killall Xorg && killall X
```

It will complain about X or Xorg not existing, this is normal. It should go into the login screen, press ctrl + alt + F1.

Now
```
sudo service gdm stop.
```
Okay, now login to the terminal with your username and password. Now, type in this:
```
echo "gnome-session" > .xinitrc
startx
```

---

### Post by Underdosed on 2010-06-27
Xorg(1134): Operation not permitted
Xorg: no process found

It didn't go into the login screen.

---

### Post by dragos240 on 2010-06-27
> **Underdosed said:**
> Xorg(1134): Operation not permitted
Xorg: no process found

It didn't go into the login screen.

Okay, in that case logout. Just logout, and do what I said earlier, do Ctrl+alt+F1, and then follow the rest. If you have any other issues, just post.

---

### Post by Underdosed on 2010-06-27
I followed the instructions.

It said

Xauthi creating new authority file
Xauthi creating new authority file

Fatal server error:
Server is all ready active for display 0
if this server is no longer running, remove /tmp/.xo-lock and start again.

---

### Post by dragos240 on 2010-06-27
> **Underdosed said:**
> I followed the instructions.

It said

Xauthi creating new authority file
Xauthi creating new authority file

Fatal server error:
Server is all ready active for display 0
if this server is no longer running, remove /tmp/.xo-lock and start again.

GDM seems to be running. Did you do sudo service gdm stop? If so, try sudo killall gdm.

---

### Post by Underdosed on 2010-06-29
Sorry for the delay, had to go to work, said:

gdm.: no process found

---

### Post by Underdosed on 2010-07-07
Followed directions
blueooth something or another failed and so did four other things, don't know if its normal or not, it said migration complete, did startx and screen went blank.

---

