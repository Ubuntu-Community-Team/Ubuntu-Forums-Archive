---
title: "Why does formatting your harddrives not require password authentication?"
date: 2010-01-30
forum: General Help
---

### Post by MikeHaggarKJ on 2010-01-30
EDIT gwpritch told me you can change the permissions with this command: 
sudo chmod <command or app.> 744

Now I just need to know what command is invoked when i format via the right click menu. CAN SOMEONE HELP ME?? PLEASE?? I dont want to downgrade to ubuntu 8.10.

I noticed that in Ubuntu 9.10 (had 8.10 before, hadnt upgraded in a while) you can reformat by simply right-clicking your harddrive/usb stick/whatever and then choosing format. 
The scary thing about this is that it doesnt require password authentication from you. It doesnt even second check to make sure that thats what you want to. 
I don't want it to be like this. Not because I'm afraid of malware or hackers or anything, but because I know that I sometimes accidently press the wrong buttons etc and I REALLY dont want to accidently reformat my harddrives.

Is there any way to change this, so that it requires authentication? Or maybe take away the option from the right-click menu entirely? (i prefer to use gparted partition editor anyway)

Thanks for any help.

---

### Post by dcstar on 2010-01-30
> **MikeHaggarKJ said:**
> I noticed that in Ubuntu 9.10 (had 8.10 before, hadnt upgraded in a while) you can reformat by simply right-clicking your harddrive/usb stick/whatever and then choosing format. 
The scary thing about this is that it doesnt require password authentication from you. It doesnt even second check to make sure that thats what you want to. 
I don't want it to be like this. Not because I'm afraid of malware or hackers or anything, but because I know that I sometimes accidently press the wrong buttons etc and I REALLY dont want to accidently reformat my harddrives.

Is there any way to change this, so that it requires authentication? Or maybe take away the option from the right-click menu entirely? (i prefer to use gparted partition editor anyway)

Thanks for any help.

I can find nothing on my system that allows me to format partitions apart from in gparted.

---

### Post by MikeHaggarKJ on 2010-01-31
> **dcstar said:**
> I can find nothing on my system that allows me to format partitions apart from in gparted.
Maybe its only in 9.10 then. You sure you cant see it in the righ-click menu when you right click a partition?
So what do I do? downgrade to 9.04?

---

### Post by NightwishFan on 2010-01-31
(I believe) that it will ask for permission before formatting a system disk partition. It also will not allow you to format a partition that is in use. You can format Fat32 volumes, such as flash drives though. You do not have to downgrade.

---

### Post by MelDJ on 2010-01-31
if you right click it and press format, a notification comes up asking what filesystem you would want it to format to.
isn't that enough warning?

---

### Post by MikeHaggarKJ on 2010-01-31
> **MelDJ said:**
> if you right click it and press format, a notification comes up asking what filesystem you would want it to format to.
isn't that enough warning?
Not for me, sorry.
All you need to do is to accidently press format and then enter. Lets say you where supposed to right click to choose something else and then confirm that action with enter (so you press left click and enter almost simultaneously) and that can lead to you loosing all of your data.
Since formatting isnt something you do everyday or often at all (most people will never have any reason to do so except when they buy new HDDs) theres no reason formatting should be this easy, quick and accessible.
If you disagree thats fine but those are the reasons I want this fixed really badly.
> **NightwishFan said:**
> (I believe) that it will ask for permission  before formatting a system disk partition. It also will not allow you to  format a partition that is in use. You can format Fat32 volumes, such  as flash drives though. You do not have to downgrade.
I tried formatting one of my external HDDs that where empty and it required no authentication.
Getting to the "which file format would you like to format to?" screen when right clicking an internal HDD required no authentication. Maybe it does when you confirm it but I didn't try that for obvious reasons.

---

### Post by MikeHaggarKJ on 2010-02-01
Please someone? Is there any way to change this?

---

### Post by gwpritch on 2010-02-01
Do you know what command is invoked when you reformat? 
If so, you can change the permissions as follows"

```
sudo chmod <command or app.> 744
```

This will change permission so that only root may write to or execute this command or application.
Group Members and others will have read only permission.

---

### Post by whiskeylover on 2010-02-01
Is it possible that the permissions were already elevated by another program before you tried to format the disk?

---

### Post by MikeHaggarKJ on 2010-02-01
> **whiskeylover said:**
> Is it possible that the permissions were  already elevated by another program before you tried to format the  disk?
 no, ive tried reformatting the first thing i do after a reboot. you  always have permission to reformat by defau
> **gwpritch said:**
> Do you know what command is invoked when you reformat? 
If so, you can change the permissions as follows"

```
sudo chmod <command or app.> 744
```This will change permission so that only root may write to or execute this command or application.
Group Members and others will have read only permission.
Thanks alot dude!! That's exactly what I wanted!! :D

Problem is: I have no clue what command is invoked when you reformat or how you find something like that out.

Although I use Ubuntu quite a bit Im still a total noob at it cuz I only do such basic things in it (Email, websurfing and managing files....thats pretty much it). Anyone wanna help out here or know what command it is?

---

### Post by MikeHaggarKJ on 2010-02-03
Anyone know how to figure out what terminal command formatting is?? Or how to figure it out?? please!!

---

### Post by MikeHaggarKJ on 2010-02-05
please, please PLEASE! I will not be able to use ubuntu like this, im stuck with windows!! please help me!

---

### Post by oldos2er on 2010-02-05
You're looking for mkfs.xxx commands, which live in /sbin. I can't recommend you change permissions on /sbin though.

---

### Post by Ocxic on 2010-02-05
> **MikeHaggarKJ said:**
> Not for me, sorry.
All you need to do is to accidently press format and then enter. Lets say you where supposed to right click to choose something else and then confirm that action with enter (so you press left click and enter almost simultaneously) and that can lead to you loosing all of your data.


Wow, thats just like, turning on your car, accidentally shifting into drive instead of reverse, and pushing the gas pedal, and hitting the guy in front of you.

moral of the story, Look where you click. if your dumb enough to to format your HD like that, you deserve to loose all your data. you know how many times I've heard "my computer crashed I didn't know It was my job to backup my stuff, your computer sucks."

Think before you do, or do before you think, oh s**t. your choice

---

### Post by MikeHaggarKJ on 2010-02-06
Or I just use windows where the designers weren't stupid enough to put format right next to something that I click all the time (unmount) and let you reformat without any extra confirmation from you.
I shouldn't have to worry about accidently clicking a MEGA DEATH PANIC CHAOS button all the time. The fact that formatting can happen by accident this easily is a design flaw regardless of how much you deny it. 
It has nothing to do with THINKING. It's completely different from being stupid, this is about accidently pressing a button when you meant to press another one. Maybe youre perfect and never make mistakes so you dont need to worry about that, but not everyone are perfect, real sorry about that.

> **oldos2er said:**
> You're looking for mkfs.xxx commands, which live  in /sbin. I can't recommend you change permissions on /sbin  though.
Is there any way to find out what the specific command for this is? Thanks.

---

### Post by sisco311 on 2010-02-06
You can only format external disks without password authentication, but you should be prompted for a password when you try to change (delete/create a partition on) an internal disk.

Anyway, you can change this behavior by editing the /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy file:
```
gksu gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy
```

In the [COLOR="Red"]org.freedesktop.devicekit.disks.change[/COLOR] entry change the authentication mode (allow_active) from **yes** to **auth_admin_keep**:

```

...
  <action id=[COLOR="Red"]"org.freedesktop.devicekit.disks.change"[/COLOR]>
    <description>Modify a device</description>
    <description xml:lang="da">Modificér en enhed</description>
    <description xml:lang="de">Gerät ändern</description>
    <message>Authentication is required to modify the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at ændre en enhed</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät zu ändern</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>**auth_admin_keep**</allow_active>
    </defaults>
  </action>
...
```

---

### Post by oldos2er on 2010-02-06
"Is there any way to find out what the specific command for this is?"

Please define "this"...?

---

### Post by MikeHaggarKJ on 2010-02-06
> **sisco311 said:**
> You can only format external disks without password authentication, but you should be prompted for a password when you try to change (delete/create a partition on) an internal disk.

Anyway, you can change this behavior by editing the /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy file:
```
gksu gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy
```

In the [COLOR="Red"]org.freedesktop.devicekit.disks.change[/COLOR] entry change the authentication mode (allow_active) from **yes** to **auth_admin_keep**:

```

...
  <action id=[COLOR="Red"]"org.freedesktop.devicekit.disks.change"[/COLOR]>
    <description>Modify a device</description>
    <description xml:lang="da">Modificér en enhed</description>
    <description xml:lang="de">Gerät ändern</description>
    <message>Authentication is required to modify the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at ændre en enhed</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät zu ändern</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>**auth_admin_keep**</allow_active>
    </defaults>
  </action>
...
```

This worked. Thanks a million. :) 
This is fantastic!!! :D:D

---

### Post by Ocxic on 2010-02-06
I'm running 9.10, there is no format command when I right click

---

### Post by wojox on 2010-02-06
> **Ocxic said:**
> I'm running 9.10, there is no format command when I right click

Are you booting from aq live CD to do this?

---

### Post by Ocxic on 2010-02-07
no.

---

### Post by dcstar on 2010-02-08
> **Ocxic said:**
> I'm running 9.10, there is no format command when I right click

Actually there is - but **only** on external drives, just like Windows.

And just like Windows, any admin rights level user can format an external drive without a password - so Ubuntu is working exactly as 99.99% of users want it to.

It is pretty simple for the OP, if you don't want admin functions then don't use an account with admin rights.

---

### Post by Ocxic on 2010-02-08
I was clicking on my external drive, and usb stick

---

