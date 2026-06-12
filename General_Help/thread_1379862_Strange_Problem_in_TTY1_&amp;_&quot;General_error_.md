---
title: "Strange Problem in TTY1 &amp; &quot;General error mounting filesytems&quot;"
date: 2010-01-13
forum: General Help
---

### Post by Zeniff on 2010-01-13
Hi~

Does anyone know how to copy and paste the output from the TTY?

It would take me forever to go back and forth to retype it all here just to show the other problem I'm having....

Besides that, here's my main problem:

I noticed this more than one time in tty1 (when pressing CTRL+ALT+F1):

> 
General error mounting filesystems
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try
And there's more...but I don't know how to copy and paste from the TTY. It gets really strange after this because it gives me login prompts but seems to think I'm entering commands, and when I try to enter commands it thinks I'm entering usernames... O_o??? Why???

---

### Post by Zeniff on 2010-01-13
Hmmm... well, after my clock reset to UTC suddenly and the admin password stopped working, I decided to reboot. So, unless it logged the output from tty1, I guess it's lost... :sad:
 
Since I couldn't find a way to copy the output before rebooting or see anything in a log, basically the main weird thing happening was this:

It looked like it had a root prompt after the error. Below that, it gave me a login prompt. 

In no particular order, it gave these kinds of errors (seemed random to me and I don't recall what was first):

I tried logging in, but it said "(my username) command not found"
Okay, it wants a command, when I tried entering one, it then prompted for a password.
One time, it seemed to take my username as a login, as well as took my password... but it returned by printing "Password: (my password)" to the screen, and then "bash: (2nd half of my password + error which I forgot, sorry)"

Well, I decided to try pressing CTRL-D, which I didn't know was still an option since it said it would give me a shell....which I already had (so I thought it already did that by itself). Anyway, after I pressed CTRL+D, it said it was mounting all, but I think that's when my clock reset and root/admin password stopped working.

So that's where I am now. Upon reboot it did not have the same error and my clock and password work, but I still don't know what happened.

(By the way, I'm not sure about other times, but I got the original mounting filesystems error today when rebooting because my CD drive wouldn't stop spinning after canceling a simulated Brasero burn operation. Also, one of my internal NTFS partitions wasn't showing up, but after this last reboot without the error, it showed up... Strange...)

---

### Post by Zeniff on 2010-03-17
I never really figured out the rest of the problem, but the minor "copy/paste" tty problem was solved.

Saving the last page of screen output can be done by:
```

sudo screendump N > screendump.txt

```N = tty number whose screen you want to save. Change text file name to anything you need.

From my specific post about it:
[http://ubuntuforums.org/showthread.php?t=1379903](http://ubuntuforums.org/showthread.php?t=1379903)

I still think my computer was completely insane that day... O_O;;;

---

