---
title: "crash when running VLC"
date: 2010-05-08
forum: General Help
---

### Post by Nr90 on 2010-05-08
Hello everyone,
I've recently posted here about ubuntu crashing on boot (black screen). Some helpful poster helped me and ubuntu now boots and runs great.

However, when I try to watch a .avi movie with VLC I get the black screen again.

I have a dell inspiron 510m laptop and am using i915.modeset=1 to boot.
It has an intel 855 graphic chipset

Any advice?

EDIT: just checked, crashes with regular movie player aswell

---

### Post by dino99 on 2010-05-08
need to install with synaptic:

- ubuntu-restricted-extras
- medibuntu codecs

************[COLOR="Blue"]sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list[/COLOR] *****
****[COLOR="SandyBrown"]sudo apt-get -q update[/COLOR]
****[COLOR="Magenta"]sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring[/COLOR]
****[COLOR="DeepSkyBlue"]sudo apt-get -q update[/COLOR]

---

### Post by Nr90 on 2010-05-08
I installed those (atleast the first one) earlier according to the method described on the ubuntu website.

It appears to me that the problem is the graphic chipset. The black screen shown is the same as the screen it showed before the modeset fix.

---

### Post by Nr90 on 2010-05-08
> **dino99 said:**
> need to install with synaptic:

- ubuntu-restricted-extras
- medibuntu codecs

************[COLOR="Blue"]sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list[/COLOR] *****
****[COLOR="SandyBrown"]sudo apt-get -q update[/COLOR]
****[COLOR="Magenta"]sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring[/COLOR]
****[COLOR="DeepSkyBlue"]sudo apt-get -q update[/COLOR]

I ran those commands and tried again.
No improvement :(

Could it be that by running a video the modeset is changed again?
(I know very little about the technical stuff)

---

### Post by dino99 on 2010-05-08
is there a crash file into /var/crash ?

sudo dpkg --configure -a

remove/purge vlc then reinstall it (with synaptic)

---

### Post by Nr90 on 2010-05-08
> **dino99 said:**
> is there a crash file into /var/crash ?

sudo dpkg --configure -a

remove/purge vlc then reinstall it (with synaptic)

No crash file.

I do not think the problem is with vlc because it crashes with regular movie player aswell. It appears to be a general problem when running a .avi (could be other filetypes aswell, but because this is a fresh install I haven't got any other movies)

---

### Post by Nr90 on 2010-05-08
some more info in how it crashes:
I turn the movie on,
I get about a second of sound
The graphical display is gone and I can see some things about batter y check etc. ok
I get to see the flashing bar in the top left screen
screen goes dead and doesn't respond to any commands (not even things like ctrl+alt+f2 etc.

---

### Post by mc4man on 2010-05-08
Don't know anything about intel graphics so probably no value - plus the crashing seems ominous 

You could try a specifying  different video output and see.

For gstreamer - run this in terminal and switch to 'no xv' in the Output- video tab
```
gstreamer-properties
```

If no good then maybe try sdl - search gtreamer in synaptic - scroll down and you'll see the sdl plug-in. Install, then open MMS again and pick SDL

Basically then same for vlc  - in Tools - preferences - video - output, choose  X11 (and or install the vlc  sdl plugin for SDL

Don't have high hopes though I thought I'd mention

---

### Post by cchi on 2010-05-22
I had exact same problem.  Try Workaround B: Switch to -vesa from this page.  It changes the graphics to crappy quality, but things work.

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by Copperline on 2010-05-22
> **Nr90 said:**
> some more info in how it crashes:
I turn the movie on,
I get about a second of sound
The graphical display is gone and I can see some things about batter y check etc. ok
I get to see the flashing bar in the top left screen
screen goes dead and doesn't respond to any commands (not even things like ctrl+alt+f2 etc.

Hi- this is a hard lockup and it is likely that it's hardware related. Does this issue happen if you do any other graphics-intensive operations other than movies? Could you test it with a game? Could you try booting with a LiveCD and installing VLC and then running your movie or one from the (mounted) hard drive (to see if the problem is related to your installed graphics driver). This could also...possibly...be a temperature issue and the graphics chip is stalling when you use something with a high refresh rate (such as a movie). If you haven't any other movies to try...have a look on Youtube :)

Copperline

---

