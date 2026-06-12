---
title: "Changing the GDM Login Screen in Lucid"
date: 2010-05-01
forum: General Help
---

### Post by turvyc on 2010-05-01
Hi all,

Just did a nice new fresh install of Lucid, and I wanted to change the login screen. I've found a few tutorial on how to change the background image, but I want to change the entire thing.

You used to be able to do this through the System > Administration > Login Screen dialog, but now you can't! What can I do?

Thanks for the help!

---

### Post by P4man on 2010-05-01
You could learn how to program and write a themer for the new greeter :)

We dont have it yet, and I'm not sure its being worked on. The old login screen was ditched for the new one to provide better boot speed and "flicker free" experience, but in the process we lost a ton of functionality, like theming.

---

### Post by turvyc on 2010-05-01
I have to say that my boot speed is now quite kick-*** . . . 27 seconds not counting my typing in user name and password! I don't even have an SSD. However, I think that functionality is more important than a few saved seconds. I'm sure eventually someone whose geekitude surpasses mine will figure something out!

---

### Post by WorMzy on 2010-05-01
It's been like this since 9.10, so I would assume that a solution, if in the making, is not fast coming.

It's a pity really, I preferred having to type my username and password to be able to log on.

---

### Post by 3rdalbum on 2010-05-01
> **turvyc said:**
> However, I think that functionality is more important than a few saved seconds.

Functionality is more important also than theming; and the new GDM does things with PAM that you could never do with the old GDM.

You can change the background of the login screen with the latest version of Ubuntu Tweak.

---

### Post by doublewitt on 2010-05-02
Unfortunately, this feature in Ubuntu Tweak does not work for me... after selecting an image file, nothing happens...

---

### Post by doublewitt on 2010-05-02
For the login background image, there must be a file format I'm not familiar with > probably the reason why Ubuntu Tweak does not accept my selections - anyone...?

---

### Post by doublewitt on 2010-05-02
I had some pictures (.jpg) with a space in the name - those didn't work - had to shorten the name and place them in the PICTURES folder - *now it works fine*...

---

### Post by slvr42 on 2010-05-02
Try this

sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

Then logout.  The gnome appearance window will start and let you change the background and themes.  now login and remove the file with unlink or rm

sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

---

### Post by Roasted on 2010-05-02
If you cannot change the login screen of Lucid, can you at least change the appearance of the lock screen window?

---

### Post by slvr42 on 2010-05-03
If you build a custom gdm theme and apply it with the method from above you can sort of change it.  It's not the most elegant solution but it will work.

---

### Post by Vaphell on 2010-05-03
how to force gdm to accept manually entered login/password without any clicking? can it be done? i don't want to see the user list and i want to login without mouse which was trivial up to 9.04.

---

### Post by BrokeMahPC on 2010-05-03
Method I use to change the login screen background:
 It's best to change your image to the resolution of your monitor - use  gimp?
It may be easier to put the background image you wish in  /usr/share/backgrounds first if not already there, doesn't really matter

-log out
-at the log in screen press CTRL+Alt+F1, 
-enter user name and password
-Code:
export DISPLAY=:0.0
-press enter
Code:
-sudo -u gdm gnome-control-center
-press enter, expect errors, 
-when terminal output stops press CTRL+Alt+F8

The Gnome Control Center should appear (it looks exactly the same as  Appearance preferences from the Gnome Desktop, but , it relates to the  login screen in this case.)
In Appearance 
-choose Add and pick a new background, (or browse to one if it's in a  different folder)
-close Gnome Control Center,
-press CTRL+Alt+F1 
-at the terminal cursor type code:
sudo reboot

---

### Post by slvr42 on 2010-05-03
Vaphell Are you talking about doing auto logins?

---

### Post by BrokeMahPC on 2010-05-05
Another method is ubuntu tweak - it has a tab that lets you change the login wallpaper and the logo with a click of a mouse.

---

### Post by Obfuscator on 2010-05-07
> **Vaphell said:**
> how to force gdm to accept manually entered login/password without any clicking? can it be done? i don't want to see the user list and i want to login without mouse which was trivial up to 9.04.

+1. This used to work in 9.10, you could just start typing and a text field would automagically appear. In 10.04 you need to click on 'Other' first. This is believe it or not really a show stopper for me. Can't be that hard to just revert the code from 9.10, the login screens are almost identical...

---

### Post by KlavKalashj on 2010-05-18
> **slvr42 said:**
> Try this

sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

Then logout.  The gnome appearance window will start and let you change the background and themes.  now login and remove the file with unlink or rm

sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

This works fine for me. However, I would like to have shadows for the window, so I went to desktop effects and selected 'normal', and it worked fine, but that setting is not saved, next time I see the screen there is a nice theme, background and font, but no shadows... suggestions?

---

### Post by DuckPenguin on 2010-05-20
To remove the icon-based logon, our system is using the following code as root:

```
su - gdm -s /bin/bash
    $ gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable _  user _ list true
  $ exit
  /etc/init.d/gdm restart

```While we're new to posting on the forums, we're not exactly new on the block.  We know this works to create a uid-based login screen.

A problem we're having is that it generates a button labeled "Log In" that must be clicked before a user can sign in - while that's good security and all, it's actually not good for our system and is delaying deployment of a new system-wide workstation image.  Any hints on how to turn that off?

---

### Post by Michael Schmidt on 2010-05-25
The newest version of Ubuntu Tweak works just fine for changing the background - and it has lots of other neat features.  There are many nice Ubuntu themed background images (wallpapers) at desktop nexus ( [http://www.desktopnexus.com/](http://www.desktopnexus.com/) ).  I downloaded several and copied (sudo cp) them to /usr/share/backgrounds.  Then use Ubuntu Tweak to change to your favorite one.  Select Login Settings option, scroll to the bottom of the window, click "unlock", type in your password (you might have to clsoe the window manually), and then click the background thumbnail.  Works like a top.  Here's a link to instructions on installing Ubuntu Tweak.

[http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html](http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html)

---

### Post by csmith6594 on 2010-05-26
Ugh.  I have been trying to change my gdm login screen for the last 2 hours to no avail.  I have downloaded ubuntu tweak, and I am trying to use my own custom pictures, and of course, nothing as of yet.  I will try to figure this thing out, and will post what has become of my endeavor so hopefully everyone in the ubuntu world will be able to easily change their gdm theme.  Ya know sometimes I miss the easiness of Windows.  Yes I said it!!  Don't ya just hate having to figure things out for yourself?  Ugh.:confused:

---

### Post by philinux on 2010-05-26
Just google gdm2

---

### Post by ttshivers on 2010-05-26
I posted a thread about this question.  [http://ubuntuforums.org/showthread.php?t=1454595](http://ubuntuforums.org/showthread.php?t=1454595)

---

### Post by csmith6594 on 2010-05-26
Whoa-Ho.  Indeed my digital friend, the Linux gods have blessed me this day.  MWAHAHAHA!  GDM2 works just fine.  It takes about 3-5 seconds longer to start the system, BUT it eases my soul.  Thank you very much phil.

---

### Post by rgm3 on 2010-07-08
Installing Ubuntu Tweak worked for me.  Here's how I did it:

1.  Open a terminal
2.  Type the following to add the PPA for Ubuntu Tweak and install it:
```
 sudo add-apt-repository ppa:tualatrix/ppa
 sudo apt-get update
 sudo apt-get install ubuntu-tweak
```
3.  Click Applications -> System Tools -> Ubuntu Tweak
4.  On the left side, click "Login Settings" in the Startup section, then click the "Unlock" button in the lower-right corner of the app.
5.  Click on the background picture icon to change it, press Quit.

---

### Post by kazuya on 2010-10-28
Thanks man for this link to ubuntu tweak.

---

### Post by ivarn on 2010-10-28
So will GDM2 allow gnome-look's gdm themes?
Also, when I install the gdm2 package, what package(s) do I have to remove then?

---

