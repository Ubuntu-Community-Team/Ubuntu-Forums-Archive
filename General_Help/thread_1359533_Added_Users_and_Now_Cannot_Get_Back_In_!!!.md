---
title: "Added Users and Now Cannot Get Back In !!!"
date: 2009-12-19
forum: General Help
---

### Post by hotrodrodney on 2009-12-19
I have installed ubuntu 9.10 and am loving it.  The problem is that I had created users for my wife and kids to try to weed them off of windows and now it will not let me get logged back in.  The login screen flashes up with my user "rodney-desktop" and says I think "Invalid user" or something to that extent. It will then go away, try again and just keep flashing the same message over and over and there seems to be nothing I can do to get me logged in.

I have a lot of files and programs on there now so i don't want to go and just do a re-install.  What can I do to fix this and get back in?

Thanks in advance for the help.

---

### Post by Chesamo on 2009-12-19
When you boot up, hit Escape to open up the GRUB menu when it says "GRUB loading..." Try "Ubuntu failsafe".

---

### Post by hotrodrodney on 2009-12-19
I don't see the fail safe boot anywhere.  Tried hitting escape a few times but nothing happened.  It's a dual boot system if that helps anything.

---

### Post by hachre on 2009-12-19
> **hotrodrodney said:**
> I don't see the fail safe boot anywhere.  Tried hitting escape a few times but nothing happened.  It's a dual boot system if that helps anything.

How do you normally select the other OS when it's a dual boot system?

---

### Post by Chesamo on 2009-12-19
I mean... sorry, not failsafe. I mean "Recovery Console". One of the options in there is "Root Shell". You should be able to modify accounts from there.

[http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)

---

### Post by hotrodrodney on 2009-12-19
Oh thank you, I was able to go in there followed the link you sent me and deleted the users causing the problems.  Thanks again.

---

