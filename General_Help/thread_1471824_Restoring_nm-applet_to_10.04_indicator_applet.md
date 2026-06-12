---
title: "Restoring nm-applet to 10.04 indicator applet"
date: 2010-05-03
forum: General Help
---

### Post by TetonsGulf on 2010-05-03
I removed the "indicator applet" from the default gnome panel at the top of the default Lucid desktop. Doing so resulted in me losing the ability to control the sound from the panel, which I value so I put it back.

Once I restored the indicator applet to the panel, the nm-applet went missing. I'm still connecting to my home network with no problem, so the function is there, but the little icon that updates when you're trying to connect, shows signal strength, and other available networks is now missing. This 

I've searched the problem and haven't found any solutions that work, I think because of the new applet integration, but I'm very surprised this hasn't been found by someone yet!

Any ideas on how to bring it back? I know there's a way, I just haven't found it yet.

---

### Post by sean.terrell on 2010-05-03
> **TetonsGulf said:**
> I removed the "indicator applet" from the default gnome panel at the top of the default Lucid desktop. Doing so resulted in me losing the ability to control the sound from the panel, which I value so I put it back.

Once I restored the indicator applet to the panel, the nm-applet went missing. I'm still connecting to my home network with no problem, so the function is there, but the little icon that updates when you're trying to connect, shows signal strength, and other available networks is now missing. This 

I've searched the problem and haven't found any solutions that work, I think because of the new applet integration, but I'm very surprised this hasn't been found by someone yet!

Any ideas on how to bring it back? I know there's a way, I just haven't found it yet.


Did you try adding the notification area to the panel?

---

### Post by g00f on 2010-05-03
I had the same problem.

The above post was spot on. After loosing 1/2 my panel items trying to get rid of the envelope icon I had re-added the "Indicator Applet" but what I also needed to re-add was the "Notification Area" as that's where nm_applet appears. They are two separate things, you need both.






.

---

### Post by TetonsGulf on 2010-05-03
> **sean.terrell said:**
> Did you try adding the notification area to the panel?

Agreed! Very much appreciated, thanks for the tip sean.terrell

---

### Post by lucaa on 2010-05-05
thanks guys, I was just about to try adding all those applets to the panel until one of them will bring battery & network back.

---

### Post by ddreamer on 2010-05-08
AFter adding back notification area, there only appeared 3 short horizontal bar lined up vertically. Network manager icon didn't show up. However, when I clicked around, sometimes the menu of network manager would appear. How strange... ....

---

### Post by pjizz on 2010-05-08
I don't understand these changes.  Apparently no one tested the panels before release?

The Notification Area shows dropbox, keyboard language, the old volume icon, and the nm-applet dialog for network and wireless connections.  the Indicator applet shows rhythmbox, monitor, battery, new volume icon, and messaging.

if you don't have a widescreen monitor, there is hardly room for the me menu, the calendar, the notification area, the indicator applet, and the main menu in the panel.  especially since the indicator applet and notification area are confusing, this is a big problem.  i'm glad i installed lucid on a test machine before taking the jump with my real box

---

### Post by ddreamer on 2010-05-10
> **pjizz said:**
> I don't understand these changes.  Apparently no one tested the panels before release?

The Notification Area shows dropbox, keyboard language, the old volume icon, and the nm-applet dialog for network and wireless connections.  the Indicator applet shows rhythmbox, monitor, battery, new volume icon, and messaging.

if you don't have a widescreen monitor, there is hardly room for the me menu, the calendar, the notification area, the indicator applet, and the main menu in the panel.  especially since the indicator applet and notification area are confusing, this is a big problem.  i'm glad i installed lucid on a test machine before taking the jump with my real box

After unlocking "indicator applet" and "notification area" from the panel, you can move it free in the panel. The nm-applet still remained disappeared. My screen resolution is 1440 x 900. So, that's not a problem. Though I could pass the problem by eliciting pppoe to connect to the internet and wicd to connect wirelessly, I still think it pity to be unable to use the wired and wireless integrated connection provided by nm-applet.

In addition, the setting program for nm-applet is also bad. It always showed "never" behind the connections whatever you edited the connection.

---

### Post by Argentino on 2010-05-12
HI! Good news! I got it back now! HOW?:

I uninstalled the applet from the Software Center, then re install and reboot... BAM! nm-applet is back! 

I really really like nm-applet, makes life super super easy if you are switching back and forth between static ips, or wanting to disconnect from wireless and stay on wired, and so on. Bless those Network Manager devs!

---

### Post by ddreamer on 2010-05-16
> **Argentino said:**
> HI! Good news! I got it back now! HOW?:

I uninstalled the applet from the Software Center, then re install and reboot... BAM! nm-applet is back! 

I really really like nm-applet, makes life super super easy if you are switching back and forth between static ips, or wanting to disconnect from wireless and stay on wired, and so on. Bless those Network Manager devs!

Good for you!! I also had my panel somewhat ruined. The "Chat Button" next to the "Power Button" appeared strange, which was fixed by using your method. However, the nm-applet is still absent. I use "ps aux|grep nm-", which showed "nm-applet --sm-disable". So, the problem not completely solved~~:confused:

---

### Post by Nunu on 2010-05-22
Hi guys

Same thing on my side. I created a launcher on the desktop with command "gksu nm-applet. After reboot the NM icon would flash I would then get a notification that there is wireless networks available and the icon would then drop. using my "Shortcut" it would prompt for a password and the icon jumps back in place. I kinda like the idea of it working like that helps control my Internet access when my note book is at work with me.

---

### Post by rtimai on 2010-05-31
I'm really glad I read this discussion for the clue that the Notification Area applet controlled the nm-applet position, and the Indicator Applet displayed system indicator items: the Volume Control, and Chat-Mail-Broadcast status.

In my case I removed the Notification Area when I should have removed the Indicator Applet, and the Network Manager applet slid over and jammed itself into the upper right corner of the screen. The Help-About-Remove-MOVE-Lock drop-down became unavailable, and I couldn't move the nm-applet back to its rightful position of importance. Re-adding the Notification area just to the left of it fixed the nm-applet position problem. 

((( TIP )))  Right-click on Panel Properties, Background tab. Likely you will see Background None (use system theme.) Temporarily select SOLID COLOR, WHITE, OPAQUE. This will enable you to see elements on the panel that are otherwise invisible, and you can see where are the Notification Area and the Indicator Applet. After you make any needed corrections, you can return the panel to no-background or however you had it.

---

### Post by benji_benji on 2010-07-01
Reinstallation of the indicator packages did nothing. Adding and removing the indicator from the panel did not solve the issue either, however, adding and removing the notification area did fix it.

 I suggest to anyone having this issue is to try removing and re-adding the notification area first before trying anything else.

This issue is not really with the indicator applet but either the nm-applet or the notification applet. They are all separate applets. Maybe because they are beside each other and are themed uniformly, users are confusing them for the same applet.

---

### Post by nadim.chidiac on 2010-07-22
Taken from [https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/577678/comments/1](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/577678/comments/1)



Try this:
 sudo gedit /etc/network/interfaces
 then check that the file has only this 2 lines:
 auto lo
iface lo inet loopback
 Delete all the others then reboot...


This was the only option that worked for me from all those mentioned in this thread and others.

---

### Post by Jior on 2010-08-17
Well, i think my nm-applet crashed (and still doing).
When i log in my account, the applet is there.
Some minutes or even an hour later, the wireless signal indicator disappears and just the wired connection works sometimes. The notification area still there, is just the wireless icon the one whos disappears.
if i run "sudo nm-applet --sm-disable" nothing happens, i need to write it down with out "--sm-disable" and the icon appears again.
Somedays this happens more than once in a session.

Any ideas???

Greets

Jior

---

### Post by rtimai on 2010-08-17
> **Jior said:**
> Well, i think my nm-applet crashed (and still doing).
When i log in my account, the applet is there.
Some minutes or even an hour later, the wireless signal indicator disappears and just the wired connection works sometimes. The notification area still there, is just the wireless icon the one whos disappears.
if i run "sudo nm-applet --sm-disable" nothing happens, i need to write it down with out "--sm-disable" and the icon appears again.
Somedays this happens more than once in a session.

Any ideas???

Greets

Jior
Jior,

Try moving the Notification Area to a less-crowded part of the Panel. I'm wondering if the Network Manager applet is getting crowded out by another icon appearing in that space.

---

### Post by RavisPohan on 2010-08-19
In my case, the package "indicator-network" was not installed or had been uninstalled. Installing it saw it show up in the indicator-applet again.

---

### Post by rtimai on 2010-08-19
RavisPohan, it sounds like you have a slightly different set of tools. NetworkManager Applet 0.8 appears in Notification Area 2.30.2. I can't find a indicator-network package in Synaptic software list, and I have an expanded Repository list. What's going on here?

Added: OK... It's an unsupported extension of the Ayatana Project from their Personal Package Archives.
[https://launchpad.net/~indicator-network-developers/+archive/ppa](https://launchpad.net/~indicator-network-developers/+archive/ppa)

Jior, I noticed that whenever I hot-plugged in my USB drive, my wireless connection got disconnected. It always reconnected automatically about 30 seconds later, however. This stopped happening after I added Disk Mounter to a Panel. This latter applet is completely invisible when I don't have a USB drive plugged in, and appears only when I plug it in. Anyway, I wonder if this behavior is related to your symptoms.

---

### Post by jdorenbush on 2010-08-24
> **RavisPohan said:**
> In my case, the package "indicator-network" was not installed or had been uninstalled. Installing it saw it show up in the indicator-applet again.

Thanks for the heads up on this app. I've installed and setup my static IP through with it and everything appears to be working okay. 

The interface isn't my favorite though -- spacing and alignment is kind of messy, and it looks like the actual applet is spaced a bit too far to the left. But at least this takes care of the problem with the Network Manager not being in the Indicator Applet, so I can't complain too much. :)


...I wonder why the developer didn't use the native network manager software, or at least something that looks similar.

---

### Post by fmurrieta on 2010-09-03
I had apparently the same problem, I tryed everithigng you've suggested with no luck.

I have a bunch of users in this machine.

I've prevoiusly checked the "Available to all users" checkbox for all the wireless networks I use.

After 2 months I've got my problem solved:
 
All I need to do to fix the missing nm-applet was1.- Login as your first user
[INDENT]2.- Go to Edit Network Connections- 
3.- Select your first network
4.- Click the **Edit** button
5.- Unckeck the "**Available to all users**"
6.- Click **Apply**
7.- Repeat for all connections
8.- Repeat for all users
[/INDENT] Hope thi*s can save you* some time!


Fernando Murrieta

---

### Post by fmurrieta on 2010-09-03
I had apparently the same problem, I tried everything you've suggested with no luck.

After 2 months I've got my problem solved:
 
Please read

[http://ubuntuforums.org/showthread.php?p=9800977#post9800977](http://ubuntuforums.org/showthread.php?p=9800977#post9800977)


Hope thi*s can save you* some time!


Fernando Murrieta

---

### Post by Siljrath on 2010-09-06
i also am now missing my nm-applet, just after upgrading to 10.04.

when i attempt to start nm-applet or any of the nm- stuff, i get stuf like this spat back at me in terminal:
```
** (nm-applet:16452): WARNING **: <WARN>  bus_init(): Could not get the system bus.  Make sure the message bus daemon is running!  Message: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused


** (nm-applet:16452): CRITICAL **: nm_remote_settings_system_new: assertion `bus != NULL' failed

** (nm-applet:16452): CRITICAL **: nm_settings_service_export: assertion `priv->bus != NULL' failed

** (nm-applet:16452): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (nm-applet:16452): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSettings service.
  Error: (-1) (unknown)


```

---

### Post by Artyom7 on 2010-09-07
Hello guys!

It seems that i was faced with a similar problem, however, the solutions offered here ( and elsewhere online ) didn't work for me.
I couldn't try some of the solutions, as i had already fixed the problem by the time i found them.
Following is a step by step account of what happened / how it happened and what i did to fix it.

(i run Lucid Lynx 64 bit on a WIPRO laptop)

Problem : Network connection icon disappeared

I noticed this when i restarted the computer using "sudo shutdown -r now" from a terminal window while some programs were still running.

When the computer rebooted, the network icon was gone from the notification area and the sound icon looked kinda weird ( like an outline ), and there was no sound. a few other things seemed strange:
1. even though there was no network icon, my wired connection was active and i could browse the net.
2. running "ifconfig" shows that my eth1 connection is active, and shows all relevant details like netmask, ip address etc etc..
3. rebooting ( again ) brought the sound back.
4. When i tried checking System>Preferences>Network Connections, all the wired connections were missing. I added a new one, but as soon as i checked "available to all users" it disappeared. Same happened with the wireless connections.

Troubleshooting attempt no 1:
reinstalled network manager, reinstalled notification applet, restarted networking services... Result = Failure :(

I looked online for a solution but nothing seemed to describe my problem. Yes i did try removing and adding the notification area applet and the like. That didnt work either.

one solution involved changing /etc/NetworkManager/nm-system-settings.conf file.
    - it suggested editing the line 
[ifupdown]
    managed=false ( change to managed = true )

This didnt work either. In fact, i lost network connectivity completely.

At this point in time i got really fried, so i did the following:

1. Open system monitor
2. Find the pid of NetworkManager
3. in terminal i typed "sudo kill [pid]"

i was in for a shock.. the network connection icon reappeared!!!
However, it was showing a disconnected icon, and there were no wired networks available ( even though the network cable was plugged in ).

i then did a "sudo /etc/init.d/networking restart"

at this point i do not remember what i did next. I think i just rebooted once again ( a habit from the days of windoze ).

Everything went back to being normal except for a few things.

All those connections that kept disappearing suddenly showed up in the connection manager.

a new wired connection showed up caled "ifupdown (eth1)" .
this looks very familiar to the entry in /etc/NetworkManager/nm-system-settings.conf file.

And now to the questions:

1. what is /etc/NetworkManager/nm-system-settings.conf file?  what information is stored there? what is managed / non managed. what is the difference?

2. I spent about 3 hours figuring this out, was there any other way that might have solved my problem quicker?

3. Why did killing the NetworkManager process made the icon reappear?

4. Why would the connection be active when the icon shows it as disconnected? is this a bug?

Please keep in mind that i have started using ubuntu very recently ( hardly been a few months ), and am not fully familiar with all the technical aspects.

Thank you

---

### Post by e.m.fields on 2010-09-24
@Artyom7:

That's a good bunch of questions, I'd like to know the answer to this too.

I'd suggest looking in the Ubuntu Guide: [http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

for information about the networking configurations and how they work. I probably shouldn't put my time into looking into this, but would like to understand this better myself. 

Please post if you find anything out.

---

### Post by MishMich on 2011-03-02
I tried all the suggestions here and elsewhere.  The only think that worked for me was to kill the connection by hard reset - switching the wifi off on and then off again on the laptop.  The network manager comes alive when it is switched off, and then is available to select a new network.  The same thing happens if I lose a WiFi connection.  Logically speaking, this is not surprising, because if booted with a connection, there is no need for a notification, only when losing a connection would something be noteworthy.  However, there is a problem here, because it goes to the networks marked automatic, which makes it difficult to switch networks without switching the wifi interface off and then on again.  I guess that if you made sure all the interfaces are unchecked, then the computer would not automatically connect to anything, and the notification area nm would become available for you to select a network.  I will test this out over the next few days - but it seems to me the best way to ensure the nm appears is for it to need some kind of input - if it needs no input it won't appear.  The problem is it being in the notification area.  It needs to be an applet that can just sit in the panel regardless of whether it needs input or not.  I guess reinstalling might set the automatic flag back to off?

---

### Post by MishMich on 2011-03-02
Tried it out, and yes, setting the flag for automatic connection off, when you boot up, there is no network connection, so the nm applet is visible, and you select the network connection you want.

Mish.

---

### Post by abdusamed on 2011-03-06
i have it disabled doesn't work

---

### Post by chernobila on 2011-03-23
Thank you guys 

as always best forum !!!

---

### Post by nehmesis100 on 2011-10-22
Probably will help this:

1. Click on a panel
2. Select Add to panel
3. Choose Notification Area
4. Click Add

Now the the applet should be visible, if no the problem is somewhere else.

---

### Post by andthen.. on 2011-10-27
This made my nm-applet reappear:

```
gconftool --recursive-unset /apps/panel
```

It restored the default applets to Gnomes notification area. I owe the credit to:
[http://superuser.com/questions/129320/how-do-i-restore-the-default-applets-to-gnomes-notification-area](http://superuser.com/questions/129320/how-do-i-restore-the-default-applets-to-gnomes-notification-area)

---

### Post by Darukur on 2012-05-06
Hi all, in my case the missing nm-applet was fixed by calling:
sudo nm-connection-editor

And removing the wifi connections on the root user.
It seems that nm-applet has not enough permissions in some point trying to open the open the connection edited with root.

---

### Post by jringoot on 2012-06-06
Alas, none of the above helped.

It is linked to the username: 
Changing the userid doesn't help, changing the username (= deleting the user and creating a user with the same userid but a different name) does make the icon reappear.

It is not linked to anything in the users homedir, since I removed it and let it create with the pam.d mkhomedir module.

I suspect something in a binary database in /etc or /var contains this and it is not removed by a apt-get purge network-manager.

It doesn't help to modify or even add as new entry to startup apps in gnome this nm-applet.

For a workaround I have added an icon in the gnome-panel that launches nm-applet.

maybe a script that does "nohup nm-applet &" when the user logs in would be even a better workaround.

Another workaround would be changing the users login name, that worked too, tested.

---

