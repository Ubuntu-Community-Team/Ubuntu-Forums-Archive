---
title: "Keyboard failure - but only in one user account"
date: 2011-01-11
forum: General Help
---

### Post by chip616 on 2011-01-11
This is the second machine of mine where the keyboard has quit once the machine is fully booted.  However, this only happens in one user account, in both cases, the most-used account.  The keyboard works fine in the other user accounts on both machines, and the keyboard works fine in all accounts when logging in.  It is only when Kubuntu 8.04 is up an running that the problem occurs.

In the problem accounts, pressing and _holding_ one of the keys does generate input, but it comes in pairs.  I cannot type a single letter.  It looks like the delay and repeat rates are messed up, but resetting them in the control panel does nothing.

On one machine, I just installed a newer version of the OS.  On the machine in question now, however, it is a business machine, and I don't want to have it down if I can 'save' it.

I am guessing that this is a config issue somewhere in the innards of KDE 3.5.  Can I safely delete a hidden directory somewhere, and force KDE to recreate a new set of config files?

Thanks.

Frank.

---

### Post by tredegar on 2011-01-11
You could try *renaming* **~/kde **
Do NOT delete it as it contains all your emails, and possibly other important stuff.

Here, I am assuming **yourself** is the problem user

Boot.
Do not login.
CTL-ALT-F2 to get a terminal
Login as yourself
```
mv ~/.kde ~/kde.bak
```
Logout.

CTL-ALT-F7 (or F8, I forget).
Login to the GUI as yourself .
You will have lost your customisations, but does the keyboard work?

You can use the same procedure to **rm -rf ~/.kde** (the newly generated default one) and then **mv ~/kde.bak ~/.kde** to put things back as they were. You _cannot_ do this from the GUI.

kubuntu 8.04 was good (and I admit I am still using it), but it is out of date, and only receives security updates now. I hate KDE4, so have switched to gnome on 10.04, and will probably soon move to Debian.

---

### Post by chip616 on 2011-01-12
tredegar:

> You could try renaming ~/kde 

Thanks.  I thought I'd try that today anyway.  And, yes, I was not planning on deleting it, for the reasons you mention.

As this is a business machine, I have done little to customize it, so I can easily re-create the few changes made.  It has no mail account, just a few OOo templates which I have on other machines anyway.

All my machines have the root account enabled, so I can make the change you mention from the comfort of the root gui.  :)  Situations like this are just one of the reasons why I disagree with the 'no root' philosophy of Canonical.  At least it is possible to switch back to a more 'normal' way of doing things in the 'buntus.

I won't be back in to work until later today, but I'll post back and let you know what happened.

Thanks for confirming my suspicions.

Frank.

---

### Post by tredegar on 2011-01-12
See what happens.
Please note the typo in my last post: It's **~/[COLOR="Red"].[/COLOR]kde** not **~/kde**

---

### Post by tredegar on 2011-01-12
Double-post due to system glitch.

---

### Post by chip616 on 2011-01-12
tredegar:

>It's ~/.kde not ~/kde<

Not a problem.  I knew that anyway.

Thanks again for the suggestion.

Frank.

---

### Post by chip616 on 2011-01-12
tredegar:

OK, worked like a charm!  I went in through root, renamed .kde to .kde.old, and then switched users to the problem account.  KDE recreated the .kde config directory, and the keyboard worked fine.

The only thing I lost were my wallpaper settings, and the panel settings.  Everything else was fine, which, if I'd thought it through, one would expect.  All the other apps have their own config directories, which I did not touch, and all my desktop launch icons are in the ~Desktop folder, which again was untouched.

So, successfully accomplished!

Thanks again.

Frank.

---

### Post by SObailey on 2011-01-20
Hi.  Not sure whether or not I can post on a solved thread and  I could not find the answer on that question so my apologies in advance.  I'm having the very same problem chip616 was having word for word only in Ubuntu 10.04 LTS (Lucid Lynx).  I don't quite understand the process for fixing this. I'm still a beginner.  I can reboot but my computer is set to automatically log in so I need to start there.  How do I bypass auto login?  Then, how do I go about renaming ~/.KDE? If in fact thats what I need to do? Thanks and again my apologies If I'm in the wrong for posting on a solved thread.

Sid

---

### Post by SObailey on 2011-01-20
Hi.  Not sure whether or not I can post on a solved thread and  I could not find the answer on that question so my apologies in advance.  I'm having the very same problem chip616 was having word for word only in Ubuntu 10.04 LTS (Lucid Lynx).  I don't quite understand the process for fixing this. I'm still a beginner.  I can reboot but my computer is set to automatically log in so I need to start there.  How do I bypass auto login?  Then, how do I go about renaming ~/.KDE? If in fact thats what I need to do? Thanks and again my apologies If I'm in the wrong for posting on a solved thread.

Sid

---

### Post by SObailey on 2011-01-20
Hi.  Not sure whether or not I can post on a solved thread and  I could not find the answer on that question so my apologies in advance.  I'm having the very same problem chip616 was having word for word only in Ubuntu 10.04 LTS (Lucid Lynx).  I don't quite understand the process for fixing this. I'm still a beginner.  I can reboot but my computer is set to automatically log in so I need to start there.  How do I bypass auto login?  Then, how do I go about renaming ~/.KDE? If in fact thats what I need to do? Thanks and again my apologies If I'm in the wrong for posting on a solved thread.    Sid

---

### Post by SObailey on 2011-01-20
p { margin-bottom: 0.08in; }   Hi.  Not sure whether or not I can post on a solved thread and  I could not find the answer on that question so my apologies in advance.  I'm having the very same problem chip616 was having word for word only in Ubuntu 10.04 LTS (Lucid Lynx).  I don't quite understand the process for fixing this. I'm still a beginner.  I can reboot but my computer is set to automatically log in so I need to start there.  How do I bypass auto login?  Then, how do I go about renaming ~/.KDE? If in fact thats what I need to do? Thanks and again my apologies If I'm in the wrong for posting on a solved thread.    Sid

---

### Post by chip616 on 2011-01-20
SObailey:

Your keyboard is not working?

The problem I had was specific to Kubuntu 8.04.  If you have a problem with your keyboard not working, I'd be inclined to start again troubleshooting from scratch.

My keyboard worked in other accounts on the SAME computer.  Few Ubuntu users have more than one account on their machine.  Do you?

Does the keyboard work on another machine?  Can you put a different keyboard on the problem machine?  Even laptops will often accept an external keyboard.

Give us the answer to those, and we'll see what might be done.  What worked for me in 8.04 may not work for you in 10.04.

Frank.

---

