---
title: "Customizing Ubuntu 12.04.1"
date: 2012-09-28
forum: General Help
---

### Post by newhere_m on 2012-09-28
I finally upgraded to ubuntu 12.04.1 from 10.04 LTS. Now I need some help regarding customizing the same. There are lots of changes in this version.

1. In the log in screen there is option for guest session which requires no password. How do I disable/remove this guest option?

2. By default the application launcher is vertical, placed to the left edge of terminal. Can I make it horizontal, at the bottom position? How do I do that?

3. Is it possible to change the login screen? I would like to replace the current one with something I prefer, may be some picture file or even some wallpaper already given in 12.04.1

4. How do I include more applications of my choice on the application launcher bar (currently at left, vertical)? I feel, the previous version was a lot user friendly where I could search the options myself and add new items to launch bar (eg, I had calculator, network log in and out options etc in the launcher.) Here I have not yet been able to figure out how to get those options in the first place.

5. If I keep the mouse on the launch bar and left/right/middle click, nothing happens (no options are displayed). Does this mean my mouse is incopatible with 12.04.1?  What to about this?

Sorry for asking so many questions at a time (obviously due to my lack of experience with linux). Hope at least some suggestions will be made. Thanks.

---

### Post by carl4926 on 2012-09-28
2. In the system settings > appearance 
you can set the launcher size position and hidden properties

4. search in the dash and drag apps to the launcher

---

### Post by sir.sargento on 2012-09-28
Hello there.. I think I may be able to help with some of these questions.

#1 - Goto 'System Settings' > 'User Accounts' .. This should list all accounts on your install and let you delete/disable/add accounts.

#2 - I am not sure that you would be able to move the Unity bar to the bottom. As far as I know you are stuck with it on the left of your screen... I could be wrong about this.

#3 - You could use a different login manager that allows you to play with your login screen a bit more. By default I believe 12.04 is using LightDM. There are others like gdm, slim, etc... But you may want to google more into that before doing so.

#4 - Another way to add items to the launcher is when you open an application you will see the icon in your unity launcher. You can simply right click this icon and click 'Pin Application' (Not sure of exact wording at the moment as I'm in gnome shell. But it will read as 'Pin something' haha)

#5 - Depends on the launcher Icon you are clicking on.. Say you decided to right click the 'FireFox' launcher icon it would give you options of 'Open in new tab', 'Close Application', etc.. Some launchers just may not have extra options.

Also I reccomend you download 'MyUnity' and/or 'Ubuntu Tweak' from the Ubuntu software center.. This are programs that will let you easily tweak some setting for your ubuntu launcher.

Hope this helps and if I'm wrong about something somebody please let him/her know. I am just a noob and trying to help out.

Tony

---

### Post by HiImTye on 2012-09-28
> 1. In the log in screen there is option for guest session which requires no password. How do I disable/remove this guest option?
```
sudo sh -c 'echo allow-guest=false >> /etc/lightdm/lightdm.conf'
```

> 2. By default the application launcher is vertical, placed to the left edge of terminal. Can I make it horizontal, at the bottom position? How do I do that?
you would need to switch from Unity to another desktop environment (such as Gnome Classic, or LXDE), as Unity is a plugin to Compiz and that option doesn't exist.

> 3. Is it possible to change the login screen? I would like to replace the current one with something I prefer, may be some picture file or even some wallpaper already given in 12.04.1
the background of lightdm changes as the user changes his. if you want the background to change, change your wallpaper.

> 4. How do I include more applications of my choice on the application launcher bar (currently at left, vertical)? I feel, the previous version was a lot user friendly where I could search the options myself and add new items to launch bar (eg, I had calculator, network log in and out options etc in the launcher.) Here I have not yet been able to figure out how to get those options in the first place.
I believe you would right click and choose 'add to bar' but I use Gnome Shell so I'm not positive. I would try either in the application lens (searching for an application) or by right clicking an opened program.

---

### Post by newhere_m on 2012-09-28
If I install lxde (sudo apt-get install lxde) in default ubuntu 12.04.1, what will happen to its support? Will I have to upgrade as soon as new version of lxde is released? I did not understand one statement regarding lubuntu in the page [http://en.wikipedia.org/wiki/Lubuntu](http://en.wikipedia.org/wiki/Lubuntu) i.e., "Current version. Unlike Ubuntu this is not a long term support release." (please search for this on that page) What is meant here?

---

### Post by HiImTye on 2012-09-28
Long Term Support (LTS) releases are 5 years, where regular releases are 2 (or 3, I can't remember)
you can just add LXDE to ubuntu by:
```
sudo apt-get install lxde
```rather than installing an entirely different distro (Lubuntu)

there are other options as well, such as KDE and Gnome Shell

---

### Post by newhere_m on 2012-09-29
That is precisely what I intended. I have the default ubuntu 12.04.1 and I want to install lxde so I need to use the command:
```

sudo apt-get install lxde

```
I hope this will not replace precise pangolin by lubuntu. Can some body please confirm?

My question was in case I install lxde, will I have to keep reinstalling new versions of lxde? Is it different from LTS version of ubuntu in nature? If there is some analogue of LTS in case of lxde, I would prefer to install that.

---

### Post by newhere_m on 2012-09-29
One more problem with default ubuntu 12.04.1 is that the OS looks for default network connection at the time of booting. In fact I have set network connection so far after logging in. I connect the modem after logging in because of the way it is arranged along with the telephone. But precise pangolin assumes that the modem and network connection is ready at boot time and unnecessarily delays appearance of log in screen. How can I change this behavior?  

Another query: if I change from current desktop to lxde, can there be conflict with any/some programs (e.g., xfig, latex, gimp, some mathematical programs like gnuplot, c++ compiler etc) if changes in configuration of network or some other are done?

---

### Post by spaceshipguy on 2012-09-29
> **sir.sargento said:**
> #4 - Another way to add items to the launcher is when you open an application you will see the icon in your unity launcher. You can simply right click this icon and click 'Pin Application' (Not sure of exact wording at the moment as I'm in gnome shell. But it will read as 'Pin something' haha)

This probably isn't working for you because of your mouse issues. Once your mouse is sorted, customizing the launch bar is real easy.

---

