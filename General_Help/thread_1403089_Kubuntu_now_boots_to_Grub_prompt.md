---
title: "Kubuntu now boots to Grub prompt?????"
date: 2010-02-09
forum: General Help
---

### Post by portlandaudio on 2010-02-09
Hello, I recently installed Kubuntu with the windows installer wubi. Everything has gone fine until today. When i turn on the pc i normally have a prompt to go to windows or kubuntu. I choose Kubuntu and it loads it up. But now it goes to a grub prompt and i have no idea how to fix this or get into Kubuntu.

Things i did before the last reboot that may have caused this.

I edited my swappiness to help speed things up at the advice of many websites. 

Example: [http://blog.kutakutik.or.id/linux/tu...kubuntuubuntu/](http://blog.kutakutik.or.id/linux/tu...kubuntuubuntu/)

I changed it from 60 to 10. I did this by adding the line "vm.swappiness=10" to the end of sysctl.conf

I noticed that there was a # or something at the beginning of every line in sysctl.conf and i did NOT add it to my line. This is my guess as to why i am having problems.

The other thing i did was some bug updates. Something was popping up down by the clock area and it was asking me to do some bug updates of some sort. I said yes.

Any idea on how i can fix this? As of now i cannot get into kubuntu at all. It just gives me a grub command prompt.

---

### Post by houseworkshy on 2010-02-09
I haven't used the wubi way of duel booting, however did have a similar problem a long time ago.  What got me out was to use the gdm ( gnome desktop manager ) command.  In Kubuntu the equavalent is kdm ( kde desktop manager) I think.  For any command if you type man in front of it then, if linux is actually running you will open the manual for that command.  So trying "man kdm" would serve as a diagnostic, to test if linux is actually running *and* show you how to use the command.  To close a manual page type "q".  As I use a Gnome gui and don't know about wubi installations I can't offer much help.  The link in your post led me to a 404 error. That might just be me, my internet has been a little odd recently, couldn't log in earlier.

A few things that might help indirectly if you are at a linux command line.  Try entering "info info" and "man apropos" These commands only open help pages and don't change anything so are safe.  Using them you could find out how to navigate around, open the editor and undo what you remember doing.  That might help.  Be cautious though as you would probably need to use gksu ( enter "man gksu" for details )for the editor, which would give it root powers, try without first if you can.  In gnome the editor is gedit which may mean that in kde it's kedit, that's only a guess, if wrong "apropos edit" should dig it out.  Commands found by "apropos install" would be worth looking at especially the update and upgrade options for whatever it is Kubuntu uses, I'm fairly sure its apt-get and aptitude but double check using the man command anyway.  Good luck.

All uses of "" are only to surround what is to be entered, not to be entered themselves.

You really need a Kubuntu person on this as it is probably an Xorg thing pertaining to the kde enviroment, which is differant, so your best bet is to find out if you are at the linux command line using man commands which can't do any damage.  Mention here if you are or not, also mention which version of Kubuntu you are on and wait for a Kubuntu person to post.

---

### Post by portlandaudio on 2010-02-09
> **houseworkshy said:**
> All uses of "" are only to surround what is to be entered, not to be entered themselves.


I didnt type the quotes in sysctl.conf

I just typed them in this forum so you knew what i typed. What i typed exactly was:


vm.swappiness=10


I added this as the last line in sysctl.conf


I used the editor Kate i believe.

---

### Post by houseworkshy on 2010-02-09
That was understood.  I was refering to my own post, eg "man apropos"

---

### Post by meierfra. on 2010-02-09
> The other thing i did was some bug updates. 
That's what caused it. For more details and how to fix it see:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by houseworkshy on 2010-02-09
I shall have to leave as I have to get out of the bed I'm not even in yet in ....arhhh two hours.  I'll look in again later today (after work ) Good luck with it.

---

### Post by houseworkshy on 2010-02-09
I've looked, I shall come back and look again later but must sleep now.  With luck some one who knows more will have helped you mend it by then.  Good forum is this.  Bye for now.

---

### Post by Marty- on 2010-02-09
I had the same problem with the Grub terminal coming up as well.

I posted a thread and somebody was able to help me fix it, you should check it out:
[http://ubuntuforums.org/showthread.php?t=1403126](http://ubuntuforums.org/showthread.php?t=1403126)

---

### Post by portlandaudio on 2010-02-09
> **meierfra. said:**
> That's what caused it. For more details and how to fix it see:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)


Thank you so much! This was super simple and fixed it immediately!

---

