---
title: "Please Help (libasound.so.2) Log In Error"
date: 2006-04-17
forum: General Help
---

### Post by cowlikk on 2006-04-17
I have apperently screwed up my libasound.s0.2 file so when i login it logs me out and sais the file doesnt exist or somthing. i am new to linux and would love to get ride of windows. please help me fix this so i can login. i am very unfamiliar with command line so please specify well!! any help is much appreciated!!

---

### Post by prizrak on 2006-04-17
Try the following.
If Ubuntu is your only OS when you start the computer hit ESC key that will bring up the GRUB menu. If you are dual booting the menu should already be there.
Choose the option that has the (Recovery mode)
Once you boot log in with your username and password.
It will be all text just hit <enter> when done typing each one.
Then do this 
```
sudo apt-get remove libasound2
```
It will ask for a password just put in your password
Then
```
sudo apt-get install libasound2
```
That basically will reinstall (or should at least should). Goodluck.

---

### Post by PictureThis on 2006-06-15
I ran into similar problems after trying to update my Realtek ALC650 drivers:

```
error while loading shared libraries:
libasound.so.2: cannot open shared object file: no such file or directory
```

I did apt-get remove libasound2 but that removed a whole bunch of other stuff!! 
In total some 370MB... More harm done? After apt-get install libasound2 it seems it only installed some 3MB. After restarting my computer Ubuntu loads, I'm able to login but I'm stuck with a black screen (from the good old DOS days) and the prompt from the terminal. Now what? 

Why is it that my whole graphical interface is gone after trying to update a sound-driver? OK, something went wrong but why no graphical desktop? It seems sound and graphics could/should work indepently? I would be happy quietly surfing the internet looking for answers to solve my sound problem ;)

---

### Post by Guild220 on 2006-06-28
Did anybody ever find out how to fix this?  I have the exact same problem, and I really, really don't want to totally reinstall Ubuntu.

---

### Post by eoinmadden on 2006-07-19
I was having a similar problem (with skype).
Went into synaptic. Installed ia32-libs-sdl.
Done the trick. :)

---

### Post by sindrejh on 2006-12-14
> **PictureThis said:**
> After restarting my computer Ubuntu loads, I'm able to login but I'm stuck with a black screen (from the good old DOS days) and the prompt from the terminal. Now what? 

Try:
```

sudo apt-get install ubuntu-desktop

```

---

