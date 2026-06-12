---
title: "Help with &quot;gksudo nautilus&quot;"
date: 2011-08-31
forum: General Help
---

### Post by vasa1 on 2011-08-31
Newbie on Ubuntu 11.04 ... I installed 11.04 just a couple of days ago as a dual boot with Win 7. I've accepted all updates.

When I type "gksudo nautilus" in a terminal, I'm prompted for my password. After I provide that, I see this:
"Initialising nautilus-gdu extension".

Nautilus also opens.

Even after closing the nautilus window, this "Initialising nautilus-gdu extension" message remains in the terminal and I don't get the "$" prompt. If I click the close button on the terminal window, I get a message that a process is still running and that closing the terminal will kill it.

It looks like something isn't right. Can someone help?

---

### Post by decrepit on 2011-08-31
Bit of a mystery!
Just tried that on my 10.4 machine, exactly the same happened, but instead of closing the console I hit "Ctrl C", that got me back to $prompt.
I then tried "gksudo nautilus" again and everything behaved properly.
I suspected that doing ">file>close all windows", would work better, but guess I'll have to wait until I close down and restart to find out.

---

### Post by vasa1 on 2011-08-31
> **decrepit said:**
> Bit of a mystery!
Just tried that on my 10.4 machine, exactly the same happened, but instead of closing the console I hit "Ctrl C", that got me back to $prompt.
I then tried "gksudo nautilus" again and everything behaved properly.
I suspected that doing ">file>close all windows", would work better, but guess I'll have to wait until I close down and restart to find out.

Thank you for confirming that!

After reading your post, I tried "gksudo nautilus" again, and there wasn't that initializing message, just the $ prompt as it should be. Strange but good!

I won't mark this as "solved" right away. Better keep one eye on this for a while.

---

### Post by dino99 on 2011-08-31
nautilus dont need to be root

---

### Post by saltmarshlamb on 2011-08-31
Unless you want to use it to do stuff as root.

---

### Post by vasa1 on 2011-08-31
> **saltmarshlamb said:**
> Unless you want to use it to do stuff as root.

That's about it.

I was trying to set up Privoxy. Rather than editing its user.action file line by line, I wanted to copy over a user.action file that I had used successfully in Windows 7. To do that I needed permission. That's why I resorted, rightly or wrongly, to this route.

I remember seeing a friend's PC running Mint 11 that had Nautilus set up such that a right-click would show "open as root" or something to that effect. I searched a bit but didn't find how to do it on my system but that was very convenient.

---

### Post by saltmarshlamb on 2011-08-31
You can of course use the terminal to accomplish things of this nature - some prefer not too :)

---

### Post by jerrrys on 2011-08-31
is this what you mean?

[ATTACH]201157[/ATTACH]

---

### Post by Frogs Hair on 2011-08-31
I am unable to reproduce the result ; however , the the extension message remains until the terminal restarts with no indication of a running process.

---

### Post by vasa1 on 2011-08-31
> **jerrrys said:**
> is this what you mean?

[ATTACH]201157[/ATTACH]

I don't think anything comes closer than that! I'm going to give it a try.

Thank you!

:D

Re. using the terminal, I'm not allergic to it, but please give me a little time to find my feet first.

---

### Post by vasa1 on 2011-08-31
> **jerrrys said:**
> is this what you mean?

[ATTACH]201157[/ATTACH]

Marked as "solved". I had to reboot to see the change but it's all good now.

---

