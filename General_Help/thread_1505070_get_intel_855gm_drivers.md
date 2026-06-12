---
title: "get intel 855gm drivers"
date: 2010-06-08
forum: General Help
---

### Post by fatereaper on 2010-06-08
hey everyone, i'm a true newb with ubuntu. I've tried to find online how to get my graphics card up and running but all the places i check are way over my head.  I've been a windows guy forever. Basically the graphics work on my laptop but won't do anything 3d right now. This makes me think i'm not using a correct driver. I've got no clue where to dl the from the ubuntu interface or what to do. any help is greatly appreciated. thx so much.

---

### Post by davidmohammed on 2010-06-08
given that you said that you are a newbie - can you just officially confirm the graphics card you have...

in a terminal type

lspci | grep VGA

---

### Post by fatereaper on 2010-06-10
Hey, thanks for the reply.  Here is what the terminal shows me.

evan@evan-laptop:~$ ispci | grep vga
No command 'ispci' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
ispci: command not found
evan@evan-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
evan@evan-laptop:~$ 


again thanks for the help :)

---

### Post by davidmohammed on 2010-06-15
Ok - you need to boot with 

i915.modeset=1

When booting (just after the splash) press shift.  This should display a list of your kernels.  This is called grub.  Immediately press e.
Find the line ending with quiet splash --

add the i915.modeset=1 immediately before quiet splash

i.e.
it should read 
i915.modeset=1 quiet splash --

CTRL +X to boot.

---

### Post by fatereaper on 2010-06-17
thx for the help :)   I'm currently unable to get that screen to pop up.. i've even tried mashing shift. it keeps getting me into the os.  I've seen that screen you're talking about when i first installed ubuntu. i had to do "i915.modeset=0 xforcevesa" but now that im up and running i cant get shift to bring it up. i also tried spamming shift and e.. i'll keep trying.. any tips on the direct timing? thx again!

---

### Post by davidmohammed on 2010-06-20
some people have found that an upgrade doesnt uplift legacy grub to grub2 - you might still have to press escape to display the grub screen...

---

### Post by fatereaper on 2010-07-28
ok, i can get into the command line now.. not sure what i was doing wroing. i enter in the code and i get an error saying its going to run in low graphics mode for one session due to an error with a vesa kernal being used already or something.. i can write it down if it helps. I also installed ubuntu on my dads com.. it had a jittery screen but i found a command line code that fixes it. the 2nd part of my question is that when ever he has to reboot he has to enter the command line everytime to enter the code. is there a way to save changes so that he and i don't have to do that?  Many thanks.. u guys have been very kind and patient with a noob. i thank u all for not flaming :)

---

### Post by davidmohammed on 2010-07-28
what is the "command line" option that you have to enter - and when & how to you enter it?

The error message is needed to diagnose what the fix should be.

possibly from a terminal session - check if you've got a file called 

/etc/X11/xorg.conf

if you have - rename it to something else

i.e.

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.fatereaper

Then reboot.

---

### Post by fatereaper on 2010-07-28
great that did the trick for the graphics.  The only prob now is i have to type it in each time i restart the computer.. is there a way to save it so i don't have to do it again, or am i stuck typing each time?  Minor annoyance i'm quite happy now :)

---

### Post by davidmohammed on 2010-07-28
if you've got a grub boot option that works for you - let everyone know what it is... 

to fix it so that you dont need to enter it each time

sudo nano /etc/default/grub

for the line 
GRUB_CMDLINE_LINUX=""

put your option in between the quotes

e.g. for my PC I use
GRUB_CMDLINE_LINUX="i915.modeset=1 noapic"

save

then run

sudo update-grub

reboot and enjoy.

---

### Post by fatereaper on 2010-07-28
Man i know it doesn't mean much over the net.. but thanks!! it worked and now i don't have to type it in everytime.  The way i got around the vesa error or whatever it was callled was i left out the -- after quiet splash. This is by far the most helpful forum i've ever seen.  consider me solved on this issue :)

---

