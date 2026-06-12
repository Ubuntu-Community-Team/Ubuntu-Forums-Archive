---
title: "Launching folders, websites via keyboard shortcut"
date: 2012-03-12
forum: General Help
---

### Post by SyntheticShield on 2012-03-12
Is there a way in Xubuntu to launch/open a folder via a keyboard shortcut?  How about opening a website that way?

Ive used the keyboard settings to create keyboard shortcuts to applications I use frequently but would love to do the same with other such things but do not see how to do so in keyboard settings.

If it makes any difference, Im using a Logitech wireless keyboard and mouse.

---

### Post by LewisTM on 2012-03-12
Use the [FONT="Courier New"]exo-open [/FONT]command in your shortcut. For example:
```
exo-open /home/user/Music
exo-open http://www.website.com/something
```

Cheers!

---

### Post by SyntheticShield on 2012-03-13
Thanks Lewis for your reply.

That is just friggin' brilliant.  I never knew you could do that.  Thank you so much for that tip.  Ive got to write that down so I dont forget it.

---

### Post by SyntheticShield on 2012-03-13
If I may trouble you for one other thing, or anyone that may have the answer for that matter.  The CD eject button is not working on the keyboard.  My experience has been its a hit or miss proposition.  Ive had a couple of laptops that it works on well, and I have one that it does not.

That said, what is the command to eject the CD/DVD tray (or close it) so I can add that to the keyboard shortcuts and activate that key as well.  Thanks.

---

### Post by SyntheticShield on 2012-03-13
Let me add Ive tried

eject
eject cdrom

and a few others, and none open the CD/DVD tray.  However, I can open it, and then close it via the command line eject -t cdrom.  So what is the opposite of that command? LOL.

---

### Post by SyntheticShield on 2012-03-13
Okay, sorry about the multiple posts so quickly, guess I should have just done some more searching.

The command eject -t will close the tray if its already open, but wont open it if its closed.  Oddly enough, change it to eject -T and it will open and close it.  Problem solved.

---

### Post by LewisTM on 2012-03-13
Glad you got it all figured out!
Please mark as SOLVED.
Also these are support forums so you should open new threads for each new problem or question.

---

