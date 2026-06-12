---
title: "Help with Vidalia!"
date: 2011-09-05
forum: General Help
---

### Post by samtey on 2011-09-05
Hi all!

I am new to this forum, and also to Linux Ubuntu 10.10! Now, I downloaded Vidalia via command! But when I start it, it gives me this error:
"Vidalia was unable to start Tor. Check your settings to ensure the correct name and location of your Tor executable is specified."

Well, when I go into the settings, it says me it's under /usr/sbin/tor!
What now? I can't find Tor anywhere, where the hell did he install this?

Can you help me?

---

### Post by haqking on 2011-09-05
> **samtey said:**
> Hi all!

I am new to this forum, and also to Linux Ubuntu 10.10! Now, I downloaded Vidalia via command! But when I start it, it gives me this error:
"Vidalia was unable to start Tor. Check your settings to ensure the correct name and location of your Tor executable is specified."

Well, when I go into the settings, it says me it's under /usr/sbin/tor!
What now? I can't find Tor anywhere, where the hell did he install this?

Can you help me?

try starting tor manually:

[I]sudo /etc/init.d/tor start 
sudo /etc/init.d/polipo start[/I]

what messages are returned ?

then check it is running with

[LEFT]*ss -aln | grep 9050*
[/LEFT]

---

### Post by samtey on 2011-09-06
Well, the first two commands I typed, are getting the answer: Command not found!

When I type
 ss -aln *| grep 9050*
[I]

nothing happens, that means it returns and say only like when you start the terminal:
username@pcname
[/I]

---

### Post by haqking on 2011-09-06
> **samtey said:**
> Well, the first two commands I typed, are getting the answer: Command not found!

When I type
 ss -aln *| grep 9050*
[I]

nothing happens, that means it returns and say only like when you start the terminal:
username@pcname
[/I]


I am guessing Tor is not installed then.

See here [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

vidalia is a GUI for tor thats all

---

### Post by samtey on 2011-09-06
Yes, this could be the problem! I only installed Vidalia via terminal!

But say, how to install Tor now? I don't really understand it...

---

### Post by haqking on 2011-09-06
> **samtey said:**
> Yes, this could be the problem! I only installed Vidalia via terminal!

But say, how to install Tor now? I don't really understand it...


I take it you didnt read the link i posted on how to install tor then ? ;-)

It is above

---

### Post by samtey on 2011-09-06
Of course I read it, I meant the description from the site you've given! ;) This I don't understand, could somebody explain it in steps for me?

---

### Post by haqking on 2011-09-06
> **samtey said:**
> Of course I read it, I meant the description from the site you've given! ;) This I don't understand, could somebody explain it in steps for me?


Well here is another step by step then [https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu)

It doesnt get much simpler.

I could type it out again but it is all there, just follow instructions and cut and paste commands.

---

