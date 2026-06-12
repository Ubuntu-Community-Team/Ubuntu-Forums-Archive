---
title: "Can't unlock Login Screen Settings on Ubuntu 9.10"
date: 2009-10-31
forum: General Help
---

### Post by TheNerdAL on 2009-10-31
Hey, I want to login into Login Screen Settings to Change the login Screen on Ubuntu 9.10 and it won't like, I constantly clicked it and nothing happened.

It gave me this: "WARNING **: Failed to unlock: The name org.gnome.DisplayManager was not provided by any .service files"

Any help?

---

### Post by mikewhatever on 2009-10-31
I don't think there are any login screens to choose from in 9.10.

---

### Post by TheNerdAL on 2009-10-31
> **mikewhatever said:**
> I don't think there are any login screens to choose from in 9.10.

I want to change it from a site.

---

### Post by cariboo on 2009-10-31
Gdm in Karmic is not configurable, the only thing you can change is auto-login. You'll probably have to wait until someone comes up with a configuration utility.

---

### Post by Raven2k360 on 2009-11-01
> **cariboo907 said:**
> Gdm in Karmic is not configurable, the only thing you can change is auto-login. You'll probably have to wait until someone comes up with a configuration utility.

Speaking of auto-login, I'm having problems.  Just upgraded to Karmic tonight, and for some silly reason I checked the 'auto-login' feature.  I should have known better seeing that I have an encrypted home directory because I had the same issue when I installed Jaunty on my brother's laptop.  Now, it bypasses the log-in screen and gives me a couple of errors, and just hangs.  I think it's trying to boot into a root profile because my wallpaper isn't showing up, but neither are any of the task bars.

The only way I can log into my account is to boot into recovery mode, drop to root shell, then type 'login' and enter my credentials...then type 'startx'.  At that point it asks me for my password for the Gnome keyring (which it never does normally), and if I try and change the login screen settings again, the button for 'log in screen' is selected, not the autologin feature.  But everything is greyed out because it's locked.  When I click the 'unlock' button, nothing happens.

Is there a way I can change the auto-login feature back in root shell?  I know on previous releases you edit the gdm.conf-custom file, but when I tried editing both that and gdm.conf, it said it created a new file.  If anyone knows the answers here, I'd greatly appreciate it.

Thanks,
- Justin

**Edit**
    Nevermind, I figured it out.  Did a little digging in the gdm folder and found that the file name is different.  It is now 'custom.conf' instead of 'gdm.conf-custom'.  Hope this info helps someone else!

---

### Post by TheNerdAL on 2009-11-04
I still need help. :(

---

### Post by dpj23 on 2009-11-06
Making Configuration Changes to Login is limited at best...  I working on writing instructions... should be able to post them this weekend...

---

### Post by Niniel on 2009-11-06
You can change from the default to a login where you have to type your own name (with gconf-edit), but that seems to be about it.

---

### Post by klausner on 2009-11-09
> **Niniel said:**
> You can change from the default to a login where you have to type your own name (with gconf-edit), but that seems to be about it.

*Where* in gconf-editor, please.

---

### Post by danbee on 2009-11-12
To disable the user list on Karmic's login screen do the following:

1. Make sure you're logged out and looking at the login screen.

2. Switch to console 1 (ctrl-alt-f1), and log in as your normal user.

3. Type the following commands:

```
$ export DISPLAY=:0.0
$ sudo -u gdm gconf-editor
```

4. Switch back to GDM (ctrl-alt-f7). You should see gconf-editor.

5. Navigate to 'apps->gdm->simple-greeter' and set 'disable_user_list' to true. Close gconf-editor.

6. Switch back to console 1 and run the following command:

```
$ sudo /etc/init.d/gdm restart
```

Done!

---

### Post by Niniel on 2009-11-14
There is no need to log out.

Just start Applications/System Tools/Configuration Editor (you may have to enable that first via System/Preferences/Main Menu).
Then navigate to apps/gdm/simple-greeter and check "disable_user_list".

---

### Post by klausner on 2009-11-14
> **Niniel said:**
> Just start Applications/System Tools/Configuration Editor (you may have to enable that first via System/Preferences/Main Menu).
Then navigate to apps/gdm/simple-greeter and check "disable_user_list".

Unfortunately, that doesn't seem to have any effect in 9.10. :(

---

### Post by klausner on 2009-11-20
Bump.

---

### Post by jludwig on 2009-11-25
Ran into the same problem trying to setup myth. Same error message "WARNING **: Failed to unlock: The name org.gnome.DisplayManager was not provided by any .service files". I noticed this only occurred when using the Login Screen Settings with kdm as login manager. 

Ran a dpkg-reconfigure gdm, set gdm to default, and then I could unlock and config my user for auto-logon (required for myth after power failures).

I don't have time to cross-post or file bugs (two turkeys to cook!), but here are some other issues I ran into, hopefully google will help index these:

- the Nvidia driver install never ran the nvidia-xconfig script. I could change the settings to get my s-video out working, but they never saved to the X11 config file. Running the aforementioned script first, then the nvidia-settings script was the fix.

- multiple config scripts don't properly ask for privilege escalation. If you run into a problem, try running from a shell with sudo. This also helps see error messages.

- sound was a real pain. For whatever reason something in gnome kept resetting my volume to muted after every reboot. No idea what fixed this.

J

---

### Post by raineater on 2009-11-29
Thanks for this tip.  In my case the login shell for gdm is /bin/false, so "sudo -u gdm gconf-editor" failed.
To solve this, as root, I changed the entry in /etc/passwd from
```
 gdm:x:111:123:Gnome Display Manager:/var/lib/gdm:/bin/false
```
to
```
gdm:x:111:123:Gnome Display Manager:/var/lib/gdm:/bin/bash
```

Now the sudo command worked as described and, when done with the gconf-editor changes, I  reverted the shell for gdm in /etc/passwd back to /bin/false.

The user list at login is replaced with a "Login" button which takes you the user-name entry box.

---

### Post by buck2825 on 2009-11-29
Ubuntu 9.10 32bit  

regardless how I launch the configuration editor my disable_user_list "This key is not writable" 

any help

Thanks

---

### Post by buck2825 on 2009-11-30
bump

---

### Post by hellomoto on 2009-12-09
can i sugest taking a look here [http://lani78.wordpress.com/2009/07/30/gnome-auto-login-in-ubuntu-9-10-karmic-koala-alpha-3/]("http://lani78.wordpress.com/2009/07/30/gnome-auto-login-in-ubuntu-9-10-karmic-koala-alpha-3/")

for users that are unable to use the GUI for gdm setup. 

The link details how to change a GDM config file in order to enable/disable automatic login. 

worked for me. :D

---

### Post by johnmuir on 2009-12-18
> **dpj23 said:**
> Making Configuration Changes to Login is limited at best...  I working on writing instructions... should be able to post them this weekend...

Hi,
Did you get around to posting the instructions anywhere? Please post the location if you did. 
Thanks, john

---

### Post by klausner on 2010-01-23
> **johnmuir said:**
> Hi,
Did you get around to posting the instructions anywhere? Please post the location if you did. 
Thanks, john

Bump.

---

