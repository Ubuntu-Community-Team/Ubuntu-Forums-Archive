---
title: "Reassigning Caps Lock to the letter &quot;R&quot;"
date: 2011-05-09
forum: General Help
---

### Post by Percivale on 2011-05-09
Hi,

I am completely new to Ubuntu and these forums.

I just installed Ubuntu 11.04 on my Dell laptop yesterday. This laptop has seen better days, and the R key is barely functional - I have to dig my thumb into it with tremendous strength in order to pop out a tiny little 'r.'

When I had Windows XP installed, I downloaded the program "Sharpkeys" and reassigned the Caps Lock key to be my new letter r. No problems.

My understanding is that Ubuntu is completely customizable, though all the keyboard options in the "Keyboard" control program are premade - there is no option to edit any keyboard layouts to my liking. A little frustrating and disappointing.

I have done some research into how to edit some of the system files. Forum searches led me to try editing files in usr/X11/xkb/symbols/; although the full keyboard layout file I tried to edit, "us," does not refer to caps lock at all; and the capslock file only refers to standard, premade capslock swapping functions, as listed in the "Keyboard" control program in a drop-down list.

I then ventured into Xmodmap. I was able to look into it. I found an "ehow" page that told me that I could edit .xmodmap by adding a couple lines to the .bashrc file. I tried this. I typed:

Xmodmap -e 'keycode 66 = r R'

But it had no effect. In fact, in the terminal, a bunch of error messages appeared:

(gedit:3015): Gtk-WARNING **: Attempting to store changes into '/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9BFZUV': No such file or directory

And five other similar warnings.

Any help would be appreciated. What is going on here? How do I assign the letter R to my Caps Lock key?

Thanks!

---

### Post by Percivale on 2011-05-10
UPDATE:

I figured out that by executing

usr/bin/X11/xmodmap -e 'keycode 66 = r R r R'

I could get the Caps Lock key to serve as my R key.

The problem is that it is simultaneously acting as a Caps Lock key.

So my current questions are:

Where is Ubuntu getting the signal to use Caps Lock as Caps Lock, even though I have changed the keycode?

How can I rectify this, so that Caps Lock only prints r or R and doesn't act as Caps Lock anymore?

Thanks again.

---

### Post by Percivale on 2011-05-10
UPDATE:

Having shut down my computer last night and starting it up again this morning, I've discovered that the changes I made in the last post did not remain. 

New question: how do I make such changes permanent?

---

### Post by Ghost|BTFH on 2011-05-10
Tutorial found [HERE...]("http://ubuntuforums.org/showpost.php?p=7675138&postcount=2")

Focus on Step 3 + for how to make it permanent.

Cheers,
Ghost|BTFH

---

### Post by Percivale on 2011-05-12
Thanks, Ghost.

I have been able to permanently modify the xmodmap with the suggestions. I still have one major problem, one minor problem and an error message I'd like to understand better.

The Major Problem: I still have not figured out how to permanently disable the "lock" function of the caps lock key, even though it is now printing "r"s. If I hit the key several times, it looks like this: rRrRrR. I have downloaded xkeycaps, and I have used that program to temporarily turn the caps lock key into a normal letter key, but I don't know how to make those changes permanent, as it seems that whether or not a key has a modifier function is not governed by xmodmap.

UPDATE: This problem was solved. I didn't figure out how to do in manually, but I went back and made the permanent changes with xkeycaps. I'm still curious as to how to do it manually, if anyone knows.

My assumption is that if I knew which file governs modifiers, I could make permanent changes in a way that's similar to what's described in the link that Ghost posted. Is that true?

The Minor Problem: Any changes I make to xmodmap are only active once I am logged in as a user. Caps lock behaves as normal in the login screen, and I cannot print any "r"s. This is not an issue if I simply don't include any rs in my passwords and user names. Is there a way to fix this?

The Error Message: After creating the files according to the thread in Ghost's link, every time I open up the Terminal it prints:

"No command 'Xmodmap' found, did you mean:
 Command 'xmodmap' from package 'x11-xserver-utils' (main)
Xmodmap: command not found"

I followed all the instructions as listed, and it also functions as it's supposed to. What is the problem here?

Thanks for your assistance.

---

### Post by Percivale on 2011-05-12
UPDATE: I have an explanation for the error message. It was from a past attempt to edit the .bashrc file. Everything is now cleaned up.

So the problem still stands: is there any way to carry my changes to xmodmap over to the login screen, or can they only come into effect when I am logged in as a user?

This is the final piece to the puzzle. Any help will be much appreciated. I hope that showing my work will help other people in the future.

---

### Post by Ghost|BTFH on 2011-05-12
Quick guess before I pass out - in the file made, if it says Xmodmap, use xmodmap instead.  Linux is VERY case sensitive.

Cheers,
Ghost|BTFH

---

