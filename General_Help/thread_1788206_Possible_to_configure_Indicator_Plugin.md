---
title: "Possible to configure Indicator Plugin?"
date: 2011-06-22
forum: General Help
---

### Post by trumad on 2011-06-22
The indicator plugin (part of the default panel) is great - I can configure wifi and audio from it.

The only problem is the mail icon. I don't use pidgin, so I removed it - hoping the mail icon would go away also. But it remains. 

In panel preferences, there is no way of configuring the indicator plugin - so I can't find a way to remove the mail icon. I could remove the whole plugin, but then I wouldn't be able to configure wifi and sound.

Can someone help me remove the mail icon?

Thanks!

---

### Post by Toz on 2011-06-22
Uninstall the package **indicator-messages** and the icon will disappear. After which, you will need to either logout and back in again or remove and re-add the Indicator Plugin from the panel to get it to disappear.

---

### Post by jerrrys on 2011-06-22
i removed "xfce4-indicator-plugin".  after you will end up with network icon, but no sound control.

---

### Post by Toz on 2011-06-22
What do you mean "removed xfce4-indicator-plugin"?

To remove the envelope from the indicator applet in the panel, you need to uninstall **indicator-messages**. This will not affect the sound icon.

To make the change take immediate effect, you need to either:
1. log out and back in again _or_
2. remove and re-add the indicator plugin from the panel.

---

### Post by azertyh on 2011-07-16
uninstall indicator-messages removes the mail icon. good.
but is it possible to separate volume and network-manager icons? for example, i want to put the volume on the first panel, and the network on the second.

---

### Post by sal02452 on 2012-06-13
I just installed Xubuntu 12.04 with Xfce 4.8, and I was also wondering how to get the mail icon out of my panel.

"Uninstall the indicator-messages package" sounds like an ok response, but with an obvious problem:  What if someone else who uses this computer uses Pidgin?

Ideally, I would like to have the software installed, and I would like to configure my indicator applet as "Run A and B.  Do not run C."  Does the indicator applet currently have that functionality?  If it doesn't have that functionality, and I tried to implement it, would that be a complete waste of time?

Actually, let's take a step back.  The indicator applet is documented as: "An indicator of something that needs your attention on the desktop."  Well, neither my volume control nor my network manager need my attention.  So why are they indicator plugins?  Wouldn't it make more sense for them to be Panel plugins?  I think it would.  I'd like to be able to add and remove a volume control from my panel just like I can add and remove a clock or a launcher.  Is that possible?  Or would that be a bad idea for some reason?

---

### Post by Toz on 2012-06-13
> **sal02452 said:**
> I just installed Xubuntu 12.04 with Xfce 4.8, and I was also wondering how to get the mail icon out of my panel.

"Uninstall the indicator-messages package" sounds like an ok response, but with an obvious problem:  What if someone else who uses this computer uses Pidgin?

Ideally, I would like to have the software installed, and I would like to configure my indicator applet as "Run A and B.  Do not run C."  Does the indicator applet currently have that functionality?  If it doesn't have that functionality, and I tried to implement it, would that be a complete waste of time?
You could use the messages blacklist functionality. Look in ~/.config/indicators/messages/applications-blacklist directory (if you don't have one, feel free to create one). Here you can blacklist (disallow) certain applications from showing up in the messages indicator. To do so, create a file (e.g. pidgin) that contains the full path to the desktop file of the application that you want to blacklist (e.g. /usr/share/applications/pidgin.desktop). This should prevent pidgin from showing up in the messages indicator. I've also read that if you blacklist all the applications that show up there, the messages icon will not appear. (Disclaimer: I haven't played with this functionality since 11.04 so I can't vouch whether it still works like this - you'll need to test)

> Actually, let's take a step back.  The indicator applet is documented as: "An indicator of something that needs your attention on the desktop."  Well, neither my volume control nor my network manager need my attention.  So why are they indicator plugins?  Wouldn't it make more sense for them to be Panel plugins?  I think it would.  I'd like to be able to add and remove a volume control from my panel just like I can add and remove a clock or a launcher.  Is that possible?  Or would that be a bad idea for some reason?
Good points. You could remove the indicator applet from the panel and install the Mixer plugin to get a (different) sound mixer (with slightly different functionality). Only problem is, there doesn't appear to be a network plugin to take place of the one that is removed. You could also file a bug report/enhancement request on launchpad regarding this.

---

### Post by Jose Catre-Vandis on 2012-06-14
I don't like this either. Here is my solution:

Remove the indicator plugin from the panel (mail-network-sound)
Reboot / Logout/Login
You should get a new network icon
Then add mail watcher to panel if you want that

For sound, I first install xfce4-mixer then add the volume applet to the panel. You lose the pavucontrol and mute this way.

For mute I have added an .asoundrc file and launcher (thanks to Toz iirc :))
see here:[http://bimma.me.uk/2012/03/01/xubuntu-1110-volume-mute-button/](http://bimma.me.uk/2012/03/01/xubuntu-1110-volume-mute-button/)

pavucontrol is still in the Multimedia Section of the apps menu so you can always drag out a launcher for it

---

### Post by fixitmanarizona on 2012-07-14
This thing was a bad idea and I didn't like it from the very start. With 11.10 you can now get other options. I have everything I need, without it, including the new Xubuntu Weather Update (which WAS in this thing as "weather indicator") The new one shows current temperature, wind conditions etc and a cloud or sun icon etc.. The news one uses METAR data instead of google or yahoo data as the indicator one did.)
Plus I now have a simple volume icon, the date, network connectivity, printer icon in something called the "notification area" which IS configurable (maybe that's  from gnome, as I do have gnome support AND kde support (libraries) installed.)
I also have Orage panel clock. The date from the clock shows in the notification area, between the network icon and the sound volume icon, and either clicking the time on the clock OR clicking on the date will open Orage calendar.
The weather update, near as I can determine, is new, from XFCE. It's a panel application ONLY and does not show up in your applications menu, you have to select it from your panel items now. That is not a bad idea really, if well implemented.:P
These will apparently work even better in Xubuntu 12, without the need for indicator-plugin.
If I were you I would find the other add ons in the repositories (say using Synaptic) and then you won't need the indicator.

---

