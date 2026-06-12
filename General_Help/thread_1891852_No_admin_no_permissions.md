---
title: "No admin/ no permissions"
date: 2011-12-06
forum: General Help
---

### Post by efoster4green on 2011-12-06
Hey Im fairly new to Ubuntu, have had it for about 6 months no problems.. Just upgraded from 11.04 to 11.10 and had been going great.. Not exactly sure what happened but when I turned on my computer today and logged into my user it was frozen.. the side bar was there, the default keyring unlock was there and GNOME do which i had just installed popped up and the mouse could move but i could click nothing on the screen, nor would any keyboard keys work...

Here's where I messed up.. It seemed to me as if the GNOME do was freezing everything up and I wanted to make that not run on start-up. Went into guest and unchecked the run on start-up box, that of course didn't change anything for me (admin), the only user on the computer. after 5 or so restarts with nothing but being frozen, logging in as ubuntu, ubuntu 2d, user defined.. still got nothing.. (actually user defined worked once for me and I grabbed some files, didnt work 2nd time though)

I wanted to make something not popup at start-up so i went into guest, went to users, unlocked that to make my user name (and the only admin) a standard user. Well it worked. No more frozen. But now there is no administrator. The computer asks me for the root password which isn't my password, nor anything I could think of.. I tried to:
evan@evan-badass:~$ sudo apt reset root passwd
[sudo] password for evan: 
evan is not in the sudoers file.  This incident will be reported.

I tried to:
evan@evan-badass:~$ visudo
visudo: /etc/sudoers: Permission denied

because im not an administrator (i think)

Week before finals and I really need some help.. Sorry for the novel

---

### Post by searchfgold6789 on 2011-12-06
Just spit-balling here, but at least to see what interesting thing may happen, you can try booting into Recovery Mode. This should be an option from your boot menu (OS selection) at startup, which, if it doesn't appear normally, should be accessible by pressing and holding down the Shift key at startup. **Once you are in Recovery mode, you can get to a Root Shell Prompt** (or a Root Shell Prompt with Networking). Please let us know what happens.
 - search

---

### Post by fdrake on 2011-12-06
with a live cd or with the suggestion posted before , edit this file "/etc/group" and make sure in the line that says > admin:x:119:user1,user2 make sure you add the name of the user you want to give admin privilegdes .
(you need to run this commands as root)
```

gedit /etc/group

```
save and reboot .

---

### Post by efoster4green on 2011-12-06
Ok I was able to get to the recovery mode root stuff.. Tried gedit /etc/group and got "Cannot open display".. Also there is no folder group folder under etc :/ 

Wouldnt mind reinstalling ubuntu but im pretty sure its going to ask me for the same passwords I dont have

---

### Post by searchfgold6789 on 2011-12-06
The thing is, now that you've gotten to the root prompt, you have root access and can change the root password, or whatever you want to do. Only don't use Gedit because that will not work from the prompt, use Nano:```
nano [file]
```

---

### Post by efoster4green on 2011-12-06
could you tell me the correct code to change the root password plz.. Also my screen resolution is wrong now.. code for that?

Thanks for your quick replys

---

### Post by fdrake on 2011-12-06
@searchfgold6789:
he is not looking to change the root/user password. he is looking to add his user to the sudoers list.

> **efoster4green said:**
> Ok I was able to get to the recovery mode root stuff.. Tried gedit /etc/group and got "Cannot open display".. Also there is no folder group folder under etc :/ 

Wouldnt mind reinstalling ubuntu but im pretty sure its going to ask me for the same passwords I dont have

in case you used the method suggested by the post before me (recovery mode)you have to use another editor:
```

vi /etc/group

```
to edit the file press "i" ; to save and quit press "Esc" then type ":wq" and reboot. --pay attention it's ":"+"w"+"q" 

My previous suggestion was refering to a live-cd boot.

Also you can use another approach :
1-
boot in your sys as your reg user;
type "groups". And you will see a list of names separated by commas, write or copy this list in a file or a piece of paper; add to that list the group "admin" followed by a comma

2-
reboot in recovery mode as root; type:
usermod -G group_list your_username

3-
reboot in your sys as your user and try "sudo" commands

---

