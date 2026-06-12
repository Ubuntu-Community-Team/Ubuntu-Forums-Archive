---
title: "GUI doesn't load after start-up"
date: 2010-01-02
forum: General Help
---

### Post by resisthegemony on 2010-01-02
I've just switched from XP to Ubuntu 9.1 on a relatively old computer (6-9 years?) yesterday, and everything worked like a dream. I've used my computer twice today and nothing seemed to be going wrong...but then came the problem. I haven't toggled with the settings too much since I'm still very new to Ubuntu, but whenever I log in with my password, the GUI doesn't automatically start up. I get the terminal in the right left-hand corner instead, and none of the fixes I've found so far have worked. :( I usually get some variant of an error message or my hostname doesn't exist. 

I've tried: 

startx
sudo apt-get install xorg 
apt-get update 
sudo apt-get install xserver-xorg 
sudo dpkg-reconfigure xserver-xorg 
sudo nano/etc/apt/sources.list 

...all to no avail. Help please :)

---

### Post by MelDJ on 2010-01-02
what happens when you type startx?
try sudo gnome-desktop

---

### Post by jwatne on 2010-01-02
Do you have an /etc/X11/xorg.conf file?  Sometimes, when I have encountered graphics problems, it has been helpful to remove it and have Ubuntu default to autodetecting the appropriate settings.  If you do have such a file, you may wish to try the following:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
sudo rm /etc/X11/xorg.conf
sudo startx

```

Hope this helps; good luck!

---

### Post by resisthegemony on 2010-01-02
Thanks for all of the quick replies! All of your support really is amazing :) 
 
 @MelDJ: When I tried sudo gnome-desktop, I got this: 

```

``` sudo: unable to resolve host Crystal's computer 

Could the problem be the fact that the computer name has an apostrophe in it? I haven't been *really* toggling the settings but I remember I changed the hostname since I didn't want my computer to be named 'resist' for the rest of its life...I consulted the forums to see how to do it but aesthetics in this instance was probably a stupid concern. ](*,)

@jwatne: I think the thing I just mentioned might be the source, too :-/ because the first thing I get when I type "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak" is this: 

```

``` sudo: unable to resolve host Crystal's computer

It then asks me for my password, then says the following: 

```

``` sudo: cp/etc/X11/xorg.conf: command not found

For the second one, "sudo rm /etc/X11/xorg.conf," though, it gives me this: 

```

``` sudo: unable to resolve host Crystal's computer
```

``` rum: cannot remove `/etc/X11/xorg.conf': No such file or directory 

The really funky one is "startx"...this is what I get: 

```

``` hostname: Unknown host
```

``` xauth: (argv):1: bad display name "Crystal's" in "list" command
```

``` xauth: (stdin):1: bad display name "Crystal's" in "add" command 
```

``` X: user not authorized to run the X server, aborting. 
```

``` xauth: (argv):1: bad display name "Crystal's" in "remove" command 

I think I made a huge mistake. :( Reboot?

---

### Post by jwatne on 2010-01-02
Aha!  Yes; that apostrophe will cause problems.  Basically, it looks like an unmatched quotation mark to Linux.

The wikipedia article on hostnames has a useful section on [valid hostname characters]("http://en.wikipedia.org/wiki/Hostname#Restrictions_on_valid_host_names"): the characters A through Z (case-insensitive), the numbers 0 through 9, and the hyphen (-). You will probably want to make sure the first character is a letter, and you cannot use spaces or any punctuation other than the hyphen.

There is a tutorial on how to change the hostname [here]("http://ubuntuforums.org/showthread.php?t=774029").  Although, as I looked through information on various sites, I saw mention that, if you have this sort of problem with the hostname, you can't sudo -- which you need to do in order to get this to work.  I don't know if there is a better way to do it, but what I would probably do is boot off an ubuntu installation CD (the "try without installing" option, or whatever the wording is to that effect), and browse the hard drive to edit ***its*** copy of /etc/hosts (not the /etc/hosts on the LiveCD).

Good luck!

---

### Post by resisthegemony on 2010-01-02
ah, thanks so much! :)

---

### Post by jwatne on 2010-01-02
Oh, and just as clarification, if booting off an ubuntu installation CD, the files to edit won't appear in /etc, but in the etc subdirectory of the folder representing the hard drive on which you have installed ubuntu.  You should be able to find it by selecting the "Places" top menu item and selecting the correct drive icon, in the second section, somewhere under the "Computer" icon, then find that drive's etc directory. You should be able to right-click on the icons for the appropriate files, Choose "Open with...", then "gedit".

Good luck!

---

### Post by resisthegemony on 2010-01-02
@jwatne: Thanks, everything is now working perfectly! :)

---

### Post by jwatne on 2010-01-03
You're welcome.  Scanning the forums has helped me out with several problems, so I am glad to have my turn to help.

---

