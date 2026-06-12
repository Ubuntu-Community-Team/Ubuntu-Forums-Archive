---
title: "Desktop is frozen, other apps working, but sloowww"
date: 2011-12-25
forum: General Help
---

### Post by aronstandley on 2011-12-25
Hey,

My desktop is not responding to any prompts by the mouse. I've tried restarting the computer, and that works slightly - the reaction time is still majorly slow after a reboot.

Other apps work fine, but their speed is incredibly slow now, compared to what this computer has been doing.

I just recently went through the steps here to clean up my computer to try to get it to speed up:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

How can I unfreeze the desktop, and speed up my computer's processing power?

Ubuntu release - latest
Computer - Asus Eee 1005HA

---

### Post by jerrrys on 2011-12-26
Deborphan is a good package when used correctly.  Unfortunately I suspect that you have been guessing and have removed necessary packages.

   GUESSING
       --guess-*
       --no-guess-*
              deborphan can try to guess what packages may not be of much  use
              to  you  by  examining the package's name and/or description. It
              will pretend the package is in the main/libs section, and report
              it  as if it were a library. This method is in no way perfect or
              even reliable, so beware when using this! It is also possible to
              tell  deborphan  e.g.  to guess all interpreters but not Perl by
              using --guess-interpreters --no-guess-perl or to guess  all  but
              not  Mono by using --guess-all --no-guess-mono. Please note that
              the --no-guess- option must occur after the --guess-  option  it
              modifies,  this makes it possible to declare more complex things
              like to guess all, except interpreters but additionally  try  to
              guess perl.

For more info, open a terminal and enter **man** **deborphan**

things to try:

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

---

### Post by saneearth on 2011-12-26
You may also be having some hardware issues. Ubuntu and other Linux distros are not nearly as susceptible to "junk" slowing the system down as a windows machine. Sounds like you may be having hardware issues of for some reason your configuration has gotten messed up, either video and/or compiz.

---

### Post by meditatingfrog on 2011-12-26
> **aronstandley said:**
> Hey,

My desktop is not responding to any prompts by the mouse. I've tried restarting the computer, and that works slightly - the reaction time is still majorly slow after a reboot.

Other apps work fine, but their speed is incredibly slow now, compared to what this computer has been doing.

I just recently went through the steps here to clean up my computer to try to get it to speed up:
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

How can I unfreeze the desktop, and speed up my computer's processing power?

Ubuntu release - latest
Computer - Asus Eee 1005HA

Have you tried running ```
top
``` to see what is eating cpu cycles?

---

### Post by aronstandley on 2011-12-28
jerrrys: Your ideas make sense, since the timing of this with the timing of running deborphan seem aligned. I tried running your suggested commands, but no changes took place on the command line.

saneearth: It seems possible, but unlikely - nothing in my hardware has changed, by damage or by repair work. Why would the desktop be so specifically affected?
If it is hardware, what would be a way to check without paying for a tech to run diagnostics? 
The machine is an Asus Eee netbook, so taking it in would be about as much as buying a new one...

meditatingfrog: I ran the command, but I'm not sure what to look for. My browser (Chrome) occasionally ran high - almost 40% - but no other app or function seemed to be much out of place (to my inexperienced eyes anyway).
Any clarifications or distinctions that would narrow this command down into useful next steps?


Thanks for everyone's suggestions so far. I can't wait until this is solved, and I'm grateful for your time and energy in making that happen.

---

### Post by jerrrys on 2011-12-29
And it didn't spit out any errors?  Too bad...

Try reinstalling lightdm:

sudo apt-get remove lightdm && sudo apt-get install lightdm

also could try

sudo apt-get remove xserver-xorg && sudo apt-get install xserver-xorg

and I think its better to do this in tty mode (its another terminal like gnome terminal).

**Ctrl Alt F6** will open a tty session. 

After running the commands, enter:

sudo reboot

good luck

---

### Post by aronstandley on 2012-01-15
> **jerrrys said:**
> 
Try reinstalling lightdm:
sudo apt-get remove lightdm && sudo apt-get install lightdm
also could try
sudo apt-get remove xserver-xorg && sudo apt-get install xserver-xorg


jerrrys: Thanks for this, this seems to have helped quite a bit.

Everything seems have gone back go regular functionality, until now - whenever I go to the dashboard, the mouse freezes up again.
It's like somebody put a transparent image over the functioning desktop - the desktop works, and restart windows show up on the desktop, but the dashboard sits over it.
The dashboard responds to key prompts and searches for apps, etc; but no mouse functionality until a restart resets the computer.

Any ideas?

---

