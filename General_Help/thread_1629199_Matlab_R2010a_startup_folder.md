---
title: "Matlab R2010a startup folder"
date: 2010-11-23
forum: General Help
---

### Post by M.D.G. on 2010-11-23
Hi all,

I cannot figure out how to change the startup folder for MATLAB.  The userpath is defined as /home/username/Documents/MATLAB but upon starting MATLAB I start in /home/username. I have tried searching around but have been unable to figure out how to change this.  Any help (preferably detailed since I'm fairly new to Linux) would be much appreciated.

P.s. Matlab is installed in /etc/matlab

---

### Post by Flying_Pigeon on 2011-04-30
Hey

I don't know if you are still having problems with this but I was recently and non of the ways i found online worked properly for me.

In the end I just wrote a start up file so matlab would change directory when it starts.

Create a file called startup.m in /home/username.

Put the command "cd /home/username/Documents/MATLAB" in that file.

Hope this helps.

---

