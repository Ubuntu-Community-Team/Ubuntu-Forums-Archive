---
title: "I cannot see the minimize - restore - close icons on top right of the application"
date: 2010-04-11
forum: General Help
---

### Post by hihihi100 on 2010-04-11
Hi there:

I recently installed via synaptic some packages about netbook to try the new appearance. Having decided that I didnt like it, I chose to revert, by uninstalling those packages...

My problem now is that on every application I execute, the icons that are usually found on top right of the screen (minimize, maximize and close) cannot be seen and, if I want to shut an application down I must do it via control q or control w depending of the application. I mean every application, be it firefox, opening folders on the hard drive, open office...

It may be that there is still a package I must uninstall... If so, please name it

If its not, Id appreciate some tips

cheers

---

### Post by drs305 on 2010-04-11
Do you have the normal title bar, just without the buttons? 

If so, you could check to see if the button layout was altered or removed:
```

gconf-editor /apps/metacity/general/button_layout

```
The default for Karmic is:
> 
menu:minimize,maximize,close


Another thing you could try would be to change to another theme to see if the buttons are restored:
System, Preferences,Appearance: Theme tab. Choose another theme or keep your current theme and try changing to a different window border via "Customize": Window Border tab.

---

### Post by hihihi100 on 2010-04-11
that didnt work:

I tried some other layouts, and none of em showed those needed icons.

Plus, previously, when I clicked on an application's upper bar, it would change its color, to make sure me or any other user knows it has been selected: that doesn't happen anymore

And I executed the command you copied to get what you can see in the attached file

cheers

---

### Post by WinterRain on 2010-04-11
Your problem would indicate there there is a problem with metacity. In synaptic, completely remove metacity, (if it is installed still) then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then reinstall metacity.

---

### Post by Klump on 2010-04-11
What window manager were you using? Have you tried running ```
metacity --replace &
``` in terminal?

---

### Post by hihihi100 on 2010-04-13
Unfortunately, that didnt work either:

I deleted every metacity package I found, applied the pasted command and got:

```
hihihi100@hihihi100-laptop:~$ sudo apt-get clean && sudo apt-get autoremove  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following packages will be REMOVED: 
   gfxboot libclutk-0.2-0 libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgtksourceview-common  
   libgtksourceview1.0-0 liblauncher-0.1-0 python-bugbuddy python-evince python-evolution python-gnomedesktop python-gnomeprint python-gtksourceview python-gtop  
   python-mediaprofiles python-nautilusburn python-totem-plparser python-wnck  
 0 upgraded, 0 newly installed, 21 to remove and 1 not upgraded.  
 After this operation, 10.8MB disk space will be freed.  
 Do you want to continue [Y/n]? y  
 (Reading database ... 670906 files and directories currently installed.)  
 Removing gfxboot ...  
 Removing libclutk-0.2-0 ...  
 Removing python-gtksourceview ...  
 Removing python-gnomeprint ...  
 Removing libgtksourceview1.0-0 ...  
 Removing libgnomeprintui2.2-0 ...  
 Removing libgnomeprint2.2-0 ...  
 Removing libgnomecups1.0-1 ...  
 Removing libgnomeprint2.2-data ...  
 Removing libgnomeprintui2.2-common ...  
 Removing libgtksourceview-common ...  
 Removing liblauncher-0.1-0 ...  
 Removing python-bugbuddy ...  
 Removing python-evince ...  
 Removing python-evolution ...  
 Removing python-gnomedesktop ...  
 Removing python-gtop ...  
 Removing python-mediaprofiles ...  
 Removing python-nautilusburn ...  
 Removing python-totem-plparser ...  
 Removing python-wnck ...  
 Processing triggers for libc-bin ...  
 ldconfig deferred processing now taking place  
 Processing triggers for python-support ...  
 
```Then I reinstalled every metacity package, turned off the laptop, and when I logged in, an error message appeared:

```
OAFIID:GNOME_FastUserSwitchApplet".
```asking me to delete the application, I clicked yes

Is it related?

---

### Post by hihihi100 on 2010-04-13
an update:

things are getting worse: now the shut down icon, the one that should be right next to the calendar section in the upper bar is missing too, Im using an "added to panel" icon instead, not the default one

---

### Post by sandyd on 2010-04-13
> **hihihi100 said:**
> Hi there:

I recently installed via synaptic some packages about netbook to try the new appearance. Having decided that I didnt like it, I chose to revert, by uninstalling those packages...

My problem now is that on every application I execute, the icons that are usually found on top right of the screen (minimize, maximize and close) cannot be seen and, if I want to shut an application down I must do it via control q or control w depending of the application. I mean every application, be it firefox, opening folders on the hard drive, open office...

It may be that there is still a package I must uninstall... If so, please name it

If its not, Id appreciate some tips

cheers
you attempted to upgrade to lucid eh?
reinstall the packages and read [http://techpad.co.uk/content.php?sid=94](http://techpad.co.uk/content.php?sid=94)

---

### Post by dnguyen1963 on 2010-04-13
> **hihihi100 said:**
> Hi there:

I recently installed via synaptic some packages about netbook to try the new appearance. Having decided that I didnt like it, I chose to revert, by uninstalling those packages...

My problem now is that on every application I execute, the icons that are usually found on top right of the screen (minimize, maximize and close) cannot be seen and, if I want to shut an application down I must do it via control q or control w depending of the application. I mean every application, be it firefox, opening folders on the hard drive, open office...

It may be that there is still a package I must uninstall... If so, please name it




If its not, Id appreciate some tips

cheers



Press F11.  This button hides and unhides the top taskbar.  Hope this works for you.

---

### Post by hihihi100 on 2010-04-15
no, i wasnt attempting to upgrade to lucid, Ill wait till the end of the month, I just decided to try ubuntu netbook, and, when I decided I didnt like, reverted, and that's when the problems appeared

---

### Post by wowotiel on 2010-04-15
Sorry for breaking in:
I have the same problem with my 2 laptops.
I am running Ubuntu 9.10.

I have made a clean install and then everything was ok. 
But after a couple days the problem came back on both of the laptops.

If metacity is installed, you can type metacity in the terminal window.
Then the buttons and titlebar came back (as long as you leave this terminal window open).

This is not a real solution because after a restart you must type again metacity in your terminal window.

I think that the problem has something to do with window managers.
In Ubunta there are at least 3  window managers: Gnome window manager;Metacity and Compiz. 

How can I check with window manager I am using and how can I choose another window manager?

ps I am "happy" that I am not the only person with this problem.

---

### Post by wowotiel on 2010-04-15
Here some screenshots:
1) The problem before typing metacity in terminal window: Schermafdruk1.jpg
2) After typing metacity in terminal window: Schermafdruk2.jpg

You can see that in picture 1) there is no title bar on the window and no minimize - restore - close icons
On picture 2) you can see the title bar named: Afbeeldingen - Bestandsbeer (with of course the minimize - restore - close icons)

---

### Post by drs305 on 2010-04-15
wowotiel,

It's been a long time since I've used compiz, but there were instances when the title bar buttons disappeared when using it. The solution (back then) was to install compizconfig-settings-manager and then find the "Effects, Windows Borders" section and make sure it was enabled.

This was long ago, but the main point I wanted to make is that the problem could be caused by compiz, if that is what you are running. When you type "metacity" you are replacing compiz with metacity. You could 'disable' compiz permanently by going to "System, Preferences, Appearance" and selecting "None" in the "Visual Effects" tab if you don't need or want the eye candy provided by compiz or other more advanced window managers.

---

### Post by byStanderone on 2010-04-15
...you are right, lucid is coming, lol, but for the meanwhile :system>preferences>appearance>visual effects ...choose none, hope this helps.

---

### Post by wowotiel on 2010-04-15
With the help of the dutch ubuntu forum I have found a solution for me:
1. open gconf-editor (alt-f2, type gconf-editor)
Find this key: 
```

/desktop/gnome/session/required_components/windowmanager

```Change it in **'compiz'** if 'metacity' or 'gnome-wm'

2. Find the map:
```

~/.local/share/applications
 
```Delete gnome-wm.desktop and/or metacity.desktop (nb make a backup).
There must be a file compiz in this map.

3. Change compiz (nb make a backup) in this map with the compiz of the map: /usr/share/applications
```

$cp /usr/share/applications/compiz.desktop ~/.local/share/applications
$sudo chown yourusername:yourgroupname ~/.local/share/applications/compiz.desktop

```
Restart.
Succes.

---

### Post by hihihi100 on 2010-04-16
I recently upgraded from ext3 to GRUB2 and EXT4. could it be related?

---

### Post by wowotiel on 2010-04-16
> **hihihi100 said:**
> I recently upgraded from ext3 to GRUB2 and EXT4. could it be related?
I really do not know what exactly the cause is.
But I supect that is has something to do with compiz.
I have made a clean install on 2 laptops that I configured with the same software.
After a couple days the problems occurred. 
Maybe your upgrade could have cause troubles with compiz, but then there would be a lot more people with the same problem..........

Ps 
1) If you make a new user loginaccount, can you see the title bar with the minimize - restore - close icons?
2) If you go to system>preferences>appearance>visal effects, stands it on "none" and can you see the title bar with the minimize - restore - close icons again when you set it to normal ? If you do a restart, you cannot see anymore the title bar with the minimize - restore - close icons.

Then you can try the same thing as I did. (nb make backups of the old files and a backup of your home folder)

---

### Post by uRock on 2010-04-16
I have had this problem on my netbook before also. It is a setting, most likely somewhere in Metacity that was changed when you tried the new package. Try going to synaptic and make sure that ubuntu netbook edition is not installed and that ubuntu-desktop is installed. I stopped using UNE and did a clean install of Lucid for testing.

---

### Post by hihihi100 on 2010-04-16
sadly, I made a fresh reinstallation, this wasnt the only problem I had, and I still dont know if it has to do something with EXT4 or not...

now everything works fine... so far

---

### Post by cdude42 on 2010-04-16
this happened to me. turs out compiz actually got uninstalled.
all i had to do was

```
 sudo apt-get install compiz 
```

and i had my window borders back with all the effects too.

---

### Post by asadiqbal on 2010-06-04
[B]There is something Which worked for me...
[/B] 			
 			 			 		   		 		
1. open gconf-editor (alt-f2, type gconf-editor)
Find this key: 
 	Code:
 	/desktop/gnome/session/required_components/windowmanager 
Change  **'gnome-wm****'** if 'metacity' or 'Compiz'
(in my case i had compiz there so i changed it to gnome-wm)
[B][COLOR=Red]
Why? Because when we install Ubuntu the default setting is "Gnome-wm"[/COLOR][/B][COLOR=Black]
after changing it just open anything which has close maximize and minimize button.... i hope this will work for you 
[/COLOR]

---

