---
title: "Ubuntu 9.10 new installation - can't login"
date: 2010-04-19
forum: General Help
---

### Post by jbernardis on 2010-04-19
I have a brand new ubuntu 9.10 installation. I booted up the live CD and everything was fine - the system operated normally. I chose install 9.10 and went through the installation procedure with absolutely no problems. The problem comes when I now try to boot from the newly installed HD. I get to the login prompt, and instead of a solid prompt, the display is flickering very rapidly and the keyboard does not respond reliably - I hit keys and see no response except for every once in a while. I am able to struggle through entering my login, since this is echoed, but I have no hope of entering my password since I can't tell which keypresses are accepted. Remember - all this while the screen is flickering very rapidly.
 
I rebooted again from the live CD and all was OK, but then when I booted off of the HD, the same problem recurred. 
 
Any ideas?

---

### Post by klemes on 2010-04-20
It seems an X-related problem with your xserver.Your xserver provides a screen resolution
that your monitor cannot display properly.Although the flickering thing is just not right under any circumstances,assuming it's an LCD monitor.Or is it just a CRT?In any case careful not to destroy your monitor.
Maybe you should try this:
At the initial grub menu choose recovery mode,and when it finishes booting into a text menu choose root console.
At the prompt type :
```
X -configure
```
wait a couple of moments and then test the new X server with 
```
X -config /root/xorg.conf.new
```
If you successfully launch an xserver(ie you get a clean picture and your mouse is able to move the cursor and so on,remember this only a test screen)then you hit Ctrl+Alt+F1 and go back to the terminal.There you type Ctrl-C so you kill the xserver and be able to type again.
Then type :
```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```
If that command is executed and gives you no errors then type reboot and wait to see if you are lucky...:)

---

