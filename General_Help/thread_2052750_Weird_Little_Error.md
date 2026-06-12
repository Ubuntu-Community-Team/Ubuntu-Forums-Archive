---
title: "Weird Little Error"
date: 2012-09-03
forum: General Help
---

### Post by SantaFe on 2012-09-03
Okay, for some reason Xubuntu 12.04 LTS has been having the slightly annoying habit of randomly popping up a box with the following message:

> Enter password to unlock your login keyring

The login keyring did not get unlocked when you logged into your computer.

Password: [********]
  It will happen once in a long while I'm on the computer and other times 2 or 3 in a row with a short interval in between then nothing.

And it doesn't seem to matter if I enter my password, or just hit cancel.  Tried checking in the Session And Startup/Application Autostart & no mention of any Login Keyring there.

Just wondering why it's been doing this the last couple of weeks.  It's not one of those urgent "Gotta be fixed right away" problems, because all I do is click cancel and it doesn't happen often enough to be more than a slight annoyance.  

But it would be nice to see if anyone else is having the same thing happen & perchance find out how to get my Xfce to remember that darned key ring.  Unless Frodo managed to throw IT into Mt. Doom as well? :lolflag:

---

### Post by 73ckn797 on 2012-09-03
Are you booting straight into Xubuntu without having to enter a password? I would set it so that you have to enter a password on login. You did not say whether that was the case.

---

### Post by SantaFe on 2012-09-03
> **73ckn797 said:**
> Are you booting straight into Xubuntu without having to enter a password? I would set it so that you have to enter a password on login. You did not say whether that was the case.Whoops, forgot that.;)  Yes I use a password to login.  And it seems to be accepted without any problems.  And when I use a terminal & sudo something the password works, as well as when I run Synaptic.  And I looked in .config/autostart & nothing there.

---

### Post by 73ckn797 on 2012-09-03
> **SantaFe said:**
> Whoops, forgot that.;)  Yes I use a password to login.  And it seems to be accepted without any problems.  And when I use a terminal & sudo something the password works, as well as when I run Synaptic.  And I looked in .config/autostart & nothing there.

May have to take the plunge into Mt. Doom.

I do not use Xubuntu so I am not familiar with any issues. If I find something I will pass it along.

Have you searched using: [http://www.googlubuntu.com/](http://www.googlubuntu.com/) ?

---

### Post by SantaFe on 2012-09-04
Thanks for the link. ;)  Turns out it's NOT just me after all.  Finally found this post: [http://www.mentby.com/Group/xubuntu-users/password-keyring-doesnt-get-unlocked-upon-login.html](http://www.mentby.com/Group/xubuntu-users/password-keyring-doesnt-get-unlocked-upon-login.html) (the post by Jody B Allen) that talked about this problem so I tried it.  Funny thing is, on my system, there IS no gnome-keyring-pkcs11.desktop file in /etc/xdg/autostart/.  So I looked on a second system I have that had Xubuntu 12.04 (that doesn't have this problem) and it doesn't have it either.  

So I checked my brothers Xubuntu 11.04 box, same thing.  But I did notice there was a file called GPG Password Agent.desktop (on all 3 installs) and when I peeked inside it with Leafpad, it mentioned Gnome Keyring.  So I found the line OnlyShowIn=GNOME;Unity; and changed it to OnlyShowIn=GNOME;Unity;XFCE;

So far no popups.  But now it's got me to wondering was that file changed at some point or am I missing gnome-keyring-pkcs11.desktop somehow and it's supposed to be there?  Funny though I couldn't find it on 3 different Xubuntu installs that had the GNOME Keyring package installed.

Oh well, gonna give it a couple of days & if it still hasn't started back up, I'll mark it **Solved**!  

Thanks!

---

### Post by SantaFe on 2012-09-04
Okay, I'm a Dolt!  

It started doing it again.  And as I'm wondering why it's happening, I decide to play around on my desktop that also has Xubuntu 12.04 which isn't having this problem.  I'm looking in Settings Manager/Session & Startup, looking at the Application Autostart list on this machine when I suddenly notice two entries I Didn't have on the laptop 1)Certificate And Key Storage (GNOME Keyring: PKCS #11 Component) and 2) Secret Storage Service (GNOME Keyring: Secret Service)

Plus the two files Certificate and Key Storage.desktop & Secret Storage Service.desktop were missing in /etc/xdg/autostart also.  So I simply copied the ones from the desktop 12.04 to my portable HD & then opened a terminal & sudo'ed Thunar and copied the files over to /etc/xdg/autostart & rebooted.

Bet you're gonna say Yea it worked!  Well..... nope, it got to the login window, I picked Xfce & entered my password and     Back to the login window.  Hmmm... so I log into Lxde which works.  Use Thunar to look at the autostart folder & wonder Why do both of those files have a red circle with a white X in it?  Hmmm and why do both files permissions say Root/NONE/NONE instead of Root/Read Only/Read Only?  

It's time for SUDO Man!  open terminal, typed sudo Thunar entered password went to /etc/xdg/autostart and edited both files to match all the others in the folder.  Rebooted.

Okay NOW you can say Yea it worked!  Booted into Xfce, and now both items are in my autostart list.  And it's been up for 6 hours & still no missing login.

Who would of thought my laptop would Need Secret Service Protection? :D

---

