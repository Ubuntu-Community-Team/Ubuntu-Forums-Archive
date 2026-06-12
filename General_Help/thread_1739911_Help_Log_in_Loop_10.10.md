---
title: "Help: Log in Loop 10.10"
date: 2011-04-26
forum: General Help
---

### Post by Crimble on 2011-04-26
Hello everyone, 

 I'm super frustrated. After enabling in COMPIZ the option (something like) "enable windows to be drawn in all shape", basically allowing the window to be moved in any shape like a triangle or things like that. I didnt even want this option, I hit "enable" by accident. After, the machine froze, I had to do a hard reboot and now, I can get to the log in screen, choose my name, enter my passsword, and then when I hit enter, the screen flashes a Nvida splashscreen, but then goes back to the log in screen. Please, I am not to versed in Ubuntu, if you have a suggestion, please tell me HOW to show you something or give you a report, step by step , please. Thanks you.

---

### Post by ~Plue on 2011-04-26
i can't recall the exact plugin you're referring to but try disabling it from the failsafe gnome session. it would be available from the drop down list "session:" once you select the username from the login screen

---

### Post by Crimble on 2011-04-26
Thank you for your response, that did not work, I have it "disabled" but to no avail, it was something like "freely transform windows" but that doesnt seem to be the problem. 

when i hit ctrl+alt+1 and get into a tty, I then log in with user name and password as it logs me in it reads:
 
"-bash/home/USER/.profile: line 61: Syntax error near unexpected token '<'

and 

"-bash/home/USER/.profile: line 61: 'as_run_command_terminal_key = <control><alt>t'
 
I can get in to my desktop with "startx" but I dont know what to do from here, this seems to be the only error I see, I just dont know what to do, thanks for your help so much!

---

### Post by ~Plue on 2011-04-26
i don't know how an error in .profile or .bashrc could prevent a graphical login.. however, see if moving/renaming those files along with the .config folder in your home directory fixes it. (if that doesn't work, just revert the changes)

---

### Post by Crimble on 2011-04-26
additional error messages I have found:

(EE) [drm] failed to open device
(EE) failed to initialize GLX extension (Compatible NVIDIA X driver not found)

is this anything?

---

### Post by ~Plue on 2011-04-26
> **Crimble said:**
> additional error messages I have found:

(EE) [drm] failed to open device
(EE) failed to initialize GLX extension (Compatible NVIDIA X driver not found)

is this anything?
This is probably beyond the scope of my knowledge but perhaps disabling and the reactivating the nvidia driver it from system > administration > additional drivers might help if you're using the proprietary ones. 

(sorry that i haven't been of much help so far)

---

### Post by Crimble on 2011-04-26
Thank you so far for all of your help! 

I have tried those and other suggestions and nothing has worked. 

I tried to uninstall al of the third party drivers and then followed this link and I nothing worked for me
[http://www.thinkdigit.com/forum/open-source/136353-wont-login-ubuntu-10-10-login-page-shows-like-loop.html](http://www.thinkdigit.com/forum/open-source/136353-wont-login-ubuntu-10-10-login-page-shows-like-loop.html)

I have the third party all back up, I tried to replace the xorg.conf file with an older version, but that didnt work so i reverted back to the original. 

I'm not sure what to do at this point, I might just have to reinstall. I would hate to do that, but this issue is probally not even from anything I was doing in Compiz config, I know my system also updated so maybe after I had to reboot, something went super wrong :(
This really sucks

---

