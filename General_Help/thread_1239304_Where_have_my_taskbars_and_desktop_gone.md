---
title: "Where have my taskbars and desktop gone?"
date: 2009-08-13
forum: General Help
---

### Post by Macfunky on 2009-08-13
I have Ubuntu Netbook Remix installed on my Acer Aspire One. It had all been going fine until i installed XFCE to see if it would make it a bit quicker. With the netbook remix this doesn't seem to go down too well. When i booted into XFCE i got a mix of XFCE and Gnome and anytime i plugged in a memory stick it opened up in both thunar and natilius. When i then booted into Gnome thats when the real problem happened. It booted up and i logged in but when i logged in i had just my wallpaper on the screen. No taskbars. The only thing i could really do was right click and choose change desktop background. When this window opened up it was missing the borders. 

I figured the easiest way around this was to back up my stuff from XFCE because as annoying as it was to use at least i could do stuff in it as opposed to Gnome. I then reinstalled UNR. It installed ok and once it was installed it was working fine. That was until i updated it. I installed the updates (before touching anything else). Then when the updates were installed i restarted the netbook. Once again i have hit the EXACT same problem. I am very confused as this is a clean reinstall yet i have the exact same problem. It was working perfectly before i updated the machine. Does anyone know what could be wrong? Nothing in it works. I can't even use alt + F2. Any help would be appreciated. Thanks

---

### Post by P4man on 2009-08-13
Are you using desktop effects? It seems the netbook remix needs a bit more.. remixing :s. Maybe this helps:

[https://bugs.launchpad.net/maximus/+bug/335730](https://bugs.launchpad.net/maximus/+bug/335730)

(ignore the maximus thing, read further down)

---

### Post by Macfunky on 2009-08-13
I never use desktop effects and they are definitly not switched on. The taskbars are not invisible either. I have checked to see if they were but they're not. There is no functionality past right clicking and selecting an option and these come up with no window borders. This happened after a completely fresh install as well. Thats what has me really baffled. Anyone have similar problems or any ideas at all? Thanks

---

### Post by Macfunky on 2009-08-13
This is really bugging me. Have been trying to figure out whats up and i can't figure out what could be up. Any help?

---

### Post by rednano12 on 2009-08-13
Sounds like your Window Manager is messing up. Try Alt-F2 and then metacity --replace.

---

### Post by P4man on 2009-08-13
The OP wrote that even alt F2 isnt working. Sounds like gnome is not loading at all.. but why or how to solve that?


Macfunky, if you press control alt F2, do you get a console at least?
Perhaps you can try something like

```
sudo /etc/init.d/gdm restart
```

---

### Post by Macfunky on 2009-08-13
Alt + F2 shows up absolutely nothing at all. Nothing whatsoever happens. The only thing i am able to do and get a response from is right click and get the options. I can use these but for some reason no window border shows up on these

---

### Post by Macfunky on 2009-08-13
I can right click and create a launcher. Tried this and it works but once again no window borders on the apps. Is there something i could create a launcher for that might help me figure out whats going on?

---

### Post by Macfunky on 2009-08-13
Is it possible that the .img file i downloaded was slightly corrupted? Thats the only thing i can think of although i do find it very unusual that the same problem happened when i installed XFCE before that. It seemed to only be affecting Gnome. I am on mobile broadband at the moment and have a limit. I would prefer to wait til i get home (won't be a day or two) to download the file again if its needed. 

It couldn't be hardware could it? I'd imagine it wouldn't be because it seems only to be the desktop thats affected. Just thought it might be worth asking seeing as the same thing has happened 3 times essentially now even a fresh install.

---

### Post by Macfunky on 2009-08-13
I have created a launcher for configuration editor. Is there anything in here that i could do to see whats wrong? Sorry for all the posts. Just desperate to sort it out. Thanks for any help so far :)

---

### Post by Macfunky on 2009-08-13
How do i create a launcher for the terminal? Maybe this would be the way to go. What command do i use to create the terminal launcher. I tried "terminal" but it didnt work -

"There was an error launching the application. 

Details: Failed to excute child process "terminal" (No such file or directory)"

---

### Post by P4man on 2009-08-14
```
gnome-terminal
```

But are you saying **control**+alt+F2 does nothing? Thats almost impossible lol

---

### Post by Macfunky on 2009-08-17
Anyone?

---

### Post by pdowling on 2009-08-29
Any fix for this.  I'm having exactly the same symptoms, to wit...

disabled maximus
upon restarting and logging in to gnome I see desktop icons, but no panels and no way to do anything to get them back that I can see.

Anyone?  Computer is a brick right now.

---

### Post by NoaHall on 2009-08-29
Start a new thread, with a new title - you'll get more replies.

---

### Post by epicoder on 2009-08-29
try creating a launcher for 'gnome-panel'.

---

### Post by jenkinsororo on 2009-09-18
Oh, this isn't the thread I was looking for...

---

### Post by RifRaf1961 on 2010-09-29
The community center in my town switched to Ubuntu with XFCE.  The strange thing is all but one of the computers is having the exact problem (no top and bottom taskbars).  All of the computers are identical.  It is really annoying trying to teach people how to do things when the systems are not the same.  Another reason the taskbars are nice is to see which programs are running and how many copies of each.  One kid had Firefox open twice, porn in one instance and the assignment in the other.  When the teacher wasn't looking he would flip between them.  Without the taskbars the instructor couldn't see the multiple Firefox instances when walking by the desk.

Has anyone figured out how to get the taskbars back?  I would really like to help the community center out of this jam, but I don't see any option to bring them back (or even turn them off for that matter!).

Thanks!

---

### Post by P4man on 2010-09-29
Ive recently noticed what I *think *is the same issue: after installing netbook interface (clutter) it took more than a minute after it showed the desktop for the panels to appear. Turns out I had to blacklist a driver for the winmodem.

Try waiting a full minute or longer (this was on a fast machine) or try switching to a TTY with control +alt+F1 and run 

dmesg

I had endless messages about that driver (dont recall the name).

---

