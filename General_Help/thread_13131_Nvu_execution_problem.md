---
title: "Nvu execution problem"
date: 2005-01-29
forum: General Help
---

### Post by carlc on 2005-01-29
I just installed Nvu. I can execute it from the terminal by typing "sudo /opt/nvu-0.70/nvu". However, I created a link on the gnome menu to start Nvu with this command, "/opt/nvu-0.70/nvu", and when I click on it, Nvu starts to execute but does not get past the "Chose User Profile Menu". On that menu, the only thing that works is the exit button. The start Nvu button does nothing. If I click "create a profile", it does not let me save a profile and displays a file access denied error.

I am not sure what to do from here. Any help would be greatly appreciated!

---

### Post by Yukonjack on 2005-01-29
[QUOTE=carlc]I just installed Nvu. I can execute it from the terminal by typing "sudo /opt/nvu-0.70/nvu". However, I created a link on the gnome menu to start Nvu with this command, "/opt/nvu-0.70/nvu", and when I click on it, Nvu starts to execute but does not get past the "Chose User Profile Menu". On that menu, the only thing that works is the exit button. The start Nvu button does nothing. If I click "create a profile", it does not let me save a profile and displays a file access denied error.
I am not sure what to do from here. Any help would be greatly appreciated![/QUOTE]

Nvu 0.70 don't work I have tried it also on Ubuntu with no go same as you. Get NVU 0.60 it works good on Ubuntu.

---

### Post by carlc on 2005-01-29
Did you have the same problem? It will work for me if I execute it from the command line but will not work if I execute it from my start menu. The problem that I get is when it brings up the initial "Chose User Profile Menu". It does not bring this up when I excecute from the command line but does when I execute from the start menu.

---

### Post by Yukonjack on 2005-01-29
It didn't work in the cl for me all it did was loading extentions data resources for a while than it stop and nothing. 
All I could get from the menu was the profile screen.

---

### Post by carlc on 2005-01-29
I changed the user permissions for the user profile file, so I now I can create a user profile when the "Chose User Profile" menu appears. However, the button to run nvu still does nothing. I hate to give up here because as I stated earlier, I can run nvu if I start it from the terminal because it skips the "Chose User Profile" menu.

---

### Post by oseb on 2005-01-29
[QUOTE=carlc]I just installed Nvu. I can execute it from the terminal by typing "sudo /opt/nvu-0.70/nvu". However, I created a link on the gnome menu to start Nvu with this command, "/opt/nvu-0.70/nvu", and when I click on it, Nvu starts to execute but does not get past the "Chose User Profile Menu". On that menu, the only thing that works is the exit button. The start Nvu button does nothing. If I click "create a profile", it does not let me save a profile and displays a file access denied error.

I am not sure what to do from here. Any help would be greatly appreciated![/QUOTE]

I was installed my $HOME account directory. it's work fine.
but /opt/nuv... wasn't work.

---

### Post by Yukonjack on 2005-01-29
Interesting  :rolleyes:

---

### Post by morgon on 2005-01-30
to carlc...

you only have to run nvu with "[COLOR=DarkOrange]_sudo_[/COLOR] /opt/nvu..." when you set the command for the launcher

i hope this will help you ;)

---

### Post by carlc on 2005-01-30
I still can not get it to work and to beat it all, I can not figure out how to uninstall it. Since it was a manual install, apt-get and synaptic do not seem to work and I have also tried removing it as a deb package (dpkg -r .....) which does not seem to work either. How can I get rid of it?

---

### Post by darkcoder on 2005-02-04
haven't test nvu with Ubuntu yet, but it requires to run as root for the first time.

Try this:
1. Remove your .nvu folder on your home directory
2. Run nvu ( or at least nvu -register)  as root.
3. Run nvu as normal user.

---

### Post by carlc on 2005-02-04
I gave that I try and still when I try to run the program as a regular user, the "chose user profile" window pops up. From this window, all I can do is create a user profile and exit the window. But no matter what I do, I can not start nvu as a regular user because I can not get past this window. What I would like to do is keep this window from appearing.

---

### Post by darkcoder on 2005-02-06
you are using the nvu dep package provided on nvu.com, or compiling yourself.  I'm new to debian based distro and my knowledge in deb packaging is **zero**, but I've been mantaining an Arch package since V0.60, and can help you with the compile process.

---

### Post by kassetra on 2005-02-07
carlc: here's what I did to make it 0.70 work for me:

in order to find out what your "group" is for your home directory, do this on the command line:
```
ls -l
```

The first column in the result it spits out are the permissions, the second column is the hardlink count, the third column is your username and the fourth column (from the left) is your group... with that knowlege do this following command: (replace username with your username and group with your group)

on the command line:
```
sudo chown -R username:group .nvu
```

enter your password, and then run your Nvu launcher.  :)

---

### Post by neville_lobo on 2005-02-07
[QUOTE=darkcoder]haven't test nvu with Ubuntu yet, but it requires to run as root for the first time.

Try this:
1. Remove your .nvu folder on your home directory
2. Run nvu ( or at least nvu -register)  as root.
3. Run nvu as normal user.[/QUOTE]


WORKED FOR ME!
 =D>

---

### Post by carlc on 2005-02-07
Kassetra, Thanks, it works!

---

### Post by darkcoder on 2005-02-09
[QUOTE=oseb]I was installed my $HOME account directory. it's work fine.
but /opt/nuv... wasn't work.[/QUOTE]

When 1st executed no matter the user, Nvu tryies to register some extensions and its theme, and that's the reason it fail to load if stored on /opt/nvu since a user do not have priviledge on that folder.

After that, at first user execution, Nvu tryies to open the directory where it resides in read & write mode to access the extensions & themes available.  Since users cannot modify files in /opt/ it ends with the different problems like loop errors from console, Site Manager crash among others.  This one usually happens on the first execution when no .nvu folder exists on the home dir.

---

### Post by darkcoder on 2005-02-09
Only thinking on installing a package with the lib of gcc 2.9x make me sick.

I got some documentation on deb packaging, but it will take me some time to read it.  But anyone who is to the task can check my work on arch.  The patches are standard (some of them from fedora) and try to made a deb package from the info and files I have **_[Nvu 0.80 package on Arch](http://bbs.archlinux.org/viewtopic.php?t=9083)_**

The link gives you also info on the problem you are getting, and the workarounds.

---

### Post by Yukonjack on 2005-02-09
Thanks for the info darkcoder don't know why they make it so bloody hard for no reason, a little more planning from nvu would make things a lot better instead of doing the loop to loop. "2.9x hehehe"

---

