---
title: "SOS - System freezes on startup"
date: 2009-12-11
forum: General Help
---

### Post by gnomeout on 2009-12-11
[SOLVED] - My mouse was messing up, even though it would move and click things it still was somehow messed, I think possibly from my second mouse that is crappier and came with my keyboard, but its off all the time in a drawer. They must have been competing cause it would not allow me to click new windows! anyway i unplugged my main mouse and changed the usb port for my keyboard/other mouse and they both worked. turned off my crappy mouse and plugged my good one back in to a new port. and presto, it works. super effing lame that it took this long to figure out. 

Hey,

EDIT: This is possibly and GDM issue, see my most recent post for details!!!

I just turned on my computer this morning and it was running perfectly fine. The update manager popped up and installed a series of KDE updates. After that things were weird. My mouse was acting up. whenever I grabbed my chrome window to move it, the window would leap about the screen so that the cursor would always end up over the same point in the window. Then I could move it... ok. But this was weird behavior so i restarted. Now my system is just destroyed.

Whenever it turns on, it runs everything just fine and i can enter my password for my keyring on startup and everything no problem. I can even click on messages in my thunderbird window. What I cannot do is click on any other windows or bring anything else to focus(and the thunderbird window isnt even in focus when i can click it). I cant move or select anything, not even menus. Killing thunderbird or anything else does not solve the issue, I just cant click on things, but it still clearly registers my clicking as demonstrated by the thunderbird window. 

so WTF just happened?!?!?!?!?!?!?1

---

### Post by earthpigg on 2009-12-11
have you tried disabling compiz, or logging into any other window manager / desktop enviornment you may have installed?

that isn't a solution of course, but it could help is narrow it down depending on the answer.

also, are any of your partitions now (as a result of the updates) over ~90-95% full? random things start breaking when Linux partitions get over 95% full. (that is the price we pay for not needing to defrag)

to find out:
```

df -Th
```

if your / partition is over 95% full, a quick and easy fix (if, and ***only if*** you have reliable and fast interenet) is to run this command:

```
sudo apt-get clean
```

the run 'df' again to see how full things are.

---

### Post by gnomeout on 2009-12-11
Thanks for the response.

I just checked and my core filesystem has 5Gb free, so I dont think that is my issue. since that is 25% of my core partition. My home folder is on a separate partition with over 100Gb free. And I am currently in my windows partition with plenty of free space too. 

I was almost sure that would be it too! I had the same problem over the summer on my laptop and that was my exact issue, and very similar symptoms. 

My system automatically logs in and I can't click anything to log out and I could not find the terminal command(apparently this is not what the "logout" command is for). So I was not able to try loging in under KDE instead of gnome. 

Also, I tried to run metacity via "metacity --replace" and I got this error:

window manager error: Unable to open Xdisplay

I then tried running "compiz --replace" just for the heck of it, and it also gave me an error. but it was much more verbose. But it had the same general gist. 

checking for xgl: xvinfo: Unable to open display not present. 

then it logged everything in the very long logfile which I attached. 

This seems to be an issue...... thoughts??

Other info: ctrl+alt+backspace does nothing, but crtl+alt+del will bring up the shut down menu.... interesting.

Also, I would like to get this working TODAY since I have an essay due at midnight :S.

---

### Post by earthpigg on 2009-12-11
> **gnomeout said:**
> 
Also, I would like to get this working TODAY since I have an essay due at midnight :S.

time to prioritize. write it in your windows install, or from a live cd (you can pull your half-finished essay off the ubuntu partition using the live cd).

the solutions you tried are all i personally have to offer... if it never breaks for me, i am never forced to learn to fix it, ya know? :\

---

### Post by gnomeout on 2009-12-11
Yeah, I've been working on it in windows, but still I was hoping for an easy fix. 

I have made more progress though.

Turns out I cant run compiz/metacity from the alt+f2 screen, which is what I was using. But I managed to run it in the normal screen and nothing changes, so its not compiz/metacity issues.

Then I manages to figure out to run "/etc/init.d/gdm restart" to hopefully let me log back in under kde or something. but when I did that it recommended running just "gdm restart" which I did as sudo and it told me:

failed to acquire org.gnome.displaymanager  
failed to acquire name; bailing out

so I tried running the original init.d command as root and it... "worked" sorta. the screen flickered a bunch, but when I went to the normal f7 screen(I had run this from alt+f2) everything went black and I could not get back. So I think I can narrow it down to a gdm issue... maybe... who knows???

Most likely gdm...
Still looking for help.

kthxbye.

---

### Post by gnomeout on 2009-12-11
bump... even if i get this essay out of the way I still have lots of work and would rather not clean install.

---

### Post by gnomeout on 2009-12-12
SOLVED. see edit in first post.

---

### Post by wgodoy80 on 2009-12-12
If it's SOLVED give us the solution or a link to it. There is nothing on you EDIT part on how t solve it. Thanks!

---

