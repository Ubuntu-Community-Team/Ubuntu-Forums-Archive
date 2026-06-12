---
title: "Ubuntu wont run installers, in particular Mathematica"
date: 2009-12-07
forum: General Help
---

### Post by OnkelTom on 2009-12-07
Hi guys!


Im still getting used to Ubuntu & I was wondering does anyone have Mathematica on their machine? 

I have the unix copy of mathematica, i mount it, go through to /unix/Installer then click on MathInstaller and it states "unkown file type". Im pretty sure its not corrupt or anything, i opened it up as a text file and it looks like a convincing C+ installer. 

I read somewhere that i have to do an 'sh' mount or something, but going through that process in the terminal just spits out this

bla bla :  sudo sh MathInstaller
*asks for password*
sh:Can't open MathInstaller

I am a bit confused as to why this wont even start, its a legit copy and everything!?

Anyone know what could cause this?? (it may not even be specific to Mathematica but anything that uses this kind of format)

I really like Ubuntu since i had it but Im still not competent at it, so things like this are a real pain and tempt me back to windows a bit! "Nooooo"

---

### Post by gyppo on 2010-06-09
Have you given it permission to run as an executable? chmod +x or <right-click> -> Properties -> Permission -> Allow executing file as program

---

### Post by SlidingHorn on 2010-06-09
I've never used mathematica, but I was able to find a couple simple guides that might be of assistance.  Sorry I couldn't be more helpful:

[How to install Mathematica 6,Linux,Ubuntu.]("http://www.linuxtent.com/?p=83")

[Mathematica Troubleshooting on Linux]("http://reference.wolfram.com/mathematica/tutorial/TroubleshootingOnUnixAndLinux.html")

[Possible alternatives to Mathematica?]("http://ubuntuforums.org/showthread.php?t=489196")

---

