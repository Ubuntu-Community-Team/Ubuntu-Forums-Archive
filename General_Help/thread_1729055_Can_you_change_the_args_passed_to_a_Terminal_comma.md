---
title: "Can you change the args passed to a Terminal command while it is running?"
date: 2011-04-14
forum: General Help
---

### Post by mcg.mrk on 2011-04-14
I'm trying to ssh my ubuntu laptop with my android phone.  But with the app I have (connectbot) I don't seem to be able to pass any args to the command.  I want to pass the -Y command to allow my phone access to the screen on my laptop so i can use my laptop (somewhat) from my phone.  Can you change the args passed to the command while it is running? 
(I know i could have gone to an Android forum, but i thought this forum would yield better results)

Thanks

---

### Post by randallecook on 2011-04-14
Are you looking to run a command-line terminal session on your phone where the commands you type on the phone run on your laptop and console output appears on the phone? In other words, do you want to ssh from your phone into your laptop and run command-line programs there (ls, vi, gcc, etc.)?

If so, it looks like connectbot can do this. If you instead want to launch a specific program on your laptop from your phone, then things are different. Most ssh clients can do this, and they of course allow you to pass arguments to the remote program. If they don't, you could instead create a script on your laptop that takes no arguments itself and in turn invokes the program you really want to run, passing it all the arguments it requires.

Good luck.

---

### Post by mcg.mrk on 2011-04-14
I can ssh my laptop fine and can then run simple commands there.  My only problem is I would like to be able to run a program via my phone but have the output displayed to the screen of my laptop.  Like playing a video - I still want it to open on the laptop. The way the app works, I just give it the normal arguments like username@host (I don't get to write the full command myself) but i don't seem to be able to specify my own args (As i understand it -Y would allow me to launch applications to the screen).  Once i ssh my laptop i have a full terminal but it is too late then to write the command again.

thanks for your help!

---

### Post by NFblaze on 2011-04-14
Nope as far as I am aware you cannot send any flags using ConnectBot as far as I am aware. Though once you are logged in via Connectbot SSH at the prompt you may be able to ssh -X user@localhost. Kinda like daisy chaining your ssh

Give that a try. 

I've never been able to get X11 Forwarding working though, so this isnt a guarantee.

---

### Post by mcg.mrk on 2011-04-14
Ok so i tried what you suggested.  After i ssh my laptop i then in turn ssh my laptop again with the option -Y.  I then attempted to run vlc player.  But i now get errors "No suitable interface module", "X11 initialization failed", "Could not connect to x server", **"Cannot open display"**, "Cannot initialize with OSFactory" and "interface "default" initialization failed".  I got the same errors when i tries option -X.

Any ideas? 

Thanks

---

### Post by NFblaze on 2011-04-14
You gotten better error messages than I've ever gotten.

Might be time to Google it. Or browse the man. (Offtopic-Rant:Whoops I better watch out lol. Some of the awesome :roll: mods around here might give me an infraction for that since that's technically against Community Guidelines....we'll see :D)

Another thought is to check your display environment variable and make sure the subssh gave you one.

I'd also check by seeing if you can run another simple X using application to see if it program specific or not. Though, that's all I can suggest.

---

