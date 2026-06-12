---
title: "Pranks That don't work on Ubuntu"
date: 2011-03-20
forum: General Help
---

### Post by 1chess2u Christian on 2011-03-20
I have made a couple of pranks for Windows before in notepad, but they won't work in Ubuntu, even with wine. Is there anyone that knows of a few practical jokes that I can put onto someone's computer? (I don't want anything that actually screws someone's computer up, I just want someting that I can take off very easy when I want to. :twisted:

---

### Post by polardude1983 on 2011-03-20
Take a picture of someones screen as is, Delete or move all the desktop icons folders and anything else. Then watch them trying to click things but what they are really doing is clicking the wallpaper.

---

### Post by 1chess2u Christian on 2011-03-20
> **polardude1983 said:**
> Take a picture of someones screen as is, Delete or move all the desktop icons folders and anything else. Then watch them trying to click things but what they are really doing is clicking the wallpaper.

Thank you, but that works on Windows too, but I believe that that would be tampering as well. I store things on my desktop for easy reach that I don't store anywhere else, and I would be absolutely ticked if someone deleted my files. :frown:

---

### Post by coldraven on 2011-03-20
There used to be a DOS program that faked a c:\> prompt.
When you typed anything it would alert you to having water in your hard drive, then play washing machine spin noise with some gurgling.
It would then say your drive is dry now and exit.
Maybe you could write a new version.
Maybe you will also lose some friends :D

---

### Post by 1chess2u Christian on 2011-03-21
> **coldraven said:**
> There used to be a DOS program that faked a c:\> prompt.
When you typed anything it would alert you to having water in your hard drive, then play washing machine spin noise with some gurgling.
It would then say your drive is dry now and exit.
Maybe you could write a new version.
Maybe you will also lose some friends :D

That would be unbelievably awesome, but I just don't know how to do that. I would be very grateful if anyone would teach me how to do something like that.;)

---

### Post by TenPlus1 on 2011-03-21
You could always put one of these wallpapers up on the screen to make it look like their lcd screen is cracked or damaged:

[http://www.google.co.uk/images?client=opera&rls=en&q=lcd+cracked+wallpaper](http://www.google.co.uk/images?client=opera&rls=en&q=lcd+cracked+wallpaper)

---

### Post by chavodel8 on 2011-03-21
A simple one is to swap out (make sure you back theirs up) a .bashrc file. Then set up a bunch of aliases in their bashrc file like so:

alias ls='ls /'
alias cd='echo "Directory deleted"'
alias vi='nano'
alias cp='echo "Copied to trash can"'

etc.

---

### Post by nothingspecial on 2011-03-21
```
ssh -X user@ip
export DISPLAY=:0.0
espeak "We are watching you"
espeak "We are logging your every move"
espeak "We know where you are"
```

etc

---

### Post by tredegar on 2011-03-21
> I have made a couple of pranks for Windows before in notepad, but they won't work in Ubuntu

"Pranks" generally don't work with linux.

Because linux's understanding of "security" is very, very different from windows.

I suggest you stop wasting your time.

---

### Post by 1chess2u Christian on 2011-03-22
> **tredegar said:**
> "Pranks" generally don't work with linux.

Because linux's understanding of "security" is very, very different from windows.

I suggest you stop wasting your time.

That is false. You can still make little pranks that you could put onto someone's computer by a flash drive, I'm sure. (there are also the pranks having to do with desktop wallpapers.

---

### Post by tredegar on 2011-03-22
> That is false. You can still make little pranks that you could put onto someone's computer by a flash drive, I'm sure.
Why are you are you so _sure_?

Have you tried it?

Did it work?

If so, please provide an example of this "little prank" that you are so sure works.

Otherwise, please do not express "opinions", but facts, with the evidence to back them up.

Best wishes.

---

### Post by cookiecloud on 2011-03-22
You could try:

[code]
sudo eject /dev/<insertCDromNodeNameHere> && sudo eject -t /dev/<insertCDromNodeNameHere>

:P

---

### Post by cookiecloud on 2011-03-22
> **tredegar said:**
> "Pranks" generally don't work with linux.

Because linux's understanding of "security" is very, very different from windows.

I suggest you stop wasting your time.

:lol: It's just a joke I think :)

---

### Post by jerome1232 on 2011-03-22
> **tredegar said:**
> Why are you are you so _sure_?

Have you tried it?

Did it work?

If so, please provide an example of this "little prank" that you are so sure works.

Otherwise, please do not express "opinions", but facts, with the evidence to back them up.

Best wishes.

Press alt+F2, type "free the fish"

Open a terminal type

```
apt-get install moo

```

These are just easter eggs, but there are simple pranks you can pull on a users account, stop kidding yourself.

open a terminal type
```
PS1="Error: "
```

I'm sure if I spent some time thinking, I could come up with some ingenious/funny tricks to mess with an users account, none of them would require sudo/root privileges.

---

