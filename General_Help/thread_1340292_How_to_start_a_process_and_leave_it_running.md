---
title: "How to start a process and leave it running?"
date: 2009-11-28
forum: General Help
---

### Post by Krupski on 2009-11-28
Hi all,

This is probably simple, but I would like to know the right way to do it.

I have a home file server running Ubuntu 9.04 server 64 bit. It's on 24x7 and mostly idle, so I want to put the CPU to some extra use.

(edit to add): BTW, it's a headless server... just a power cord and a network cable... no keyboard or monitor).

So, I'm running the "Folding@Home" client [([COLOR="Blue"]**LINK**[/COLOR])]("http://folding.stanford.edu/") - FYI.

There is a simple command line to start the client:

```

./fah6 -smp -verbosity 9

```

...but the problem is, if I log into my file server using SSH and start the Folding@Home client, it quits when I exit the SSH session since the "Folding" program is started as a child of the SSH session.

What I would like to do is be able to log into my server, start the Folding client (or stop it) whenever I wish, then exit the SSH session and have the program KEEP running if I started it.

Can anyone tell me how to do this?

Another question... the client writes status information to stdout. If I start the program within an SSH session, of course I see the status on the remote terminal.

If I exit the SSH session and the client is still running, where does it's output go? (since the SSH client is no longer "receiving" from stdout)... ?

I don't want to redirect the output to /dev/null because I might want to watch what's going on for a while.

Any answers will be greatly appreciated.

Thanks!!!

-- Roger

---

### Post by shaggy999 on 2009-11-28
You want to look into 'screen', which is pre-installed on ubuntu by default. It's like a "multiple desktop" program for command line and you can disconnect the program from the terminal by pressing 'ctrl+a d' and the programs continue to run in the background even afterr you disconnect. You can then re-login later and reconnect to a screen session using the 'screen -R' command. You can even set it up so multiple people can connect to the same screen session.

You might also want to look into 'byobu' (previously screen-profiles) which is a frontend full of scripts that really takes screen to the next level.

Definitely read through the man pages for screen. It's got a lot of features.

---

### Post by Krupski on 2009-11-28
> **shaggy999 said:**
> You want to look into 'screen', which is pre-installed on ubuntu by default. It's like a "multiple desktop" program for command line and you can disconnect the program from the terminal by pressing 'ctrl+a d' and the programs continue to run in the background even afterr you disconnect. You can then re-login later and reconnect to a screen session using the 'screen -R' command. You can even set it up so multiple people can connect to the same screen session.

You might also want to look into 'byobu' (previously screen-profiles) which is a frontend full of scripts that really takes screen to the next level.

Definitely read through the man pages for screen. It's got a lot of features.

Thanks... I'll look at it. I never even knew it was there or what it was... but sure enough it's there!  :)

Thanks!

-- Roger

---

### Post by Greenwidth on 2009-11-28
try:

nohup ./fah6 -smp -verbosity 9

---

### Post by retrovertigo on 2009-11-28
Definitely seconded on using screen. I use it daily.

---

### Post by Krupski on 2009-11-28
> **retrovertigo said:**
> Definitely seconded on using screen. I use it daily.

Thank you all for the ideas! And thank you **Greenwidth** for the "nohup" suggestion.

It seems like "screen" is the way to go... because it does something that I failed to think of or ask about... that is it allows me to re-connect to the running process at a later time if I want to examine it's output or shut it down.

Thanks again to all!  [IMG]http://www.gunsnet.net/forums/images/smilies/xyxthumbs.gif[/IMG]


-- Roger

---

