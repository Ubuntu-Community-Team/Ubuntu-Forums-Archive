---
title: "Streamtuner"
date: 2010-01-04
forum: General Help
---

### Post by noby2know on 2010-01-04
How is Streamtuner running for you guys?
Mine used to work well, but now it's garbage.
Any suggestions? Im thinking just get rid of what I have or reinstall. What I'm looking for is a good music site too!
Thanks
And yes Im a newby too.

---

### Post by kellemes on 2010-01-04
> **noby2know said:**
> (..) but now it's garbage.

What's up?

Can't help if you don't explain the problem..

---

### Post by bodhi.zazen on 2010-01-04
Streamtuner is running just fine for me.

Streamtuner includes hundreds if not thousands of sites.

What are you looking for ?

---

### Post by quicknick_26 on 2010-01-04
Streamtuner is working fine for me, too. The integration of Streamripper seems to be working as well. The only thing that I've noticed is a lot of empty streams. I thought SHOUTcast used to have larger directories of subgenres (e.g.: metal). One of my favorites (Kinkaardschok) doesn't seem to be available anymore, but that's probably due to the station pulling their material from SHOUTcast. I just listen to it through my web browser from their website. This is merely a minor inconvenience for me, but I certainly have no reason to call Streamtuner "garbage". I'm sure lots of people all over the world contributed to this project and would probably consider anyone calling it "garbage" to be ungrateful for free software.:guitar:

---

### Post by noby2know on 2010-01-08
**Thanks for your input**. Im glad to see its working for others.

Reinstalling did not help, but it did reveal a clue to the problem. Im attaching a screenshot with the error message I got when I tried to tune into a couple different channels. Before, I would tune in and Streamtuner would just vanish.

As for music sites that im interested in, im looking for software similar to limewire or frostwire.

Thanks,

---

### Post by quicknick_26 on 2010-01-17
Do you have audacious installed on your computer? You may need to go in to the preferences and change the program to one that's actually on your computer like mplayer or vlc or whatever you have.

---

### Post by bodhi.zazen on 2010-01-17
that and you may have to use "audacious2" rather then audacious.

---

### Post by spiritech on 2010-01-19
"audacious2" in prefernces-applications-command-...  worked for me. however when i click on local it crashes out and quits on me - any ideas?

---

### Post by spiritech on 2010-01-19
also does anyone know how i can create desktop folder for my streamripper files ?

---

### Post by bodhi.zazen on 2010-01-20
> **spiritech said:**
> "audacious2" in prefernces-applications-command-...  worked for me. however when i click on local it crashes out and quits on me - any ideas?

I got an error message stating I had to set a directory.

Edit -> Preferences 

General tab (on the left)

Enter a path in "Music folder:" (perhaps /home/you/music)

> **spiritech said:**
> also does anyone know how i can create desktop folder for my streamripper files ?

From a terminal mkdir ~/Desktop/streamripper

---

### Post by spiritech on 2010-01-20
> **bodhi.zazen said:**
> I got an error message stating I had to set a directory.

Edit -> Preferences 

General tab (on the left)

Enter a path in "Music folder:" (perhaps /home/you/music)



From a terminal mkdir ~/Desktop/streamripper


thank you!!!

local tab now workimg however when i type command "mkdir ~/desktop/streamripper" in terminal i get this 

 cannot create directory `/home/millennium/desktop/streamripper': No such file or directory

?

i suppose i need to find and rename the streamripper directory first, not sure how though.

where would streamripper store its rips??

your  help is appreciated, am new to ubuntu only had it about 5 days nows. was a bit scepticle at first, however i now think it rocks

---

### Post by spiritech on 2010-01-20
ok forget last post have managed to find recordings in /home/me

---

### Post by bodhi.zazen on 2010-01-20
it is Desktop not desktop, linux is case sensative

---

### Post by spiritech on 2010-01-20
ok have got local tab working, also found recorded music. all good so far.

have tried to get it to store its files in desktop/music/streamripper folder using comand 

x-terminal-emulator -e streamripper %q - d /home/millennium/desktop/music/streamripper -r -q 

in edit-preferences-applications under record a stream 

its still saving it to home/me

please help!

---

### Post by spiritech on 2010-01-20
sorry missed your last post

have fixed to

x-terminal-emulator -e streamripper %q - d /home/millennium/Desktop/music/streamripper -r -q

still saving to

home/me

---

### Post by spiritech on 2010-01-20
not sure if i should start new thread for this?

---

### Post by bodhi.zazen on 2010-01-20
> **spiritech said:**
> not sure if i should start new thread for this?

Probably as your question is no longer about stream tuner.

Your command looks fine, you might try using quotes (otherwise my guess is your options are being passed to xterminal-emulator):

x-terminal-emulator -e "streamripper %q - d /home/millennium/desktop/music/streamripper -r -q"

---

### Post by greenwom on 2010-02-10
Don't want to hijack this but I am also finding this package to be buggy

Shoutcast doesn't load unless I add the legacy ip address to /etc/hosts/

Changing to Audacious2 in the prefered applications isn't working for me. 

when I "tune in"  I get a segmentation fault?

There are some updates needed for this, like the change of commands to audacious2 and proper hashing of shoutcast....  

I've been using Ubuntu since Warty and this has been a real turnoff on my last two laptop installs with 9.10.  I hope this stuff gets Fixed.

---

### Post by AbdRahim on 2010-02-20
I have added a folder in preferences (Karmic) and streamtuner still  shuts down every time I try to play a shoutcast stream. Altered the host file as suggested above also. Streamtuner is now useless on my machines.

---

