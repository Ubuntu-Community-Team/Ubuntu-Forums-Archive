---
title: "Customize GDM Login Screen"
date: 2009-11-13
forum: General Help
---

### Post by Merovius on 2009-11-13
I was very unhappy that I could not customize the GDM under Karmic so I set about finding out how to do it "by hand". It turns out it's pretty easy. First you need to find a background image you like and save as it "bg_2560x1600.jpg" I made my image 2560x1600 in size as the original was that size. I then went to /usr/share/images/xsplash and renamed the original "bg_2560x1600.jpg" to "bg-2560x1600.jpg.old" I then placed the file I had created into the xsplash folder in its place. (I used the nautilus script "Rootilus" to do these two steps) 

I logged out and used the following instructions to customize the colors of the login box and bottom task bar to match my image choice.

1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using ALT-F7
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM&#8217;s font, theme and background image.
9. Close the gnome-control-center and login normally.

The image I used was,[ATTACH]136095[/ATTACH] as I like it much better then the new background. I set the colors to a dark combo that I thought went well with it and viola! a login I like much better then the original.

I'd show a screen shot but I have know idea how to do it. :)

Edit: I would do as advised below and save your image in case an update to xsplash/GDM overwrites it.

---

### Post by brandonsh on 2009-11-13
Nice guide! I might use that one day.

Anyone think this should be a sticky?

---

### Post by falconindy on 2009-11-13
Uh, it's far less complicated than that. One command:

```
gksu -u gdm dbus-launch gnome-appearance-properties
```

Make your changes, restart gdm.

---

### Post by ranch hand on 2009-11-13
When you do this you should back up your image in some other folder.  I created /usr/share/images/holding.

The reason is, when they update xsplash of GDM artwork they over write the /usr/share/images/xsplash file leaving you with the same old deal.

---

### Post by Merovius on 2009-11-13
Thanks for the tips. 

Didn't know about the "gksu -u gdm dbus-launch gnome-appearance-properties" command. Will check it out.

I will definitely back up my image in case I need to put it back every so often. hadn't thought of that.

---

### Post by Merovius on 2009-11-13
The "gksu -u gdm dbus-launch gnome-appearance-properties" command is definitely quicker to get to, but I like the other way as I can see it take effect as I do it. Let's me experiment in real time as it were. 

But, whatever floats your boat as long as the end result is what you were after.

---

### Post by Merovius on 2009-11-14
Still experimenting here. One thing though,

gksu -u gdm dbus-launch gnome-appearance-properties

When I use the above command as recommended it always starts the Acceptabilities features and places two (identical) icons in my panel. I have to un-check the option about "Accessibility features can be toggled with keyboard shortcuts" under keyboard preferences. Then I have to log out and in to get rid of the second icon. Otherwise it does what I would expect.

What gives?

TIA

---

### Post by somking95 on 2009-11-14
> **Merovius said:**
> Still experimenting here. One thing though,

gksu -u gdm dbus-launch gnome-appearance-properties

When I use the above command as recommended it always starts the Acceptabilities features and places two (identical) icons in my panel. I have to un-check the option about "Accessibility features can be toggled with keyboard shortcuts" under keyboard preferences. Then I have to log out and in to get rid of the second icon. Otherwise it does what I would expect.

What gives?

TIA

I had the same problem with the accessibility icons. I turned them off but when I log out at the bottom of the screen I have a panel and it has an accessibility icon on it.

---

### Post by somking95 on 2009-11-14
I have tried to uninstall the accessibility technology features but they won't go away. Anyone know how to remove them?

---

### Post by brydonhunter on 2009-11-14
Systems>Preferences>Assistive Technologies
select Keyboard Accessibility
Accessibility Tab
De-select Accessibility Features can be...
close window

---

### Post by Merovius on 2009-11-14
I knew how to turn the setting off. That doesn't get rid of both icons. You have to log out to get rid of both.

The original question was why does the command used to edit the GDM cause these icons to show up in the panel?

---

### Post by somking95 on 2009-11-14
Am I the only one with the accessibility icon on the log in screen? How can I get it off that screen?

---

### Post by falconindy on 2009-11-14
Consider it a "feature" of Gnome 2.28, among other things...

---

### Post by Muscovy on 2009-11-15
Does anyone know where the logo on the gdm (ubuntu circle, white) is? I want to try putting a coloured one with a glow in its place.

---

### Post by Merovius on 2009-11-15
Don't know that yet, but i'd like to.

---

### Post by Muscovy on 2009-11-21
I found the icon, it's in /usr/share/icons/HumanLoginIcons/apps/64 .

---

### Post by Merovius on 2009-11-21
Thanks for the update.

---

### Post by aslam on 2009-11-29
all these shows only how to change the background and some color changes or icon changes but does not support really install a new theme entirely as it was in the jaunty System>>Administration>>Login Window.

Is anybody know how to get rid off this new version of gdm and install the old one instead ie. that comes with jaunty?

I recently installed ubuntu-studio 9.10 alternative it dose not have xsplash folder in /usr/share/images folder, btw its default gdm theme is very bad

---

### Post by Merovius on 2009-11-29
Sorry don't know the answer to that. :neutral:

---

### Post by spiffwalker on 2009-11-29
> **aslam said:**
> 
Is anybody know how to get rid off this new version of gdm and install the old one instead ie. that comes with jaunty?


I would also like to know this.  I liked having to enter my username and password, not clicking on my username and then entering the password. It made it more secure in my opinion.

---

### Post by raktarok on 2009-11-29
See this link, but proceed at your own risk!
[http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html)

---

### Post by somking95 on 2009-11-29
> **raktarok said:**
> See this link, but proceed at your own risk!
[http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html)

cool. who's is brave and nice enough to report back?

---

### Post by slumbergod on 2009-12-01
Well, I am tempted. I might give it a go tomorrow when I have more time. I need to think about it more. I use Xubuntu and the instructions are for Ubuntu so I need to think about whether it will screw things up.

The new log-on is attractive but I dislike the way it is implemented. Disabling the userlist doesn't restore the behaviour from Jaunty though.

[update] the link above for instructions makes reference to a gdm.conf file in the /etc/gdm/ directory but in my Xubuntu it doesn't exist. While I am quite happy hacking away until I get something the way I like it I know very little about the gdm and how it is implemented in Xubuntu Karmic. Anyone else using Karmic tried changing from gdm 2.28 to 2.20?

---

### Post by spiffwalker on 2009-12-01
> **raktarok said:**
> See this link, but proceed at your own risk!
[http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-downgrade-gnome-display-manager-2-28-to-2-20-in-ubuntu-9-10-karmic.html)

I tried it and it worked wonderfully for me! Thanks for the tip! Also for people looking to try it, when it said you can run apt-get install gdm-2.20, you really can't due to dependency problems, so it's best to use synaptic.  Other than that tutorial worked perfectly!:D

---

### Post by slumbergod on 2009-12-02
No one with Xubuntu has tried it? Xubuntu seems to be a slightly different setup.

---

### Post by spiffwalker on 2009-12-02
> **slumbergod said:**
> No one with Xubuntu has tried it? Xubuntu seems to be a slightly different setup.

Well seeing as gdm stands for gnome display manager, and xubuntu uses xfce instead of gnome, I would say this makes perfect sense.  Maybe xdm? Sorry I can't help you further..

---

### Post by slumbergod on 2009-12-02
actually gdm is used in xubuntu for the login. if it is missing a gdm.conf file it is obviously set up differently which is why i was asking

---

### Post by raktarok on 2009-12-02
did you search for it?
```
sudo find / -name "gdm.conf"
```

But you have the new gdm now and I think the current version of gdm does not have that file. I can't find it on my karmic too.

The file is probably provided by the old gdm package, so I would suggest you to just follow the steps, and after you install the old package, there should be a file with that name. 

If you run into problems, you can always remove that package and then install the current version. Good luck!

Edit: Actually, there is a gdm.conf file in karmic too, but not in the place as mentioned in the above link. I just found them:
```
/etc/init/gdm.conf
/etc/dbus-1/system.d/gdm.conf
```
But you are not editing these files, you have to install the old package first!

---

### Post by slumbergod on 2009-12-03
Yes, you are right. The gdm.conf file did turn up after gdm-2.20 was installed. After that things didn't go quite so smoothly.

For Ubuntu users, there are several online posts saying that the next step is to manually edit the gdm.conf file, replacing references to 'usr/bin/X11R6/X' to 'usr/bin/X'. Unfortunately, in Xubuntu the conf file contains no such entries to correct.

I'll keep looking online and see if I can find more documentation on how Xubuntu Jaunty was set up. Until then I guess I am stuck with the new gdm.

---

