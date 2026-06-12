---
title: "Upgraded from 11.04 to 11.10...Now I can't get to anything"
date: 2011-10-17
forum: General Help
---

### Post by Nymn on 2011-10-17
All I now have on my desktop are File, Edit, View, Go, Bookmarks and Help in the top left. Compiz seems to be off as there are no animations anymore.

[[IMG]http://img713.imageshack.us/img713/8424/screenshotat20111017233.th.png[/IMG]](http://imageshack.us/photo/my-images/713/screenshotat20111017233.png/)


There are no options for Applications, Places or System, no icon for Firefox (I got it open by clicking on Help and following the online link). This is how my desktop looked before:

[http://files.digitizor.com/wp-content/uploads/2010/10/Workspace-1_001.png](http://files.digitizor.com/wp-content/uploads/2010/10/Workspace-1_001.png)

That's not my desktop, but that's pretty much how it looked. How do I get everything back?:(

---

### Post by oldfred on 2011-10-17
If you move cursor left do you get the programs which is the Unity interface?

Return to Ubuntu Classic Desktop in Ubuntu 11.10
[http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/](http://www.liberiangeek.net/2011/08/return-to-ubuntu-classic-desktop-in-ubuntu-11-10/)
[http://tombuntu.com/index.php/2011/09/11/install-the-classic-desktop-in-ubuntu-11-10/](http://tombuntu.com/index.php/2011/09/11/install-the-classic-desktop-in-ubuntu-11-10/)
How to Fix common Gnome 3 issues on ubuntu 11.04 (Natty)
[http://www.ubuntugeek.com/how-to-fix-common-gnome-3-issues-on-ubuntu-11-04-natty.html](http://www.ubuntugeek.com/how-to-fix-common-gnome-3-issues-on-ubuntu-11-04-natty.html)
[http://ubuntumanual.org/posts/405/gnome-3-and-shell-a-complete-user-guide-part-2](http://ubuntumanual.org/posts/405/gnome-3-and-shell-a-complete-user-guide-part-2)

---

### Post by Nymn on 2011-10-17
No, I tried that. I tried all the options to bring it up that was in the help doc.:(

---

### Post by Nymn on 2011-10-18
Anyone? This really stinks, I don't even have a shutdown option. It's like everything is there, I just don't have an option for selecting them.

---

### Post by oldfred on 2011-10-18
I had that with alpha & beta. Not really fixed for me until final version came out.

If you click on control-alt f2 do get to a terminal?

If so try updates:

#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by Nymn on 2011-10-19
Just tried all that. I did get a command line but after entering in all those commands and rebooting I still have the same thing.:(

---

### Post by james.m on 2011-10-19
Did you try [FONT=Courier New]unity --reset[/FONT] from the terminal?

I had heaps of problems upgrading from 11.04 to 11.10; in the end I realised it was going to be easier to do a clean install 11.10.

---

### Post by Meelad on 2011-10-19
> **Nymn said:**
> Just tried all that. I did get a command line but after entering in all those commands and rebooting I still have the same thing.:(

May be try..

```

sudo apt-get install compiz compizconfig-settings-manager
gconftool-2 --recursive-unset /apps/compiz
unity --reset
unity --replace
sudo reboot

```I'm not sure it will help, but no harm in trying..

---

### Post by collisionystm on 2011-10-19
What kind of video card

---

### Post by Nymn on 2011-10-19
It's a Radeon HD 4350 card. I just tried that unity --reset command, but it stops at Setting Update "run_key" and doesn't go any farther.

---

### Post by james.m on 2011-10-19
Or even, logout from your session (or don't log in, in the first place).

Ctrl-Alt-F1 to a console, then log in there.

Now,
```

$ cd
$ mkdir bak
$ mv .config bak/
$ mv .gnome* bak/
$ mv .gconf bak/
$ sudo reboot

```Wipe out all of your Gnome configuration settings and let them get recreated when you log back in.

---

### Post by Nymn on 2011-10-20
Ok, tried that. Now I have the Ubuntu startup sound and a default wallpaper, but it's still the same. It had me re-install language packs, too.

---

### Post by oldfred on 2011-10-20
I changed to classic, do you want to try that?

Unity info
[http://www.omgubuntu.co.uk/2011/04/how-to-add-folder-quicklists-to-the-home-launcher-in-ubuntu-unity/](http://www.omgubuntu.co.uk/2011/04/how-to-add-folder-quicklists-to-the-home-launcher-in-ubuntu-unity/)
[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)
gnome3 clasic
sudo apt-get install gnome-session-fallback
On login screen click on star and choose

---

### Post by Nymn on 2011-10-20
That seems to have almost fixed it. I have Applications and Places back, but System is still missing. None of the effects are working, either and I can't add anything to the task bar.

---

### Post by oldfred on 2011-10-20
Fallback has no system. They seem to be scattered about in other places.  I was able to drag my Firefox icon into the top panel but have not been able to do much else myself.

---

### Post by Nymn on 2011-10-20
How can I get System back?:-k

---

### Post by oldfred on 2011-10-20
With the update to gnome3 they did away with it. You find settings in various places. Some under your userID top right and some in with applications.

---

### Post by Nymn on 2011-10-22
Ah, yah I found it. How come my Compiz doesn't work anymore? I enabled all the usual settings but they don't show.
It takes longer to open windows in Places, too. I just clicked on Documents and it was almost 10 seconds for it to open whereas before it was pretty much instantaneous.

---

### Post by StevenD on 2011-10-22
> **Nymn said:**
> It's a Radeon HD 4350 card. I just tried that unity --reset command, but it stops at Setting Update "run_key" and doesn't go any farther.

I have the same thing happening. I have tried it twice now and it gets stuck at Setting Update "run_key" both times. It has been that way for the past hour. I thought it might just take a long time like the upgrade last night which took over two hour to complete.

Someone suggested at log on I click on the gear symbol and choose Unity 2D but then I get no menus at the top left of the screen including the help menu.

There certainly isn't much freedom when it comes to how much of my time has been tied up in working with this stuff. All I wanted to do was get the icons in the Launcher down from the BIG default size they are to something a bit smaller. :(

---

### Post by masgeeks on 2011-10-22
In the future you might want to consider doing a clean install.  For all the time you think you will save by upgrading - you really don't.

Voice of long experience here, lol...

Everything will run much faster and be much cleaner and happier if you do a clean install.  I even use a partitioning utility to totally wipe clean the drives before I install an new OS.  I have no issues afterward, except for the normal bugaboos that come with the territory of using something new...

---

### Post by StevenD on 2011-10-22
> **masgeeks said:**
> In the future you might want to consider doing a clean install.  For all the time you think you will save by upgrading - you really don't.

Yeah. I I'm going go with your suggestion. I'm tired of fiddling with this thing. Thanks for helping out.

---

### Post by Nymn on 2011-10-22
> **masgeeks said:**
> In the future you might want to consider doing a clean install.  For all the time you think you will save by upgrading - you really don't.

Voice of long experience here, lol...

Everything will run much faster and be much cleaner and happier if you do a clean install.  I even use a partitioning utility to totally wipe clean the drives before I install an new OS.  I have no issues afterward, except for the normal bugaboos that come with the territory of using something new...

Question on that...Is there a way to do this while keeping all the stuff in your Home directory? It's not a *huge* deal, as all my important files are backed up to an external drive anyway, but still.
Oh, and how do I switch between view methods on Places now? Before I could click above them when I had a window open and choose Tree, History, etc. Now I don't see the option anywhere.
And my Compiz still won't work.:(

---

### Post by Nymn on 2011-10-23
Just turned my PC on after having it off last night and now I'm back to that same desktop with no Applications or Places options.:confused:

---

### Post by Nymn on 2011-10-25
Well, I don't know if I'd classify this as resolved, but I just went ahead with a clean install, so everything is normal now for the most part.:-|

---

### Post by xtremo on 2011-10-25
> **Nymn said:**
> Just turned my PC on after having it off last night 

:):):)

That's one of those US-Brit phrases that doesn't come across *exactly* right in translation.

As for your situation, I ended up going back to 11.04....I just gave up with Unity. Menu bar kept appearing then disappearing for some reason.

---

### Post by Gatemaze on 2011-10-25
> **Nymn said:**
> Question on that...Is there a way to do this while keeping all the stuff in your Home directory? It's not a *huge* deal, as all my important files are backed up to an external drive anyway, but still.


Yes. Use different root and home partitions.

---

### Post by Gatemaze on 2011-10-25
Do you have similar problems with unity2d?

---

