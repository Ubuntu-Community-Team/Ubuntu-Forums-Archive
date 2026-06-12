---
title: "Help..Lost bottom tool bar...???"
date: 2009-12-29
forum: General Help
---

### Post by robertcoulson on 2009-12-29
Hi, I deleted my bottom bar and all bars (e.g.) Abiword does not have ab X bar to close, etc...Can anyone help
Bob

---

### Post by jnew93 on 2009-12-29
Hmmm, maybe you have somehow disabled your window decorator. Try doing this: press alt+F2 and then in the box type xterm. Once the terminal comes up, type in it:

```
metacity
```

This will start the window manager. Hope that works!

---

### Post by robertcoulson on 2009-12-29
Hope you mean typing it into the terminal box..If so, I get  (see attachment) this reply.
Bob

---

### Post by robertcoulson on 2009-12-29
By the way ALT/F2 didn't do anything..Nothing came up.
Bob

---

### Post by jnew93 on 2009-12-29
Oh, it seems that you have it running. Can you be a bit more specific as to your problem? I've mistaken it. What bars are missing? (screenshot would be nice)

---

### Post by robertcoulson on 2009-12-29
Well..I was trying to delete something, but I deleted the bottom bar with (sorry about my terminology) where I had 4 windows to go back and forth from...Also the icon that would let me see the desktop and minimize everything on my screen.
Bob

---

### Post by perlluver on 2009-12-29
Do you have a top bar?

---

### Post by robertcoulson on 2009-12-29
Here is screenshot of my desktop...No bar at bottom

---

### Post by robertcoulson on 2009-12-29
Yes..I got my top bar back..Don't ask me how I did it thou.
Bob

---

### Post by jnew93 on 2009-12-29
OH! Ok, that's easy enough to solve. You're talking about the "GNOME-Panels" (They're on the top and bottom of the screen.) To get the bottom one back with all your tools, simply find a blank space on the top bar and right click, in the menu that drops down you should see the option "New Panel". When you select this there should be a new bottom panel created for you.

Now, to add your windows back to it, right click on the new blank panel and select the option "add to panel". The things you want to add are "Window List", and "Show Desktop". Once added, you can right click them and select "Move" to move the applets to where you want them.

Hope this helps! :)

---

### Post by robertcoulson on 2009-12-29
Well, I got my panel back at bottom and most of the things (like trash can) back..But they are in the middle of the panel...BUT, when I have firefox up and want to minimize it, it disappears and i have to bring it up again..same with say Abiword...??
Bob

---

### Post by robertcoulson on 2009-12-29
Guess this problem is not resolvable, so I think the only thing to do is wipe out Ubuntu....I still have dual boot with Xp.
Bob

---

### Post by fisheater on 2009-12-29
I did the same, here is the solution.

[http://ubuntuforums.org/showthread.php?t=1318353&page=2](http://ubuntuforums.org/showthread.php?t=1318353&page=2)

Preferences are files in linux, restore them to default and they will reset to normal.

Good luck,

FE

---

### Post by robertcoulson on 2009-12-29
Sorry to say I can't use what you have given me...When I see what to do, I can't minimize firefoe, because I have no "MIN" button or "X" button..Then I can't read what you have typed...Thanks anyway.
Bob

---

### Post by robertcoulson on 2009-12-29
Hey..Thanks for trying guys.....I an going to start using my XP again...Really wish Ununtu had worked out for me..It's great...Thanks Again.
Bob

---

### Post by jnew93 on 2009-12-29
No no no don't reinstall! You just need to move the applets (what these things are called) away from the middle! You do this by right clicking on them and selecting "move" then they will move with your mouse to wherever you drag them. In the case of the window list, there is a small bar or line/patch you need to find on the bar, then right click on, then select move. The windows will not show unless the bar has room to show them, make room by dragging other applets away from it.

OR better yet, if that does not work, do this, which will reset everything to look like the first time you logged in to Ubuntu, and everything will be back to normal. Open a terminal and enter this:

   ```
 rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

---

### Post by robertcoulson on 2009-12-29
Oh, believe me taht is the least of my problems...Figured that one out, but the rest of the stuff that is happening is what is making me want to go back to windows (yikes, did I say that )...I might have to reinstall Ubuntu somehow if I decide to stick with it, can't seem to fix the problem(s)
Bob

---

### Post by jnew93 on 2009-12-29
Aw. Remember we're here on the forums to help, and a lot of your problems can be solved by researching a bit. But, if you choose to switch back, we're sorry to see you go! :(

Try running the command I posted to return your desktop to defaults, then reboot, if you still wish.

---

### Post by robertcoulson on 2009-12-29
Well..Tried the terminal code, and the only thing that changed was my desktop background...Still have lots of problems and don't know how to fix them...
Bob

---

### Post by robertcoulson on 2009-12-29
One example....When I bring up firefox, it covers my drop down menu(s)...I have to close firefox to get at applications, etc.
Bob

---

### Post by robertcoulson on 2009-12-29
Ubuntu is worth one more try....Is it easy to reinstall....???
Bob

---

### Post by jnew93 on 2009-12-29
Yes very, if you still have the disk you installed it with, you can just go through the installer again and select the same things you did the first time, this should create a clean install. Just make sure you do not overwrite your windows partition.

---

### Post by robertcoulson on 2009-12-29
Did the reinstall and everything is back to normal...XP is OK...Now to figure out how to get the ADD/REMOVE menu under "system" drop down box..Hey, thanks for trying to help..I appreciate your time and patience.
Bob

---

