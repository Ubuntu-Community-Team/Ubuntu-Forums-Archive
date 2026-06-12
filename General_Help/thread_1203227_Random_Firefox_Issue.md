---
title: "Random Firefox Issue"
date: 2009-07-03
forum: General Help
---

### Post by Sankou on 2009-07-03
When I try to open my firefox web browser, the 'starting firefox' thing comes up and it says it's loading. Then it just stops. Firefox won't start up at all. It's really annoying. I'm fairly new to Ubuntu so I'm running into a lot a issues, but I think it may be a permissions error because when I type 'sudo firefox' it starts up. None of the shortcuts work and neither does clicking the file directly.... so how do I change the permissions? if thats the issue....

---

### Post by Sankou on 2009-07-03
Anyone know what's going on here?

---

### Post by Sankou on 2009-07-03
I checked the permissions firefox. This says that the owner, group, and other users have full read, write, and execute permissions. I tried to change it so that groups and other users don't have write permissions with the command 'chmod go-w firefox' but it won't change when I do the ls -l command... It also shows up differently when I right click it and select properties. :(

root@zombie-laptop:/usr/bin# ls -l firefox
lrwxrwxrwx 1 root root 11 2009-07-03 03:34 firefox -> firefox-3.0

---

### Post by akakingess on 2009-07-03
what does the log say when you type firefox from within the terminal? And am I to understand that if you type "sudo firefox" that it launches and runs just fine?  If that is the case I would start by turning off/uninstalling all of the extensions and/or plugins, maybe even one at a time to see if you can find if one in particular is causing the problem.

akakingess

Actually, try launching it this way and let us know what happens:

```
 firefox -safe-mode
```

---

### Post by smartbei on 2009-07-03
This happens to me sometimes, usually after an upate to firefox. My solution is to kill all running instances of firefox - 
```

pkill -x firefox

```
After which I can usually use firefox as usual.

---

### Post by Sankou on 2009-07-03
'firefox -safe-mode'  does nothing. Sudo firefox -safe-mode boots firefox in safe mode. From there I chose the option to disable all extras in firefox. It still won't run normally though. It does nothing without elevating the permission with sudo. I even tried to change permissions and ownership manually, nothing work so I set it back to default. I also tried 'pkill' it gets me nowhere. I'm about to try logging in a root to see if it will run normally there.... this is a very confusing occourance....

---

### Post by akakingess on 2009-07-03
[http://www.techsupportforum.com/alternative-computing/linux-support/142916-k-ubuntu-firefox-only-runs-sudo.html](http://www.techsupportforum.com/alternative-computing/linux-support/142916-k-ubuntu-firefox-only-runs-sudo.html)
I found this link that was on another forum with the same issue, I believe the end fix was that the profile folder ( .mozilla) was set to owned by root and after the user chowned that folder back to themselves it worked for them.  Hope this helps.

akakingess

---

### Post by Sankou on 2009-07-03
It runs normally when I'm logged in as root and when I type 'sudo -i' or 'sudo -s' first. I tired to switch my user to the root group, but that didn't work. I also tried changing the ownership of firefox to my user. 

Solution:
I just made a small script that runs in the terminal

Echo Starting Firefox
sudo -i firefox


Then I made the firefox shortcut link to my file. This runs firefox without having to have a terminal open as well. It's a temporary fix, but it's working for now. I'd still like a different/better solution, but I've got nothing.

---

### Post by akakingess on 2009-07-03
So the solution that worked on that other forum did not work for you?

akakingess

Just remember that the folder they (in the other forum) changed from root ownership was a hidden folder (hit CTRL+H to view hidden files/folders) so maybe there is a way to fix your issue without having to use a script (although I like your ingenuity!). I was just trying to get to the root of the problem rather than just working with a work-around (no pun intended).

---

### Post by Sankou on 2009-07-03
Yes, it worked great! Thanks a ton! I just posted the other method before I had a chance to try the other forum. The other forum was extremely helpful! The key was the .mozilla file mentioned in the other forum. My problem was that I was changing files in /usr/lib related to firefox and mozilla. As in turns out, the folder .mozilla is invisible but in the /home/{your user name}/ directory. I found it with 'locate .mozilla'

This was the final fix:
cd /home/{your user name}
sudo chown -HR {your user name} .mozilla

Thanks for the help everyone!

---

### Post by akakingess on 2009-07-03
Happy surfing!!! Glad to hear everything worked out!!!!

akakingess

---

