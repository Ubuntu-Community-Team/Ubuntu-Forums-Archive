---
title: "Please!!! Urgent help!!! I erased everything!"
date: 2009-10-25
forum: General Help
---

### Post by Radissthor on 2009-10-25
I was trying to solve a problem that had to do with running a windows application through Wine. At some point I had to copy a dll file in my home folder and then copy it to C:/Win32 of the Wine folder. I didn't delete the file I had copied in the home folder. 

Then I tried to remove the applications I had installed using Wine cuz I wanted to install them again. So following the Wine wiki I typed this in the terminal:

rm -rf $HOME/.wine

It took a while and said it couldn't because the folder was being used or something like that. I closed the terminal and my background image was gone... I tried to enter my home folder... and IT WAS GONE TOO!!!

I reeboted, thinking the computer had just gone crazy, but then it was all gone!!! even my firefox configuration... It's like I had just installed Ubuntu... the weird thing is that the programs I had installed are still there (audacious, tuxguitar, even wine! )

PLEASE!!! somebody help!! I've lost everything!!!

---

### Post by shadow120 on 2009-10-25
when you use that command its gone there may be a way to get it back but not that i know of

---

### Post by fluffman86 on 2009-10-25
If you wouldn't have rebooted, then you may have been able to recover some of the files with photorec.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

But since you deleted your home folder and rebooted, most of the .hidden folders and data has been written over and recreated.  

It's still worth a shot, though.  I suggest taking your hard drive out, putting it in another computer, and mounting it read only, rather than using that computer to run photorec on itself.

---

### Post by Radissthor on 2009-10-25
Oh my god O_O

Isn't there another way?? I'm a complete newbie with computers and getting the hardrive out is way out of my league x_X, besides, it would ruin the guarante since it's a newly bought dell inspiron 1525

---

### Post by winotree on 2009-10-25
> ....It's like I had just installed Ubuntu.... If that's so then you couldn't have that much personal information on it, that much tweaking done.  Or could you?  Maybe it would be easier to reinstall your Ubuntu and start fresh -- I know I'd choose that route knowing what *those other guys* have said.  :|  But don't take my word on it -- wait and see what some others have to say, OK?  ;)

---

### Post by ndefontenay on 2009-10-25
Hi.

There's no easy way around it. You'll have to try to use photorec and go through the procedure explained above. It's called learning the hard way and you will be a lesser newbie when you've been through it with success or not.

The easy way is as stated already: Start fresh.
Finally, to avoid this painful experience again, ask yourself this question for the following: If I loose my music, can I get it back easily? Would it be painful? If you think loosing it would be painful and recovery hard, back it up.
Do the same for your contacts, your movies, your music sheets (just installed tuxguitar myself :)

I've bought a big external hard disk and backed up anything I consider I can't loose. I'm not scared of erasing my home.

Hope this helps even though it's not what you would like to hear.

Nico

---

### Post by sailthesea on 2009-10-25
+1 to the above
 Then read up on terminal commands
Never use rm -rf unless you are totally sure of what you are doing  (It is actually written in large red letters all over these forums!:))
 Put it down to experience and keep learning I hope you didn't lose too much stuff

---

### Post by fluffman86 on 2009-10-25
Removing your hard drive does not void your warranty.  On a Dell Inspiron 15**, you just unscrew the two little screws in the middle on the bottom, and it slides out.  You can then use something like this:

[http://www.newertech.com/](http://www.newertech.com/)

to plug your laptop hard drive into a desktop and run photorec on it to recover the data.

---

### Post by Radissthor on 2009-10-25
Ok guys thanks for the comforting replies... I'll just start from scratch again, trying to save some files from gmail and whatever... I lost weeks of work of Corpus analysis... hope my boss understands...  and well... I hope this serves as a lesson for all newbies to be carefull with commands...
 
By the way, I took the command from [http://wiki.winehq.org/FAQ#head-3b297df7a5411abe2b8d37fead01a2b8edc21619](http://wiki.winehq.org/FAQ#head-3b297df7a5411abe2b8d37fead01a2b8edc21619) and it said nothing about it being so dangerous, so people from Wine may want to warn people about this.

Cheerios

---

### Post by fluffman86 on 2009-10-25
Well, you can still try running photorec on your current installation.  It won't hurt, it's just less likely to work 100%

---

### Post by ndefontenay on 2009-10-25
Just another tip. Before you apply a command, check what it does:

```
man rm
``` in the terminal will do the trick.

Here ```
rm -rf
``` means remove folders (f) recursively (r) in Home. If you didn't use home and using a root account your fate could have been even worst!

[Here's a linux cheat sheet]("http://www.digilife.be/quickreferences/QRC/The%20One%20Page%20Linux%20Manual.pdf") that should propel you from newbie to someone understanding linux :)

Keep enjoying

Nico

---

### Post by nothingspecial on 2009-10-26
> **Radissthor said:**
>  So following the Wine wiki I typed this in the terminal:

rm -rf $HOME/.wine



What you probably did was put a space between the / and the .

Because of that space - I know, one little space - you told bash to delete your entire home instead of just .wine.

That`s why it says what it says in my sig

---

### Post by 7raTEYdCql on 2009-10-26
In a way, to avoid this, i always try to avoid using absolute paths. If i were you, i would have first cd'd to ~. And then taken .wine of.

Using this method, the problem of a ' ' is removed. And you can avoid this kind of errors.

But the bottom line is, in Linux, when the Terminal replies back beware, don't just shud it away, take a look at it. It isn't one of the Windows Boxes, which keeps giving these kind of things, that you become oblivious to it.

---

### Post by Radissthor on 2009-11-12
Thanks for all the good advices. The lesson is definetly learned :)
 
BTW, Could you recommend a good software to do backups? One that detects new documents and the ones that have been modified and backs those up instead of everything... I downloaded Lucky Backup and it didn't quite work, though it might've been cuz I was using Karmic and nothing works on Karmic. 

I've switched back to Jaunty. So does anyone know of a good backup program?

Thanks again! :D

---

### Post by potatan on 2009-11-12
I use Simple Backup - it's actually quite well featured for a program with that name, and you can configure it in all sorts of ways to do what you want.
Good luck

---

