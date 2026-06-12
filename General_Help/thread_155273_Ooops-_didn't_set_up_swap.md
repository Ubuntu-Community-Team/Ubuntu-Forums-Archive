---
title: "Ooops- didn't set up swap"
date: 2006-04-04
forum: General Help
---

### Post by Lisa_T on 2006-04-04
I couldn't figure out how to set up the swop/ swap?? (sp) file during the installation process, so I left it. Can I manage it post install?

thanks

---

### Post by John.Michael.Kane on 2006-04-04
**Removed Since The Info Was Not Needed!!!!!.......**

---

### Post by LKRaider on 2006-04-04
Yes you can, no need to reinstall just to add swap space.

You'll have to make a partition in swap format, and enable it on fstab.

For the fstab file, you'll have to add a line similar to this:
```
/dev/hda4     none            swap            sw                             0       0
```

There is a wiki page with some more info here: [SwapFaq]("https://wiki.ubuntu.com/SwapFaq")

If you don't know how to make a new partition (hint: use gparted under Gnome), or if you have more questions, just ask.

---

### Post by Lisa_T on 2006-04-04
H'mm. Trouble is, it's not the best spec'd box to begin with. It's an old IBM x20 that's been set up with a dual boot for win 2000/ubuntu. I tried ubuntu a while ago and liked parts of it- and hated other aspects, but decided to give another go....

Current specs: 20 GB HDD (10 to each OS)
PIII 600
128 ram

-Ubuntu loads up fine, but as soon as I try to open an app, the whole thing slows to a serious crawl and crashes. I've had to force shut down both times which linux seems even more hissy about than win under similar circs. I doubt I could get ubuntu running well enough to even try Gparted! However, I do have a 'system rescue' cd that had QTparted on it among other things- would that do the trick? And how would I actually allocate the swap? I don't remember having this problem the last time I played with ubuntu on this machine...

Then again, maybe I'm overstating the speed. My main laptop is duo core, which is pretty fast- even with the win 2000 up, the IBM seems clunky in comparison. That was one of the reasons I wanted to give U another go. That, and the fact that it's supposed to be nearly out of the box compatible with my belkin wireless notebook card.

---

### Post by Lisa_T on 2006-04-04
where is gparted?

---

### Post by Lisa_T on 2006-04-04
AAAAggh. This is the kind of thing that *really* puts me off linux. I tried following the instructions in the linked swapfaq, and opened the terminal ok. I typed in the command line from the section on adding a swap partition. Computer asks for my password. I put in the password, but I don't see a row of asterisks- it just looks blank! And my cursor has disappeared- and the hard drive is apparently whirring away doing something, but I've no idea what cos this stupid terminal isn't telling me what the heck is going on!!!!

*takes calming breath*

Please help. This password-disappearing in terminal was one of the things that really put me off linux the last time i tried.

---

### Post by Mustard on 2006-04-04
qtparted from the system rescue CD will do just fine.

You should also probably contemplate whether you would be better off running a lighter desktop environment than gnome ie xfce or others

---

### Post by Mustard on 2006-04-04
[QUOTE=Lisa_T]AAAAggh. This is the kind of thing that *really* puts me off linux. I tried following the instructions in the linked swapfaq, and opened the terminal ok. I typed in the command line from the section on adding a swap partition. Computer asks for my password. I put in the password, but I don't see a row of asterisks- it just looks blank! And my cursor has disappeared- and the hard drive is apparently whirring away doing something, but I've no idea what cos this stupid terminal isn't telling me what the heck is going on!!!!

*takes calming breath*

Please help. This password-disappearing in terminal was one of the things that really put me off linux the last time i tried.[/QUOTE]

The password is never visible when you type it in from terminal.  The key presses are being entered, but no asterisks will appear each time you press a key.  Basically you should just type it in and hit enter.  If you made a mistake in your typing then it will tell you so.  If you see no password error appear, then it will go on to do whatever instruction it was being told to do.

What command were you giving it at the time, just out of curiousity?

---

### Post by Lisa_T on 2006-04-04
I'd be happy to try a lighter one- but which distros will work with my wireless card? If I can't get internet there's no real point- I'd like to play around with linux and see what apps they offer and so on, and it's a real pain trying to do that without the web, especially since I find the whole process of trying to install an app under linux very confusing. The ubuntu system sounds beautifully simple, but the simplicity does seem dependent on having a connection.

---

### Post by Mustard on 2006-04-04
[QUOTE=Lisa_T]I'd be happy to try a lighter one- but which distros will work with my wireless card? If I can't get internet there's no real point- I'd like to play around with linux and see what apps they offer and so on, and it's a real pain trying to do that without the web, especially since I find the whole process of trying to install an app under linux very confusing. The ubuntu system sounds beautifully simple, but the simplicity does seem dependent on having a connection.[/QUOTE]

When I say a different desktop, I suppose it could be interpreted as recommending another linux distro, but what I actually meant was to install a different desktop on your ubuntu installation.  I can see that without wireless working though, that it's going to be a while before you can do so.  Ubuntu is very much tied to being able to get online and installing another desktop would require that you be online to download the new desktop manager to your system.

-edit-

What is the model of your wireless card?

---

### Post by LKRaider on 2006-04-04
With that ammount of RAM, you should definetly try another desktop instead of Gnome.
You could try using [Xubuntu]("https://wiki.ubuntu.com/Xubuntu").

Also, if you have trouble using the interface, use a livecd to boot from and use it instead.

QTparted is also very good for doing partition work, and should be as easy to work with. I would recommend making at least a 512mb swap partition, if possible, since you are low on RAM.

BTW, I too have a PIII 600Mhz machine, but with 378mb of ram, and am running Gnome fine with it.

---

### Post by Lisa_T on 2006-04-04
It's the Belkin F5D7010- according to the list, it's supported. However, I've plugged it in, gone to System>Admin>Networking and the only connection listed is my ordinary modem. I understood from the tutorial that I should be able to see the card at that point?

Oh, and I finally managed to get the swap file sorted- well, I'm assuming I have. Since closing the terminal after attempting the instructions again, the system is smoother- tho' I wouldn't call it FAST- so I'm pleased at having achieved that much. 

Now to get the wireless sorted!

Oh, and I did configure it with 512. Will that procedure work with Xubuntu? It's downloading now- also, will I be able to get wireless support etc? And I'm happy to see that AbiWord is included, since I prefer AbiWord as a WP to OO.

---

### Post by Mustard on 2006-04-04
For the question of wireless support, I would recommend that you start a new thread that deals with that issue specifically, as the question is currently contained in a thread that initially asks about swap partitions.  This could mean that the right people to answer the question on networking might not have their attention drawn to this thread by the title.

---

