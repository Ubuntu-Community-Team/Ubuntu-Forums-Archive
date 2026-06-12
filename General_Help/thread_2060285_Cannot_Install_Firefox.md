---
title: "Cannot Install Firefox"
date: 2012-09-19
forum: General Help
---

### Post by PremiumG on 2012-09-19
So I downloaded firefox from the lubuntu app center, and whenever I open it, I receive this message: Your firefox profile cannot be loaded. It may be missing or inaccessable.

I have never installed firefox on this system at all.

How can I install the latest, stable version of FF?

---

### Post by jerrrys on 2012-09-19
That should of worked.  Try this

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get install firefox

What happen?

---

### Post by PremiumG on 2012-09-19
```
brian@brzan:~$ sudo apt-get install firefox
[sudo] password for brian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  firefox-locale-zh-hans
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-globalmenu xul-ext-ubufox
Suggested packages:
  latex-xft-fonts firefox-gnome-support
The following NEW packages will be installed:
  firefox firefox-globalmenu xul-ext-ubufox
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/20.2 MB of archives.
After this operation, 45.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package firefox.
(Reading database ... 134322 files and directories currently installed.)
Unpacking firefox (from .../firefox_15.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Selecting previously unselected package firefox-globalmenu.
Unpacking firefox-globalmenu (from .../firefox-globalmenu_15.0.1+build1-0ubuntu0.12.04.1_amd64.deb) ...
Selecting previously unselected package xul-ext-ubufox.
Unpacking xul-ext-ubufox (from .../xul-ext-ubufox_2.1.1-0ubuntu0.12.04.1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up firefox (15.0.1+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (15.0.1+build1-0ubuntu0.12.04.1) ...
Setting up xul-ext-ubufox (2.1.1-0ubuntu0.12.04.1) ...
brian@brzan:~$ 
```

---

### Post by PremiumG on 2012-09-19
And when I open it now... same thing.

Ubuntu seems too buggy for me, I am thinking about switching to Arch.

---

### Post by QIII on 2012-09-19
In the terminal, run```
firefox -p
``` to see if you can generate a clean profile.

---

### Post by PremiumG on 2012-09-19
> **QIII said:**
> In the terminal, run```
firefox -p
``` to see if that generates a clean profile.

Same message pops up...

---

### Post by QIII on 2012-09-19
In /home/yourusername/.mozilla/firefox, do you have a file (probably two now) that look something like this:

ms6okgdn.default

Yours will not be the same name.

---

### Post by PremiumG on 2012-09-19
> **QIII said:**
> In /home/yourusername/.mozilla/firefox, do you have a file (probably two now) that look something like this:

ms6okgdn.default

Yours will not be the same name.

Actually, there is no folder listed "firefox" in /home/brian/.mozilla/

---

### Post by jerrrys on 2012-09-19
Good call Qlll

Don't know how to do it in lubuntu, but you need to find the "show hidden files" in the menu of your file manager to see the .mozilla folder.  And since this is a new install I would just delete the .mozilla folder and restart firefox.  A new one will be generated.

---

### Post by twipley on 2012-09-19
CTRL-H is often a sure way to toggle between shown and hidden modes, by the way.

---

### Post by PremiumG on 2012-09-19
> **jerrrys said:**
> Good call Qlll

Don't know how to do it in lubuntu, but you need to find the "show hidden files" in the menu of your file manager to see the .mozilla folder.  And since this is a new install I would just delete the .mozilla folder and restart firefox.  A new one will be generated.

It is denying me permission to delete... This is starting to bug me, Ubuntu...

Anyone have better luck with Arch? I hate having to do some special thing just to have temporary permission in my own system.

---

### Post by twipley on 2012-09-19
I have read somewhere: ALT-F2 and running "gksu nautilus" then right-clicking files and changing permissions from there (through root access) -- does that work?

---

### Post by QIII on 2012-09-19
> It is denying me permission to delete... This is starting to bug me, Ubuntu...This is not a problem with Ubuntu.

> Anyone have better luck with Arch? I hate having to do some special thing just to have temporary permission in my own system.Your last post indicates that** *you*** have done something to modify the default permissions of at least that directory in your home directory, not Ubuntu.  Since Warty, I have not experienced a case where Ubuntu just up and changed permissions on my home directory all on its own.  Not in any other Linux distro either.

Have you opened any graphical applications from the terminal, like nautilus, using sudo instead of gksudo?  Have you opened Firefox from the terminal using "sudo firefox"?    I found a clue to what might be your issue [here]("http://ubuntuforums.org/showpost.php?p=12231756&postcount=10").   It seems you have been mucking around with sudo incorrectly, which may  certainly be the source of your permission problems.  It is anyone's  guess at this point what else may have been affected.

"Ubuntu sucks and I'm thinking about taking my ball over to Arch" is not a particularly good way to continue to get help.

Whether you use Ubuntu or Arch is none of my business. Nor is it anyone else's.  Nor is it going to impress anyone.

---

### Post by PremiumG on 2012-09-20
I dont know what half of that stuff means. I installed Lubuntu. I tried to install veetle for chromium, to no avail... I want to install firefox so veetle HD will play (not SD default). 

So I download and install FF from LSC, and when I open it, I get the message I originally posted. Note, there is no FF folder in my .mozilla, even though I installed the program. I even uninstalled it and tried thru the terminal.

---

### Post by PremiumG on 2012-09-20
> **twipley said:**
> I have read somewhere: ALT-F2 and running "gksu nautilus" then right-clicking files and changing permissions from there (through root access) -- does that work?

When I do that, and input my correct password, hit enter... nothing happens. I see the forum I left to run that command.

---

### Post by daslinkard on 2012-09-20
My first question for you is what happens if you try to use the terminal and start FF?  Are you getting this issue when you click on an icon or using the terminal?  Are you trying to run FF as a normal user or as sudo?

---

### Post by PremiumG on 2012-09-20
> **daslinkard said:**
> My first question for you is what happens if you try to use the terminal and start FF?  Are you getting this issue when you click on an icon or using the terminal?  Are you trying to run FF as a normal user or as sudo?

Both, I guess... I dont know anything about linux, so how do I run in terminal

---

### Post by daslinkard on 2012-09-20
Go to your Dash Home and type Terminal.  Select the terminal option that appears.  Then you can use the sudo option to run Firefox such as:

```
sudo firefox
```You may be prompted for your password....let me know if this allows FF to work for you.

---

### Post by PremiumG on 2012-09-20
WOW... it works! :D how can I open it like a normal human being now, as well as install applications on Lubuntu without having to change permission every time I want to open?

---

### Post by PremiumG on 2012-09-20
> **PremiumG said:**
> WOW... it works! :D how can I open it like a normal human being now, as well as install applications on Lubuntu without having to change permission every time I want to open?

Spoke too soon, it is asking me to create a profile, but it wont let me in the default folder it wants... says its not writable

---

### Post by daslinkard on 2012-09-20
Try the following:

First close FF and  then
 
```
sudo chown -R $USER:$USER ~/.mozilla
```

Now try to use the icon and let me know what happens.

---

### Post by PremiumG on 2012-09-20
Works now, without requesting a dang ol profile... WOOT!

Now, how to get Veetle to work? Whenever I install it following the website's instructions, it is almost as if it never installed, because it still only plays in SD, and when i try to make it HD, it does the exact same operation of events where if I never installed it at all.

---

### Post by daslinkard on 2012-09-20
Try this link [here]("http://veetle-ubuntu.blogspot.com/2011/05/how-to-install-veetle-on-ubuntu-11.html") and let me know if this works.  Also don't forget to mark this thread as solved.

---

### Post by PremiumG on 2012-09-20
Nothing happened when I ran in terminal... Just absolutely nothing happened.

---

### Post by daslinkard on 2012-09-21
Mark this thread solved and open another thread for veetle so we can start the progression of getting it fixed too for you.

---

