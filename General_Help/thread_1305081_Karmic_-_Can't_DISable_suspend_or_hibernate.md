---
title: "Karmic - Can't DISable suspend or hibernate"
date: 2009-10-29
forum: General Help
---

### Post by dnairb on 2009-10-29
In *Jaunty*, and other previous releases, it was a simple exercise to disable suspend and hibernate, using the gnome configuration editor:

apps -> gnome-power-manager -> general

and unchecking can_hibernate and can_suspend options.

The "Shutdown the computer" window then only has "Shutdown" and "Restart" as the available options.


In Karmic, however, this doesn't work. Suspend and Hibernate are still options in the shutdown/restart window.

---

### Post by dnairb on 2009-11-01
Any ideas?

---

### Post by Geert Jan on 2009-11-01
Yeah I'd like to disable suspend as well, as it does weird things to my system. I haven't been able to find a workaround.

This bug is on Launchpad though. It's Confirmed and has Medium Importance, so let's hope a fix will come soon.

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/432598](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/432598)

---

### Post by dnairb on 2009-11-03
Thanks for the pointer Geert.

I see that the bug is as yet not allocated.

---

### Post by nerdy_kid on 2009-11-03
i think gnome-power manager sucks big time.  In my opinion, it need a complete overhaul.  Heck, i switched to KDE to escape that thing!  It doesn't even have profile support!  All u desktop users dont care, but for all the laptops, its a pain in the butt.

---

### Post by marshalium on 2009-11-06
I found a way to prevent the system from suspending and/or hibernating. The suspend/hibernate options still show up in the menu but if you click on one of them it just locks the screen.

You just need to edit: /usr/share/polkit-1/actions/org.freedesktop.devicekit.power.policy

And change the ```
<allow_active>yes</allow_active>
``` entries for suspend and/or hibernate to ```
<allow_active>no</allow_active>
``` So it should look something like this:
```
 
  <action id="org.freedesktop.devicekit.power.suspend">
    <description>Suspend the system</description>
    <message>Authentication is required to suspend the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>no</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.devicekit.power.hibernate">
    <description>Hibernate the system</description>
    <message>Authentication is required to hibernate the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>no</allow_active>
    </defaults>
  </action>
```

Then you will probably need to restart your machine for the changes to take effect.

---

### Post by nanotube on 2010-01-30
the above-mentioned workaround works for me on a fresh install of karmic.

a little suboptimal, inasmuch as the hibernate option is still there even if 'disabled', but even so i'd rather have it lock the screen than freeze the comp, if i accidentally click on it.

thanks marshallium for posting it. :)

---

### Post by Pjotr123 on 2010-02-06
marshalium's tip is correct. Thank you.

You can only change the text as root, so the terminal command is:
```

gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.power.policy

```

--edited: removed a wrong assumption--

---

### Post by nanotube on 2010-02-06
> **Pjotr123 said:**
> marshalium's tip points in the right direction, but it's not entirely complete, I think. 

I think you should not only change this line from "yes" into "no":
<allow_active>yes</allow_active>

but also the line above, from "no" into "yes"!
<allow_inactive>no</allow_inactive>


hmm, i only changed allow_active from 'yes' to 'no' and everything worked... 

what in particular didn't work for you when you didn't set allow_inactive to yes?

---

### Post by Pjotr123 on 2010-02-06
I only applied "my" version, which works fine on my machines.... 

I'm not sure, but it seems logical to not only **forbid** "active", but also **allow** "inactive". The one implies the other. Otherwise you forbid hibernation to be *active*, and also to be *inactive*! A logical impossibility. That feels wrong.

As I said, I'm not sure. I'm acting solely on my "Linux intuition", which may be quite wrong in this case, of course. However, "my" version works fine, so it's probably not wrong to edit the second line. Superfluous at most, but not wrong.

---

### Post by warfacegod on 2010-02-06
Ubuntu Tweak has a check box to disable both. [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

It also has a number of useful settings that are a real pain to find normally.

---

### Post by Pjotr123 on 2010-02-06
> **warfacegod said:**
> Ubuntu Tweak has a check box to disable both. [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

It also has a number of useful settings that are a real pain to find normally.

No offence, but I distrust those third-party scripts. God knows what harm they do to your system. I don't want my system to run on software from all kinds of shady third-party sources and PPA's, like those that Ubuntu Tweak facilitates...

The few exceptions I make include only well known 3d party sources like Medibuntu and Opera. But as I said: no offence meant. Everybody makes his own decisions, and after all, it's *your* Linux. :)

---

### Post by warfacegod on 2010-02-06
> **Pjotr123 said:**
> No offence, but I distrust those third-party scripts. God knows what harm they do to your system. I don't want my system to run on software from all kinds of shady third-party sources and PPA's, like those that Ubuntu Tweak facilitates...

The few exceptions I make include only well known 3d party sources like Medibuntu and Opera. But as I said: no offence meant. Everybody makes his own decisions, and after all, it's *your* Linux. :)

Ubuntu Tweak is hardly shady and it doesn't install anything except itself. You, yourself have the option of installing the software in it's sources list.

Adobe Flash
Audacity
Banshee
Cairo-dock
Chromium Browser
Compiz
Dropbox

To name a few. Apparently, these are shady? I believe all of them are available from Add/Remove, Synaptic, and/or Ubuntu Software Center.

---

### Post by Admiral_Payne on 2010-02-06
> **Pjotr123 said:**
> marshalium's tip points in the right direction, but it's not entirely complete, I think. 

I think you should not only change this line from "yes" into "no":
<allow_active>yes</allow_active>

but also the line above, from "no" into "yes"!
<allow_inactive>no</allow_inactive>

Thanks marshalium for the idea and Pjotr123 for the addition.
Had been looking for this a bit :-)

---

### Post by nanotube on 2010-02-07
> **Pjotr123 said:**
> 
I'm not sure, but it seems logical to not only **forbid** "active", but also **allow** "inactive". The one implies the other. Otherwise you forbid hibernation to be *active*, and also to be *inactive*! A logical impossibility. That feels wrong.

As I said, I'm not sure. I'm acting solely on my "Linux intuition", which may be quite wrong in this case, of course. However, "my" version works fine, so it's probably not wrong to edit the second line. Superfluous at most, but not wrong.

well, the fact that a 'logical impossibility' may be created, using two seemingly redundant options, should tell you that your interpretation of the options is probably wrong (this isn't microsoft we're talking about, after all :D )

as it happens, your intuition is in this case wrong. active and inactive refer to active and inactive sessions, not to active and inactive hibernation.

when intuition fails, the manual doesn't :) : [http://manpages.ubuntu.com/manpages/lucid/man8/polkit.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/polkit.8.html)

though setting inactive to 'yes' doesn't apparently hurt anything, according to this kde policykit tutorial, "it's a good idea to set inactive to 'no'":
[http://techbase.kde.org/Development/Tutorials/PolicyKit/Introduction](http://techbase.kde.org/Development/Tutorials/PolicyKit/Introduction)

i think that pretty much settles the issue, showing that marshallium's post does not need an amendment...

---

### Post by Pjotr123 on 2010-02-07
> **nanotube said:**
> well, the fact that a 'logical impossibility' may be created, using two seemingly redundant options, should tell you that your interpretation of the options is probably wrong (this isn't microsoft we're talking about, after all :D )

as it happens, your intuition is in this case wrong. active and inactive refer to active and inactive sessions, not to active and inactive hibernation.

when intuition fails, the manual doesn't :) : [http://manpages.ubuntu.com/manpages/lucid/man8/polkit.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/polkit.8.html)

though setting inactive to 'yes' doesn't apparently hurt anything, according to this kde policykit tutorial, "it's a good idea to set inactive to 'no'":
[http://techbase.kde.org/Development/Tutorials/PolicyKit/Introduction](http://techbase.kde.org/Development/Tutorials/PolicyKit/Introduction)

i think that pretty much settles the issue, showing that marshallium's post does not need an amendment...

You've convinced me... I rest my case. :)

---

### Post by congminh1709 on 2010-05-05
Hello everybody, my Ubuntu 10.04 can't suspend correctly (suspend = not responding), and I want to disable it.

> **marshalium said:**
> I found a way to prevent the system from suspending and/or hibernating. The suspend/hibernate options still show up in the menu but if you click on one of them it just locks the screen.

You just need to edit: /usr/share/polkit-1/actions/org.freedesktop.devicekit.power.policy

And change the ```
<allow_active>yes</allow_active>
``` entries for suspend and/or hibernate to ```
<allow_active>no</allow_active>
``` So it should look something like this:
```
 
  <action id="org.freedesktop.devicekit.power.suspend">
    <description>Suspend the system</description>
    <message>Authentication is required to suspend the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>no</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.devicekit.power.hibernate">
    <description>Hibernate the system</description>
    <message>Authentication is required to hibernate the system</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>no</allow_active>
    </defaults>
  </action>
```

Then you will probably need to restart your machine for the changes to take effect.
Maybe this is a good tip, but I don't have  config file **org.freedesktop.devicekit.power.suspend** to edit?

```
congminh1709@ubuntu:/usr/share/polkit-1/actions$ ls
com.hp.hplip.policy
com.ubuntu.devicedriver.policy
com.ubuntu.systemservice.policy
com.ubuntu-tweak.daemon.policy
com.ubuntu.usbcreator.policy
gdm.policy
org.debian.apt.policy
org.debian.aptxapianindex.policy
org.freedesktop.consolekit.policy
org.freedesktop.network-manager-settings.system.policy
org.freedesktop.policykit.policy
org.freedesktop.RealtimeKit1.policy
org.freedesktop.SystemToolsBackends.policy
org.freedesktop.udisks.policy
org.freedesktop.upower.policy
org.freedesktop.upower.qos.policy
org.gnome.clockapplet.mechanism.policy
org.gnome.cpufreqselector.policy
org.gnome.gconf.defaults.policy
screenresolution-mechanism.policy
congminh1709@ubuntu:/usr/share/polkit-1/actions$ 

```

So, when i run

```
sudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.power.policy
```

It's just open a blank file

I also tried Ubuntu Tweak, but it doesn't apply the changes for my system, and I can't disable the suspend function.

Any solution for this case? Thanks.

**_Update:_** I found this, **org.freedesktop.devicekit.power.suspend** has changed to **org.freedesktop.upower.policy**. So my new command is 

```
sudo gedit /usr/share/polkit-1/actions/org.freedesktop.upower.policy
```

After editing and relogin, it works well.

---

### Post by marshalium on 2010-05-05
> **congminh1709 said:**
> 
**_Update:_** I found this, **org.freedesktop.devicekit.power.suspend** has changed to **org.freedesktop.upower.policy**. So my new command is 

```
sudo gedit /usr/share/polkit-1/actions/org.freedesktop.upower.policy
```

After editing and relogin, it works well.

FYI, I believe the correct way to do this in 10.04 is to create a new config file in /etc/polkit-1/localauthority/50-local.d/

Something like:
```

sudo gedit /etc/polkit-1/localauthority/50-local.d/disable-suspend.pkla

```

And put the following in the file:

```

[Disable suspend]
Identity=unix-user:*
Action=org.freedesktop.upower.suspend;org.freedesktop.upower.hibernate
ResultActive=no
ResultAny=no

```

---

