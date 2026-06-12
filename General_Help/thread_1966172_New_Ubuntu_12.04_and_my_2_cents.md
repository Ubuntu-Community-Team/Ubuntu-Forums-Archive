---
title: "New Ubuntu 12.04 and my 2 cents"
date: 2012-04-26
forum: General Help
---

### Post by twodogs on 2012-04-26
1) wireless does not work. unless i do this in terminal...
sudo modprobe -r iwlagn
sudo modprobe iwlagn bt_coex_active=0
*internet is slow and this must be done each time i log in. :(

2) no easy way to change gtk/icon theme unless i download either gnome tweak tool or dconf-editor or who knows what else. 

3) the dots on the login screen are just plain stupid. no way to edit the login (simple lightdm doesn't work) and neither does grub-customizer. ho-hum.

other than that, it looks descent.  i'm still playing with it though.  unity is nice and quick but how is this new release supposed to be easy or good for a noob when basic tools are lacking.  i install ubuntu on friends computers because they don't want windows anymore, but i can't support this anymore it's getting harder to do stuff. 

i'm done.  anyone else have similar problems?

---

### Post by Eirreann on 2012-04-26
I've made quite a few threads here since I upgraded detailing the many problems I've had; ultimately, Ubuntu forgot to support my Nvidia drivers; the 173 drivers are out, yay.  Now I'm stuck using Ubuntu 2D until Ubuntu releases a fix (if they ever do).
That and the boot sound won't sound; when I checked "startup applications", it wasn't there....
honestly this upgrade has done nothing but frustrate me; I kind of wish that I had waited to hear feedback before hitting the "upgrade button"...

---

### Post by twodogs on 2012-04-26
hmm, on login screen, make sure volume is turned up (look in upper right corner). mine was originally on mute.  i have login sound now.

to see ALL of your startup applications, enter this in terminal and then open up 'startup applications.'  works wonders.

#Get all programs and services back in Startup Applications
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

---

### Post by Eirreann on 2012-04-26
> **twodogs said:**
> hmm, on login screen, make sure volume is turned up (look in upper right corner). mine was originally on mute.  i have login sound now.

to see ALL of your startup applications, enter this in terminal and then open up 'startup applications.'  works wonders.

#Get all programs and services back in Startup Applications
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

Well, that showed a lot more applications in "Starup Application", but Gnome Boot Sound (or whatever it was called) isn't there....

---

### Post by techsupport on 2012-04-26
> **Eirreann said:**
> I've made quite a few threads here since I upgraded detailing the many problems I've had; ultimately, Ubuntu forgot to support my Nvidia drivers; the 173 drivers are out, yay.  Now I'm stuck using Ubuntu 2D until Ubuntu releases a fix (if they ever do).
That and the boot sound won't sound; when I checked "startup applications", it wasn't there....
honestly this upgrade has done nothing but frustrate me; I kind of wish that I had waited to hear feedback before hitting the "upgrade button"...

Here is what I suggest about the video card issue. Switch from LightDM to GDM manager, and then reinstall your propertary video driver. I bet you will find that the problem goes away. They will have a patch for LightDM and the video driver soon.

You can reenable the login sound theme if you want.  It was ok, I guess.

What else do you need for right now?

---

### Post by pqwoerituytrueiwoq on 2012-04-26
> **twodogs said:**
> 
3) the dots on the login screen are just plain stupid. no way to edit the login (simple lightdm doesn't work) and neither does grub-customizer. ho-hum.
then switch to gdm
```
sudo apt-get purge lightdm;sudo apt-get install gdm
```> **twodogs said:**
> 
other than that, it looks descent.  i'm still playing with it though.   unity is nice and quick but how is this new release supposed to be easy  or good for a noob when basic tools are lacking.  i install ubuntu on  friends computers because they don't want windows anymore, but i can't  support this anymore it's getting harder to do stuff. 
then try [xubuntu]("apt:xubuntu-desktop") or install mate-desktop with the below commands (neatly in one line)
```
sudo add-apt-repository "deb http://packages.mate-desktop.org/repo/ubuntu $(lsb_release -cs) main";sudo apt-get update;sudo apt-get install mate-archive-keyring mate-core mate-desktop-environment mate-indicator-applet
```if you want compiz in mate add this to startup applications you will need to configure compiz in [ccsm](apt:compizconfig-settings-manager) before starting compiz just so you know
```
#!/bin/sh
if [ 0`mate-session` -gt 0 ]; then
killall marco
compiz --replace &
fi
```> **twodogs said:**
> wireless does not work. unless i do this in terminal...
sudo modprobe -r iwlagn
sudo modprobe iwlagn bt_coex_active=0
*internet is slow and this must be done each time i log in.
try putting it in [FONT=Courier New]/etc/rc.local[/FONT] before the line exit

---

### Post by wojox on 2012-04-26
> **twodogs said:**
> 
#Get all programs and services back in Startup Applications
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop

Sweet :p

---

### Post by Eirreann on 2012-04-26
> **techsupport said:**
> Here is what I suggest about the video card issue. Switch from LightDM to GDM manager, and then reinstall your propertary video driver. I bet you will find that the problem goes away. They will have a patch for LightDM and the video driver soon.



...I have no idea how on earth to do that....
Sorry, I'm still new at this...

---

### Post by twodogs on 2012-04-26
System -> Preferences -> Startup Applications

Click Add and use this information:

Code:

Name: GNOME Login Sound
Command: /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Comment: Plays a sound whenever you log in

That should work.

---

### Post by twodogs on 2012-04-26
sudo apt-get purge lightdm;sudo apt-get install gdm

---

### Post by techsupport on 2012-04-26
> **Eirreann said:**
> ...I have no idea how on earth to do that....
Sorry, I'm still new at this...

That's alright. 

In Terminal:

```
sudo apt-get purge lightdm && sudo apt-get install gdm
```

---

### Post by IWantFroyo on 2012-04-26
Just hit the cog-power-thingy in the top right corner, select "Startup Applications", and Add a program. Call it whatever you want, and put this for the command:
```
sudo modprobe -r iwlagn && sudo modprobe iwlagn bt_coex_active=0
```
This will start up your wireless automatically on login.

Also, open "Software Sources", and change your repositories. If you select "Other", another window will open. Click on "Choose Closest Repository" (or something like that). Allow it to run, and then:
```
sudo apt-get update
```
This will speed up application installs and software updates.

Also, nothing is lacking. It's all still there in the Applications lens.

---

### Post by Eirreann on 2012-04-26
> **techsupport said:**
> That's alright. 

In Terminal:

```
sudo apt-get purge lightdm && sudo apt-get install gdm
```

Thanks!  I'll give this a shot tomorrow!  (I'm writing an important paper for school right now or else I'd try it now)

---

### Post by QIII on 2012-04-26
> **Eirreann said:**
> Ubuntu forgot to support my Nvidia drivers

No, Canonical didn't.  They don't have anything to do with OEM hardware drivers and they don't provide support for them.  The OEMs provide the drivers that support to OSes.

---

### Post by techsupport on 2012-04-26
> **QIII said:**
> No, Canonical didn't.  They don't have anything to do with OEM hardware drivers and they don't provide support for them.  The OEMs provide the drivers that support to OSes.

It has something to do with LightDM and that video driver. It wasn't a problem until now.  It isn't really the video driver that is at fault here probably.

---

### Post by Eirreann on 2012-04-26
> **QIII said:**
> No, Canonical didn't.  They don't have anything to do with OEM hardware drivers and they don't provide support for them.  The OEMs provide the drivers that support to OSes.

I was really just being skeptical here; I have no idea how Canonical goes about with upgrading Ubuntu or all the finer details of it's production, although I highly respect and appreciate Canonical for the effort that they put into this OS!  I'm just a bit frustrated by all of the problems I'm encountering with this upgrade...

---

### Post by techsupport on 2012-04-26
> **Eirreann said:**
> I was really just being skeptical here; I have no idea how Canonical goes about with upgrading Ubuntu or all the finer details of it's production, although I highly respect and appreciate Canonical for the effort that they put into this OS!  I'm just a bit frustrated by all of the problems I'm encountering with this upgrade...

We all are having the same issues right now. This is normal around release date.

---

### Post by Uncle Spellbinder on 2012-04-26
Not suffering any nVidia issues, or any others... For now. All seems rock solid for the time being.

---

### Post by techsupport on 2012-04-26
> **Uncle Spellbinder said:**
> Not suffering any nVidia issues, or any others... For now. All seems rock solid for the time being.

Updates are running quite slow right now though.

---

### Post by Uncle Spellbinder on 2012-04-26
> **techsupport said:**
> Updates are running quite slow right now though.
True enough. Though upon initial install yesterday morning, I received nearly 600 updates. More than a hundred since then.

---

### Post by Eirreann on 2012-04-26
> **Uncle Spellbinder said:**
> True enough. Though upon initial install yesterday morning, I received nearly 600 updates. More than a hundred since then.

Seriously?  Since I upgraded earlier this afternoon I haven't received a single update!

---

### Post by techsupport on 2012-04-26
> **Eirreann said:**
> Seriously?  Since I upgraded earlier this afternoon I haven't received a single update!

Me neither. I got one or two. Nothing major.  If you select the sudo apt-get dist-upgrade there is just a kernel and a header package.  I'm not going to install them until they are ready though.

---

### Post by Uncle Spellbinder on 2012-04-26
Don't know if it makes a difference or not, but I did a clean install from the downloaded ISO burned to DVD. No upgrade.

---

### Post by techsupport on 2012-04-26
> **Uncle Spellbinder said:**
> Don't know if it makes a difference or not, but I did a clean install from the downloaded ISO burned to DVD. No upgrade.

I have been running the Beta 1 ->> Beta 2 >> And now the upgraded release.

---

### Post by Uncle Spellbinder on 2012-04-26
> **techsupport said:**
> I have been running the Beta 1 ->> Beta 2 >> And now the upgraded release.
I ran the last Alpha, Betas 1&2. Decided to start fresh with the final release.

---

### Post by bodhi.zazen on 2012-04-26
> **Eirreann said:**
> I was really just being skeptical here; I have no idea how Canonical goes about with upgrading Ubuntu or all the finer details of it's production, although I highly respect and appreciate Canonical for the effort that they put into this OS!  I'm just a bit frustrated by all of the problems I'm encountering with this upgrade...

Sorry you are having problems, but at least direct your frustration to the proper place.

If you have a nvidia card you can use the open source (nouveau) driver or the closed source driver provided by nvidia.

If you have a problem with the nvidia driver -> file with Canonical (Ubuntu) on Launchpad.

If you use the nvidia proprietary driver -> file a bug report with nvidia. Complaining to canonical or Ubuntu about a binary they neither built or support is inappropriate.

---

### Post by Eirreann on 2012-04-27
> **bodhi.zazen said:**
> Sorry you are having problems, but at least direct your frustration to the proper place.

If you have a nvidia card you can use the open source (nouveau) driver or the closed source driver provided by nvidia.

If you have a problem with the nvidia driver -> file with Canonical (Ubuntu) on Launchpad.

If you use the nvidia proprietary driver -> file a bug report with nvidia. Complaining to canonical or Ubuntu about a binary they neither built or support is inappropriate.
Forgive me if I gave the impression that I blame either Canonical or the Ubuntu developers for any of my problems; I rather blame my laptop for being so old as to have compatibility issues (if that is indeed what they are) in the first place.
As to what driver I'm using, I honestly don't know... before I upgraded, I was using an Nvidia proprietary driver 173, or something like that... now that I've updated all things Nvidia-related have been wiped from my computer... and the Additional Drivers section in settings doesn't show anything...

---

### Post by Eirreann on 2012-04-27
> **techsupport said:**
> That's alright. 

In Terminal:

```
sudo apt-get purge lightdm && sudo apt-get install gdm
```

Okay, just applied it, and nothing is different except the login screen looks a little bit different and my name isn't in the upper-right corner any more....
Besides that, nothing is different; everything is running exactly the same.
So how do I undo that code?  I'd like my name back, haha!

---

### Post by techsupport on 2012-04-27
> **Eirreann said:**
> Okay, just applied it, and nothing is different except the login screen looks a little bit different and my name isn't in the upper-right corner any more....
Besides that, nothing is different; everything is running exactly the same.
So how do I undo that code?  I'd like my name back, haha!

I just got the 12.04 kernel update this morning and my Ubuntu 3D session is working great.

Try it.

---

### Post by Stray Wolf on 2012-04-27
Two cents...

1. The video lens should be more customizable. I'd like to add Hulu and a few other video sites to it. 
2. The launcher is a bit stubborn to un-hide sometimes. Despite playing with the sensitivity. Seems to do with how quickly you mouse over to the edge. The quicker you 'slam" the mouse against the edge the better the response.
3.HUD...I have to keep reminding myself you're there.
4. Themes and customization...do I use MyUnity, Gnome-tweak, CCSM, all of the above, none of the above, something else?
5. I thought you could pull up keyboard shortcuts in the dash...
6. The music lens should also show music from music services/sites.

That's all I have for now. I'm just tinkering at the moment. Still don't like Shotwell. Installing digikam despite no HUD support. I still have to use FF or XBMC to access Hulu since the Hulu desktop only crashes.

---

### Post by techsupport on 2012-04-27
> **Stray Wolf said:**
> I still have to use FF or XBMC to access Hulu since the Hulu desktop only crashes.

Everyone reading this need to go immediately to the Hulu support forums and post something like - Hey you guys, your Hulu Player worked in 11.10 but it doesn't work in the latest release of Ubuntu 12.04. What gives Hulu??? I love Hulu, but you need to let them know to fix it. You guys have to hound them.

---

### Post by Eirreann on 2012-04-27
> **techsupport said:**
> I just got the 12.04 kernel update this morning and my Ubuntu 3D session is working great.

Try it.

I checked Update Manager and nothing... is kernel something different?
Also, could you tell me how to undo the
```
sudo apt-get purge lightdm && sudo apt-get install gdm
```
thing?  It didn't help anything but instead I lost some features (and since I used it my wifi has been extremely skittish...)

---

### Post by Eirreann on 2012-04-27
> **rockinfreeworld said:**
> There was a new kernel that installed when I booted up today on 12.04.

They fixed Ubuntu 3D effects. I have my spinny cube back. Woo-hoo!
So, is it something that installs automatically?
Because if so, it didn't work for me...

---

### Post by Stray Wolf on 2012-04-28
> **techsupport said:**
> Everyone reading this need to go immediately to the Hulu support forums and post something like - Hey you guys, your Hulu Player worked in 11.10 but it doesn't work in the latest release of Ubuntu 12.04. What gives Hulu??? I love Hulu, but you need to let them know to fix it. You guys have to hound them.
I've done this. The workaround is to use an earlier version of flash. The new version of flash works with everything else though. I guess we should hound Hulu and Adobe.

---

### Post by Eirreann on 2012-04-29
> **techsupport said:**
> 
In Terminal:

```
sudo apt-get purge lightdm && sudo apt-get install gdm
```


CAN SOMEONE PLEASE TELL ME HOW TO UNDO THIS?!?!?!?!?!?!?!

Forgive me for shouting, but I have asked multiple times on this thread and every time I have been ignored.

---

### Post by bodhi.zazen on 2012-04-29
> **Eirreann said:**
> CAN SOMEONE PLEASE TELL ME HOW TO UNDO THIS?!?!?!?!?!?!?!

Forgive me for shouting, but I have asked multiple times on this thread and every time I have been ignored.

LOL

```
sudo apt-get purge gdm && sudo apt-get install lightdm
```

And if that does not work or you get errors post back.

---

### Post by Eirreann on 2012-04-29
> **bodhi.zazen said:**
> LOL

```
sudo apt-get purge gdm && sudo apt-get install lightdm
```And if that does not work or you get errors post back.

Thank you!  I will post back shortly with the results!

---

### Post by Eirreann on 2012-04-29
> **bodhi.zazen said:**
> LOL

```
sudo apt-get purge gdm && sudo apt-get install lightdm
```And if that does not work or you get errors post back.

Okay, when I used that code, my computer hung on boot and would never go to the login screen; so using ctrl+alt+f1 I reinstalled that last thing and now everything is working again...

---

### Post by dyess002 on 2012-09-19
> **Eirreann said:**
> I've made quite a few threads here since I upgraded detailing the many problems I've had; ultimately, Ubuntu forgot to support my Nvidia drivers; the 173 drivers are out, yay.  Now I'm stuck using Ubuntu 2D until Ubuntu releases a fix (if they ever do).
That and the boot sound won't sound; when I checked &quot;startup applications&quot;, it wasn't there....
honestly this upgrade has done nothing but frustrate me; I kind of wish that I had waited to hear feedback before hitting the &quot;upgrade button&quot;...

  11.04 is the best version, if you feel the urge to upgrade you will be disappointed because there are a lot options that have been taken away like being able to manage groups in the user and groups and it took away the adding emblems to icons which I use regularly, I use that to mark favourite songs when I have a lot of them, it took away a lot of simple things that you use. I like the old Gnome, they have shoved this new desktops down our throats whether we liked it or not. I have started using Mint which is like Ubuntu.[http://ubuntuforums.org/images/smilies/smiley-faces-80.gif](http://ubuntuforums.org/images/smilies/smiley-faces-80.gif)

---

