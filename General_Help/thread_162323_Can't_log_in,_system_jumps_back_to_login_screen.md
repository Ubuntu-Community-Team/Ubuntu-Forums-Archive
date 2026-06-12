---
title: "Can't log in, system jumps back to login screen"
date: 2006-04-18
forum: General Help
---

### Post by iteyoidar on 2006-04-18
My Kubuntu installation worked the last time I used it like a month ago, I tried to log on today though and everything started up normally, but when I log in, it takes my password, sort of flashes the screen with the black and white dots or whatever, and then jumps back to the log-in screen.  It will keep doing this every time I log in.  That is, it takes the correct password, but it won't start anything, it just jumps back to the login screen.

Is there any way I can figure out what is going on or fix this somehow?  I can't imagine what could have caused this, I think I might have changed on of my partition sizes but I doubt this is effecting it since everything else starts up fine.

---

### Post by iteyoidar on 2006-04-18
I'm wondering if I might have messed up some sort of system settings.  I recall I was trying to install the ATI video driver a while back(I forgot what it is called), or maybe when I ran the installation CD again, I messed up some settings.

Is there any way I can fix my installation without erasing everything?  I really don't want to reinstall the whole thing because it took me forever to get everything working properly :( 

Sorry, I can't find an edit button.

---

### Post by uteck on 2006-04-18
I think your .kde file may be corrupted.  Use "Ctrl Alt F1" to get to a text screen and login.  Then back up you .kde file with "mv .kde kde-old"  Then press F7 to get back to the gui and try logging in.

---

### Post by iteyoidar on 2006-04-18
[QUOTE=uteck]I think your .kde file may be corrupted.  Use "Ctrl Alt F1" to get to a text screen and login.  Then back up you .kde file with "mv .kde kde-old"  Then press F7 to get back to the gui and try logging in.[/QUOTE]

Thanks for the suggestion.  I tried it, but it didn't do anything.  I still get the same issue with logging in.

Basically, I put in the proper password, the screen flashes like it's changing the resolution or refresh rate or something, and then it goes to that black and white screen, and then back to the login screen again.  

But since I can log in without the interface, does that mean it's some problem with KDE and not the entire system?  Is there a way I can just reset KDE or something?

---

### Post by iteyoidar on 2006-04-18
Ok, I tried starting up in "recovery mode", I logged in as root, and then entered 'startx", and everything loads up perfectly.  But still not when I try to log in with my normal user account.  What could be going on here?

---

### Post by uteck on 2006-04-19
In recovery mode, look to see if you have a .Xsession file in your home directory.  Since it is a 'dot' file it will be hidden, so you have to look for it by name ('less ~/.Xsession' should try to read the file if it is there.).  If you do have one, rename it and then try loging in.

---

### Post by iteyoidar on 2006-04-19
I didn't seen any files like that.

I also tried creating another user account from root, and then logging on to that one.  It does the same thing.  So basically:

It loads up while in recovery mode
It doesn't work after recovery mode, ever.

Judging by the way it's acting I'd say it's some error involving display settings somewhere(but maybe not), I tried reconfiguring X as well and it didn't change anything.  I wonder if I have some bad program loading up?

---

### Post by fdoving on 2006-04-20
check that your loopback 'lo' interface is brought up during boot: 
/etc/network/interfaces

look for:
```

auto lo

``` 


You can manually bring it up using:
```

sudo ifup lo

```



- Frode

---

### Post by iteyoidar on 2006-04-24
I checked, auto lo is already in that file, if I type it in myself it says, "interface lo is already configured".  :( 

I would just reinstall but I didn't really want to have to reconfigure my video driver and dpi settings and hard drive mount settings and everything again..

Is there some way I can just reinstall KDE?  Maybe that would fix it.

---

### Post by bungfu on 2007-10-12
I'm having the exact same problem except I'm using Gnome and it's nearly a fresh install. it happened after I changed my package to include gnome art and gdesklets so that I could mess with some new look and feel stuff. did you ever find a solution?

the only difference is that I'm usually able to login on the 3rd try. it also says something about my battery on the first attempt even if my laptop is plugged in. are you running a laptop as well?

---

