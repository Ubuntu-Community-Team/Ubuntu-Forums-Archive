---
title: "netbook problem after update to 10.10"
date: 2010-10-11
forum: General Help
---

### Post by vivanet on 2010-10-11
hello,

after updating to 10.10 i can login but then i get only the colored wallpaper. no menus, buttons, taskbar at all. nothing.
with the power-button from the netbook i get the menu for shutdown, restart, etc...

please help :-)

saludos
gerrit

---

### Post by jongudm on 2010-10-11
I'm having the same problem.  I have the wallpaper, a black bar across the top of the screen and another down the left side but nothing else.  The menus are active however, it's possible to find the programs blindly but it's not very effective...

I haven't investigated this at all yet, I ran the upgrade very late last night when already tired so when it came up fubar I just went to sleep.  I'll look into it later today, will post what I find.

---

### Post by stevea1210 on 2010-10-11
I'm having the same issue here.  Assus eeepc 900a.  I can get logged in, but then the wallpaper loads, and nothing else will happen.

Also it is 50 / 50 whether or not the trackpad will work on boot.

---

### Post by moon_cho on 2010-10-11
Still no solution. Just another confirmation: same situation here ...

BTW, how to initiate a console session? 
Further linucies have this possibility: Alt-Ctrl-1 etc ...

---

### Post by moon_cho on 2010-10-11
> **moon_cho said:**
> Further linucies have this possibility: Alt-Ctrl-1 etc ...

Meant of course: Alt-Ctrl-F1

---

### Post by stevea1210 on 2010-10-11
I just fixed it on my system.  It appeared unity never actually installed.

If I chose to log into desktop, or UNE 2d (instead of 3d), I would get the old interface of UNE.

I dropped to a shell ctrl -alt - f1 and ran

```
sudo apt-get install unity

```
Then I restarted Xorg.

```
ps -e |grep X

```
Then take the first 4 digit number it resturns and run

```
sudo kill {4 digit number}
```

When I logged back in, I had unity working.

I hope that helps others.

---

### Post by SuperRoach on 2010-10-11
I am getting the same problem - I get my background, and nothing else. The power button or cotnrol + alt + delete on my netbook gives me shutdown/reset options.

This is a 10.04 update on a netbook to 10.04 .

Because this is a machine that also was an upgrade from 9.10, It never had a root password set either, so to get into the console, I'll need to set a root password I assume to try the commands above.

---

### Post by vivanet on 2010-10-11
@stevea1210

1000 times thank you!!! it works now!

---

### Post by narmire on 2010-10-11
@stevea1210

Thanks so much. It now works for me too!

---

### Post by moon_cho on 2010-10-11
> **stevea1210 said:**
> 
I dropped to a shell ctrl -alt - f1 and ran

```
sudo apt-get install unity

```


Thanks, that was it!

---

### Post by stevea1210 on 2010-10-11
Glad I could help out.  I'm just curious why it didn't install during the upgrade.

Not curious enough that I'm going to spend hours pouring through logs though :)

---

### Post by jongudm on 2010-10-11
> **stevea1210 said:**
> 

```
sudo apt-get install unity

```

When I do this I get the message that Unity is already at the newest level.  Nothing changes...

---

### Post by jongudm on 2010-10-11
Having read the opening post again I realise that I'm apparently having an entirely different problem.  I was in a hurry when I read the description and missed the key difference that my taskbar and menubar are present and active, just completely blank to look at rather than completely missing.

Should I put this in a new thread?

---

### Post by SuperRoach on 2010-10-12
Probably would help you more, because there are other topics that have the same problem in them.


How can I set a password to my root account? I can't login to the shell without it. I'm assuming going to recovery console, and typing some kind of command..

*edit* found it: While in the recovery console, I used passwd to set a root pass. 
Then I was able to to the unity update listed above, and it boots! woohoo! 

Sound is borked but thats for another topic.

---

### Post by BigKevOz on 2010-10-12
hmmm...unfortunately installing unity didn't work for me (though it did install - implying that the upgrade didn't install it...). The frustrating thing is it's all find if at the login screen I select Ubuntu Desktop Edition, it's just not the best interface to use on a netbook. The machine I have is a Asus eeepc 1005HA-H. On another forum, it was suggested I install fglrx - tried that too but no difference.

I STAND CORRECTED... after removing fglrx, it all seems to work now.

---

### Post by schenckel on 2010-10-13
hello guys!

i'm just wondering if any of you encountered a similar problem:
after upgrading to 10.10 and manually installing unity, it works quite well, but with one issue: where usually the wallpaper image or whatever would be, i'm actually seeing the 10.04 UNR interface(which still works)....... any ideas on that??

---

### Post by YuriBCN on 2010-10-22
GREAT! Thanks for the pointer to install unity. That WAS it (no need for anything else).

Am dumbfounded, however, that since it is required to upgrade from the old 10.04 Netbook desktop to the new 10.10 one, that it isn't installed automatically! Imagine how grim it is for newbies who might not have any idea of how to deal with it or would have a hard time finding out! Not good for evangelising!

---

### Post by YuriBCN on 2010-10-22
> **schenckel said:**
> hello guys!

i'm just wondering if any of you encountered a similar problem:
after upgrading to 10.10 and manually installing unity, it works quite well, but with one issue: where usually the wallpaper image or whatever would be, i'm actually seeing the 10.04 UNR interface(which still works)....... any ideas on that??

Might be that you started a session in 2D when trying to sort the problem. That's what I had to do. The system remembers the options from your last login, so check bottom of your login screen for options.

---

### Post by dcstar on 2010-11-01
> **stevea1210 said:**
> Glad I could help out.  I'm just curious why it didn't install during the upgrade.
.........

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/614088](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/614088)

---

