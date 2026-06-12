---
title: "Invalid option: - session"
date: 2011-02-27
forum: General Help
---

### Post by hercandcarver on 2011-02-27
Hey guys

When Ubuntu 10.10 loads I get the above pop-up after logging in.

Does anyone know how I would go about finding out what this refers to, or how I could address it? Thanks.

---

### Post by hercandcarver on 2011-02-27
I've seen variants of my problem from googling it, but nothing quite the same. Haven't got a clue where to start. It's just annoying to get an error message every time you log in!

---

### Post by nicolargo on 2011-03-11
I have the same issue...

Ubuntu 10.10: Invalid option: -session

Any idea ?

---

### Post by Frogs Hair on 2011-03-11
When search  this error I find posts having to do with Oracle Data base , anyone using this ?

---

### Post by lervag on 2011-04-07
I also experience the same issue. Really annoying, and I have no idea how to find the source of it. Any help is appreciated!

---

### Post by AnWe on 2011-06-03
I think I've found the cause of this annoying problem. For me there was an entry in ~/.config/gnome-session/saved-session/ that seemed to trigger the problem. Check the files in that directory for your user with rgrep:

```
rgrep " \-session" ~/.config/gnome-session/saved-session/
```(This will search for the string " -session" in any files in that folder or it's subfolders, the space is there intentionally)

In my case one of the files tried to start Spotify with the option "-session" which didn't work and popped up the message. I just moved the file out of the directory and that seems to have solved the problem. I've only rebooted once to test though, YMMV.

If that doesn't work you can use rgrep to search other folders for the same string.

PS: I'm on 10.04

/Andreas

---

### Post by AnWe on 2011-06-04
Correction:
You also have to use "gnome-session-properties" (can be found under system->settings as well, don't know the english name for it in the menu though), and uncheck the box that autosaves your session when you log out. Otherwise there is a good chance the program that causes the error will be saved to the session again next time you log out/shutdown...

Alternately, you could make sure to close the offending program before you shut down/logout, but that would take some discipline...

Hope this helps, would be interesting to know if this solves the problem for you too.

PS, i guess the mechanism for session saving is different in unity, but i don't use it, so i can't comment on that. The solution would be similar though.

/Andreas

---

### Post by dezzadk on 2012-05-05
**OK- Here is the best solution I could find in a few minutes- in KDE or GNOME find your settings for "Sessions"**
[B]
Change it to not save the session by default[/B], but only on explicitly selecting "Save Session" button in the "Leave" tab (in KDE for me, you would probably find something similar in GNOME- go look it's a GUI it's meant to be explored in every corner) ..

This was a fresh install of the latest image of Kubuntu (because updating the USB with Kubuntu I had lying around literally breaked the system with errors on errors), so it really makes me wonder why errors such as this is allowed to go through to users new to Linux! I actually installed this on my mom's computer- and I would have been embarassed if I left her with a computer that starts up the Desktop Environment with a big fat red error saying "invalid option: -session" she would be clueless ! I know that most distributions can't do alot without a big investor, but that big investor doesn't have to make a product worse than it already is (Debian is stable, why isn't Ubuntu stable? Ask yourself, I don't care!)

And then there was alot of other crazy error messages like arab letters and something about a failed update, button says: "Run action now?", this is all I can remember.. Well I won't pick more on Ubuntu, I would rather say- please learn from your mistakes ..

**Whatsoever, I ended up here searching Google for the problem- so I left the solution here as well for whoever might find this thread in the future.**

This is _**NOT**_ to revive a year old thread or make fuzz in the forums, but nevertheless no top poster in here came with a valid solution (Erhm? Why are you holding yourself back? You could at least try! Instead of having endless new users post one after another that they have the exact same problem- and no one really cares, because you are all leet linux users now that you have a few hundred posts on the Ubuntu forums) ..

And no, I won't answer your 3 next replies telling me that I am an "Ubuntu-hater" and a "Debian-fan", forum troll- year-old-thread-necrofile-who-likes-to-go-to-bed-with-old-threads ..

Instead edit my post like I expect you to do .. It's just a big shame to have the truth out there than to leave an unanswered (but common) problem hanging on the "I feel lucky" button with this exact problem on Google. I made a user here to make another user using this broken install-image have a little hope in Ubuntu, by at least being able to find a solution on his first search on Google- so you don't have to play elite and pick on him on IRC.

Bye!

---

