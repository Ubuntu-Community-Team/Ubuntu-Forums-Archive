---
title: "User can't login with the right password"
date: 2009-11-29
forum: General Help
---

### Post by ichliebede on 2009-11-29
Hello people! I've been using linux for a while and this problem never occurred until today. And I've searched some solutions online and tried them out, no use at all.

The problem is:
I can't login on desktop even though I entered the right pssword. After I entered the right password, it seemed to be logging, but then it switched back to the log-in page. Like this, over and over again, just won't let it in. 

My system is:
Ubuntu 9.10 karmic

It still worked normally yesterday, but this afternoon it's like this. I have no idea why. Does anyone know what's wrong? How should I solve it?

According to what I found online, I've tried to remove gdm and re-installed it; failsafeGnome; autoremove to free some space. No use, still the same.

I'd appreciate any help/ideas. Thank you in advance!

---

### Post by Dinodoc on 2009-11-29
What happens if you try and login on command line out of curiousity?  Maybe it will show some error that might help you track down whats going on.

I haven't actually tried yet in ubuntu but Ctrl-Alt-F1 will often go to a command prompt (not sure if it will during gdm). Though i think I have seen on these boards F2 (Usually F1-6 will do command prompt I think and F7 is x).

Won't fix the issue, but might help track down what the issue is.

---

### Post by 23dornot23d on 2009-11-29
{Quote}

I've tried to remove gdm and re-installed it; failsafeGnome; autoremove to free some space. No use, still the same.

I'd appreciate any help/ideas. Thank you in advance!

{Quote}

To do these you need root access ....... 

so can you get to be root user in a terminal .....

if so what happens when you issue the command

startx

Sounds like gdm is failing ..... to load properly ........

apt-get install gdm2.0 

I think is the latest for Karmic ..... you might want to check .....

I had a similar situation a while back and loaded up ...... kdm

to sort it ...... but now run gdm again ok ........

Obviously if you cannot get to root ..... its more serious and a password problem ....

Caps Lock ... is another favourite with passwords ..... did you have it on or off 

when creating your password ........ just a thought ......

---

### Post by Camilia on 2009-12-11
Did you get it solved yet?

I have a thread on what to do if you forget your password[ here]("http://ubuntuforums.org/showthread.php?t=1206233"). Perhaps doing this and changing the password would help.

---

