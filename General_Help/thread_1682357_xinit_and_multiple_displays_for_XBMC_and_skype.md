---
title: "xinit and multiple displays for XBMC and skype"
date: 2011-02-05
forum: General Help
---

### Post by cnull2 on 2011-02-05
So I am running XBMClive on a Zotac MAG HD-ND01. And I must say that it rocks!!!! I have my remote working, suspend and resume, movies and TV shows on a home NAS,  etc... I love it. [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

So of course I can't leave that alone I want to make it better. I have a usb camera that I hooked up and installed skype. I have it autoanswer to people on my buddies list only. Now I can check in on the family anytime I want. 

This is how it works now. I boot XBMClive and then ctrl-Alt-F2 and login. 
Then I run this command:
xinit /etc/init.d/skype-up -- :7

/etc/init.d/skype contains this script:
#!/bin/bash
echo "user password" | /usr/bin/skype -pipelogin

This runs skype in display 7 allowing XBMC to continue to run in display 1. But it is manual at this point. I want to automate the execution of skype in display 7. 
So I created a script /etc/rc3.d/S30skype-up with the command that I was using manually "xinit /etc/init.d/skype-up -- :7"
This works except that it leaves display 7(skype) up on my TV instead of display 1 XBMC. 

I am not familiar enough with xinit to know if there is some command that I can add to the script to make it automatically return to display 1 or just make skype open silently without changing over to display 7. 

If anyone has any ideas I would really appreciate it!!!

Thank you,
cnull2

---

### Post by cnull2 on 2011-02-05
I found xrandr 
Does anyone know if I can use it to change my primary display in the script?

I am looking at it as a possible solution.

---

