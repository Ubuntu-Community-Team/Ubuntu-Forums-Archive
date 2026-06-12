---
title: "Fire fox crashes"
date: 2009-07-07
forum: General Help
---

### Post by mitchewr on 2009-07-07
Hey I have a problem.  I just installed ubuntu 9.04 on my sister's computer and it runs fine.  The only problem is that after first went to "youtube" and tried to watch a video, I had to install the flash player plugin.  Well I installed it and all that, but after that any time I try to watch a video, say on youtube, or try to go to a site that (I assume) is utilizing heavy flash player plugins, firefox will close itself.  I can't even go to like yahoo and stuff.  I've tried to remove flashplayer and re-install it; I've removed firefox and re-installed it multiple times. . . also, if I try to go to the "preferences" in firefox, it will close on it's own.  And I tried to find out what flash player plugins are installed in firefox by typing "about:plugins" in the url box and it closes itself again.  And of course, I've tried to just restart the computer, but to no avail.  

I am truly at a loss as what could be the problem.  I run ubuntu 9.04 on my own laptop, and have never had any kind of problem like this at all.  

Any suggestions or help you can offer, I will greatly appreciate it.

---

### Post by lovinglinux on 2009-07-07
I don't know which version of Firefox you are using, but Firefox 3.5 has a bug that crashes it when viewing YouTube on fullscreen. Nevertheless, by your description, it seems to be a profile corruption problem. Try to create a new profile and check if it exhibits the same issue.

For information on how to create/backup profiles and how to optimize and troubleshoot Firefox visit the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567).

BTW, re-installing Firefox probably won't do any good.

---

### Post by Megrimn on 2009-07-07
you could also try this thread:
**Comprehensive Multimedia & Video Howto**
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by lovinglinux on 2009-07-07
> **Megrimn said:**
> you could also try this thread:
**Comprehensive Multimedia & Video Howto**
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

That is an excellent multimedia tutorial, it solves most of my codec issues. Nevertheless, since the OP is having similar issues when opening the Firefox Preferences, than it's unlikely to be a multimedia issue.

---

### Post by moster on 2009-07-07
This help me.

Find your browser script in the same area, somewhere in /usr/lib/yourbrowser; (edit: other possible locations are like /usr/local/lib/firefox-3.5/firefox or /opt/firefox/firefox);
then add as 2nd (NOT 1st) line:

```
export LD_PRELOAD=/usr/lib/libGL.so.1
```

If that not work look at original thread here

[http://ubuntuforums.org/showthread.php?p=7487421]("http://ubuntuforums.org/showthread.php?p=7487421")

---

### Post by lovinglinux on 2009-07-07
> **moster said:**
> This help me.

Find your browser script in the same area, somewhere in /usr/lib/yourbrowser; (edit: other possible locations are like /usr/local/lib/firefox-3.5/firefox or /opt/firefox/firefox);
then add as 2nd (NOT 1st) line:

```
export LD_PRELOAD=/usr/lib/libGL.so.1
```

If that not work look at original thread here

[http://ubuntuforums.org/showthread.php?p=7487421]("http://ubuntuforums.org/showthread.php?p=7487421")

Yep. That solved the flash fullscreen issue for me too. I didn't mentioned the solution, because I believe that is not the main problem, since the OP is having the same issues while viewing Firefox Preferences.

---

### Post by moster on 2009-07-07
> **lovinglinux said:**
> Yep. That solved the flash fullscreen issue for me too. I didn't mentioned the solution, because I believe that is not the main problem, since the OP is having the same issues while viewing Firefox Preferences.

Yes... I was asking myself why you did not tell him right away. Ok... :)

It is somehow strange bug. I dont know is it connected only with ubuntu or with other distros as well. It seems to me that yesterday updated firofox came and update some files and that same problem come up again. Shiretoko stay same version 3.5.1 Pre. That is not changed.

---

### Post by lovinglinux on 2009-07-07
> **moster said:**
> Yes... I was asking myself why you did not tell him right away. Ok... :)

It is somehow strange bug. I dont know is it connected only with ubuntu or with other distros as well. It seems to me that yesterday updated firofox came and update some files and that same problem come up again. Shiretoko stay same version 3.5.1 Pre. That is not changed.

Do you mean the file with the fix didn't changed with the update, but the problem came back? Well, it won't affect me because I have compiled Firefox myself and it's waaaaayyyy much better :)

---

### Post by moster on 2009-07-07
OMG, it starting to happening to me too. Just click on random flash video. Crash!

Yesterday I installed some updates. Maybe they mock up something..

---

### Post by lovinglinux on 2009-07-07
> **moster said:**
> OMG, it starting to happening to me too. Just click on random flash video. Crash!

Yesterday I installed some updates. Maybe they mock up something..

Just reapply the fix posted by moster.

---

### Post by mitchewr on 2009-07-07
Yea, well it's not just crashing when I try to watch videos at full screen. . . it's crashing when I try to go to any site that uses flash plugins.  Be it youtube, yahoo, bestbuy, etc.  And like I said, it wont open the "preferences" for firefox either.

So should I do what "moster" posted, or is it some other problem?  B/c his solution seemed to be aimed at fixing a problem of firefox crashing when you try to watch it full screen.  Is the cause of mine and his problem the same then?  I guess I'm still not sure what I should do.

---

### Post by lovinglinux on 2009-07-07
> **mitchewr said:**
> Yea, well it's not just crashing when I try to watch videos at full screen. . . it's crashing when I try to go to any site that uses flash plugins.  Be it youtube, yahoo, bestbuy, etc.  And like I said, it wont open the "preferences" for firefox either.

So should I do what "moster" posted, or is it some other problem?  B/c his solution seemed to be aimed at fixing a problem of firefox crashing when you try to watch it full screen.  Is the cause of mine and his problem the same then?  I guess I'm still not sure what I should do.

No. I think it's not the same issue, otherwise it wouldn't be crashing when opening the Preferences. That's why I didn't suggested the "moster" solution in the second post.

Just to make sure it's not a profile issue, create a new firefox profile and test if it works, then we will no if it is a profile issue or not, then we can try to pinpoint the culprit.

To create a new profile, close Firefox and run the command below on a terminal [see footnote] 

```
firefox -P
```

This will launch the Profile Manager, from where you create and start a new profile.

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

---

### Post by mitchewr on 2009-07-17
Quote:
                                                                      Originally Posted by **mitchewr**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=7576713#post7576713")                 
                 "[I]Yea, well it's not just crashing when I try to watch videos at full screen. . . it's crashing when I try to go to any site that uses flash plugins. Be it youtube, yahoo, bestbuy, etc. And like I said, it wont open the "preferences" for firefox either.

So should I do what "moster" posted, or is it some other problem? B/c his solution seemed to be aimed at fixing a problem of firefox crashing when you try to watch it full screen. Is the cause of mine and his problem the same then? I guess I'm still not sure what I should do.[/I]"
                                 
(Solution) "No. I think it's not the same issue, otherwise it wouldn't be crashing when opening the Preferences. That's why I didn't suggested the "moster" solution in the second post.

Just to make sure it's not a profile issue, create a new firefox profile and test if it works, then we will no if it is a profile issue or not, then we can try to pinpoint the culprit.

To create a new profile, close Firefox and run the command below on a terminal [see footnote] 

     Code:
     firefox -P 
This will launch the Profile Manager, from where you create and start a new profile." (end of solution)


(Start of new thread) Well this is from a previous thread I had started when I first had this problem, and the above is the last post of that thread.  

I tried to create a new profile, but that didn't solve anything.  Firefox still crashes when I try to open it.  Will I have to totally reinstall ubuntu, or will that not solve anything either?

Could really use some help here, haha.

---

### Post by mitchewr on 2009-07-21
I could still use a little help here. . . any suggestions?

---

### Post by philcamlin on 2009-07-21
sudo apt-get purge firefox

sudo apt-get install firefox

does tat help 

and get the icedtea plugin it seems to work better

---

### Post by mitchewr on 2009-07-29
no that doesn't help either. . . i dont know what else to do.  If no one else can think of something, then I think I'll just try and reinstall ubuntu.  

Hopefully it doesn't come to that.  Any more suggestions anyone?  haha, this problem is a real pain.

---

### Post by mitchewr on 2009-08-06
Is there anything else I can do???  The laptop is a hp and it has nvidea (or whatever) graphics card.  It's only a couple of years old, so i dont know what the problem could be.

---

### Post by y-lee on 2009-08-06
Start Firefox from a terminal and then crash it by going to a flash web site and post whatever error messages firefox gives in the terminal here.

---

### Post by martinbaselier on 2009-08-06
You would need to pinpoint the cause of the problem. You have completely removed firefox and all its settings (purge) and reinstalled it. That means cause of the problem is probably elsewhere. Still, firefox is the only application with problems. 

Did you follow the multimedia guide, mentioned in an earlier post? This will at least make sure only the adobe flashplugin is installed and not the open source one. This will prevent conflicts if you installed them both. 

Have you tried another browser, like opera for example to see if it works better. (go to their website for it.) Or you could try firefox 3.5:
**sudo apt-get install firefox-3.5**
It will appear as shiretoko in the menu.

---

