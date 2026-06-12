---
title: "Creating an SSH Tunnel on bootup"
date: 2009-11-04
forum: General Help
---

### Post by jmcatani on 2009-11-04
I recently made the switch to ubuntu for a new PC build, and I am currently trying to get my feet wet in the unix platform. As expected, I've run into a problems that seems easy enough in theory to solve, but I just can't get it to work.  

Since I am behind an NAT, I need to set up a reverse ssh tunnel with my box and an outside server.  I am using the command: ```
ssh -R 19999:localhost:22 username@server
``` I have already set up the public keys so that I do not need to enter a password.  If I open up a terminal and run this command, it works as prescribed.  However, if I close the terminal the connection closes.  Also, I want to be able to run this command on bootup.  I tried to put that command in a .sh file with a shebang line.  I set this .sh file up with executable permissions and added it to my "startup applications" from the ubuntu system menu. Unfortunately, my script will not load properly :cry:

What am I missing?

I am unsure why this post filed as kubuntu, but I am running vanilla ubuntu.

---

### Post by (-NINJ4-) on 2009-11-04
Assuming that you want to run 
```
ssh -R 19999:localhost:22 username@server
```on login, try adding this to the startup applications:
```
screen -Sdm tunnel ssh -R 19999:localhost:22 username@server
```
It starts a screen in daemon mode, so if you want to close the ssh connection, open a terminal and type "screen -r tunnel" to resume the screen, and then type "exit".  If you want to use the connection to run commands, type "screen -r tunnel" and then when you're done using the ssh connection and want it to remain open, do CTRL+A, CTRL-D.

Works for me :)

---

### Post by jmcatani on 2009-11-05
Thanks!  Works perfectly!

---

