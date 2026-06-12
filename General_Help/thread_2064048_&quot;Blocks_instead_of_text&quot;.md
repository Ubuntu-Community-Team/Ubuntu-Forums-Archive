---
title: "&quot;Blocks instead of text&quot;"
date: 2012-09-28
forum: General Help
---

### Post by amnell on 2012-09-28
Hi there, this will be my first post after about 1-2 years of reading. And yes i know, not the best topic ;)

The reason for my post is that i have runt into some problem that i cannot find the solution to. I shall try to describe the problem as well as i can and i hope to solve this asap.

So what happens is that a run ubuntu 10.10 and windows 7 dualboot. When the computers starts grub comes up and gives me the changes to pick an OS, if i don’t pick one, ubuntu will start after a few seconds. 
So today while i was rebooting to go into windows instead of pressing - arrow down- to go down and pick w7 i pressed -arrow right- witch lead to that ubuntu started **and here is the problem**
When i get into ubuntu, where there is supposed to be text, there are "blocks" instead, there is not one single char that i can see ore make sense of, also no program will start although the terminal runs (with no chars) .
When it come to this I am clueless about what to do, I have searched for an answer for a while, but cant find anything that helps. My best guess is that there is something wrong with the charset, but I don’t know what to do about it..
Not the best description, so I will attach 2 pictures of the screen (sorry for the quality of them)

---

### Post by lechien73 on 2012-09-28
Hi and welcome to the forums.

It sounds like a font issue. I've heard of it being solved before by opening a terminal and typing:

```
sudo apt-get install --reinstall ttf-ubuntu-font-family
```

then:

```
fc-cache -f -v
```

Of course you won't be able to see what you're typing, so maybe just try and copy the text carefully :)

Hope this helps!

---

### Post by cortman on 2012-09-28
Really strange- maybe try reinstalling the default fonts? Drop to tty2 (Ctrl+Alt+F2) login, and run

```
sudo apt-get install --reinstall ttf-ubuntu-font-family
```

Then rebuild font info files by running

```
fc-cache -f -v
```

EDIT: LOL ninja'd by lechien73

---

### Post by amnell on 2012-09-28
Cheers for the answers guys.. Sadly this did not work. The reinstalls seems to be working and running in the terminal (as i cant see much of it) but after that it's still the same, even after reboot..

I am trying to work it from the beginning, what went wrong when i hit the -> instead of down.. Sounds silly, but the computer has been running great for 2 years, so that keystroke seems to be the bad guy in my world.

---

### Post by amnell on 2012-09-28
So after messing around abit more and loads of searching for an answer, by luck i found one!

[http://ubuntuforums.org/showpost.php?p=10299987&postcount=15](http://ubuntuforums.org/showpost.php?p=10299987&postcount=15)

"Try removing your ~/.fontconfig folder, or the contents of. Then reconfigure:"
```
sudo dpkg-reconfigure fontconfig
sudo fc-cache -f -v
```

Cheers for the help and cheers to lidex for the solution..

What the problem was, i do not know.. Kind of buggs me out.

---

