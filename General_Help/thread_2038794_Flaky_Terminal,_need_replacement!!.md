---
title: "Flaky Terminal, need replacement!!"
date: 2012-08-07
forum: General Help
---

### Post by killabuntu on 2012-08-07
G'day all,

I've recently installed Lubuntu and am quite happy with the way it runs on my Apple iBook. :) In the short time I've been playing around, I've noticed that LXTerminal seems a bit flaky.

When I wanted to add the battery icon to the system tray using the terminal, after entering the appropriate command and hitting enter, the cursor went to the next line where I was expecting to enter my password but it just sat there staring at me, not even blinking, it has done this a few times. Has anyone had this happen to them? I've never had a terminal do this before, what could it be? It does sometimes work ok but it seems... well, flaky. :(

Would I be better installing a different terminal app? If so, what would people recommend? Thanks for any help, cheers. ;)

---

### Post by LiamOS on 2012-08-07
Gnome terminal is fairly solid, but it might have some hefty dependencies(just use apt-get and check). 
I'm not using Ubuntu right now, and I have roxterm, which I like quite a bit, but I'm not sure what it's like on Ubuntu.

I've also heard good things of Terminator, but I didn't want to try that as it was pulling in a ton of dependencies on Gentoo.

---

### Post by killabuntu on 2012-08-07
Thanks LiamOS, I've seen Terminator (yes, and the movie) and like the look of it, never tried it, I've always used the Terminal/Console provided by the system but never seen this flakiness before. I don't have vast experience though either!!

I'll wait to see what others might suggest, too, thanks again.

---

### Post by cortman on 2012-08-07
> **killabuntu said:**
> G'day all,

I've recently installed Lubuntu and am quite happy with the way it runs on my Apple iBook. :) In the short time I've been playing around, I've noticed that LXTerminal seems a bit flaky.

When I wanted to add the battery icon to the system tray using the terminal, after entering the appropriate command and hitting enter, the cursor went to the next line where I was expecting to enter my password but it just sat there staring at me, not even blinking, it has done this a few times. Has anyone had this happen to them? I've never had a terminal do this before, what could it be? It does sometimes work ok but it seems... well, flaky. :(

Would I be better installing a different terminal app? If so, what would people recommend? Thanks for any help, cheers. ;)

I 99.99% guarantee this is because you either mistyped the command, or else it was a wrong command and just sat idling after entry. Don't worry, everyone does it. :) If you'd like help straightening that out feel free to write up another post.

> **killabuntu said:**
> I've seen Terminator (yes, and the movie) and like the look of it, never tried it.

Terminator is THE best terminal emulator for X that I've used yet- I was introduced to it by Crunchbang and was staggered how useful it is. Being able to infinitely split windows horizontally and vertically? WIN. :)

---

### Post by killabuntu on 2012-08-08
> **cortman said:**
> I 99.99% guarantee this is because you either mistyped the command, or else it was a wrong command and just sat idling after entry. Don't worry, everyone does it. :) If you'd like help straightening that out feel free to write up another post.



Terminator is THE best terminal emulator for X that I've used yet- I was introduced to it by Crunchbang and was staggered how useful it is. Being able to infinitely split windows horizontally and vertically? WIN. :)

Uh, no, how can you misspell 'top'?? No, I checked the spelling a couple of times (on a more complex command I got from a forum post) before hitting the enter key, (it did eventually work after several tries). It even hangs when invoking 'htop' from the system tray menu, no typing needed at all there.

I will, however, consider your recommendation regarding Terminator, although I don't need that level of functionality. Not sure about those dependencies, though, as reported but LiamOS. Maybe, it is different on Lubuntu???

Anyway, thanks for your help and suggestions, both of you, cheers.

BTW I see that roxterm is available on the Lubuntu Software Centre.

---

### Post by cortman on 2012-08-08
I'd still be surprised if it was the terminal emulator, but a surefire way to tell: Press Ctrl+Alt+F2 to drop into tty2. Log in and try to run "top". If it runs fine, it's obviously your emulator- if not, you have a bit of a system problem.
Oh, and you can get back to the GUI with Ctrl+Alt+F7. :)

---

### Post by Primefalcon on 2012-08-08
terminator is good, you might also wanna try guake terminal, guake offers a drop terminal on the press of a hot key, very good for quick terminal things.

of course you could always do ctrl+alt+f[1-7]

---

### Post by black veils on 2012-08-08
xfce4-terminal

---

### Post by killabuntu on 2012-08-08
Hey, thanks for all the suggestions, I'll certainly keep them in mind. Just for the moment, I've come across a small footprint terminal called Sakura from the Lubuntu Software Centre and installed that. If it works for all the use I need it for then that will do me. If I need something with a bit more power and flexibility then I will look into the ones suggested here, thanks again.

With LXTerminal, when it finishes logging in it seems to work fine but it doesn't always finish the login and I can't input anything. :(

And thanks cortman for the tty2 option, (yes, it worked fine, as I expected it would) I was aware of it but couldn't remember how to invoke it, cheers, I'm sure it will be useful.

Catch you around the forums.

---

### Post by cortman on 2012-08-08
> **killabuntu said:**
> Hey, thanks for all the suggestions, I'll certainly keep them in mind. Just for the moment, I've come across a small footprint terminal called Sakura from the Lubuntu Software Centre and installed that. If it works for all the use I need it for then that will do me. If I need something with a bit more power and flexibility then I will look into the ones suggested here, thanks again.

With LXTerminal, when it finishes logging in it seems to work fine but it doesn't always finish the login and I can't input anything. :(

And thanks cortman for the tty2 option, (yes, it worked fine, as I expected it would) I was aware of it but couldn't remember how to invoke it, cheers, I'm sure it will be useful.

Catch you around the forums.

Great! It's definitely a terminal problem then; which is weird, but possible, I guess.
Mark as [SOLVED] if it indeed solves your problem. Thanks!

---

