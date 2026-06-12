---
title: "Thunderbird store profile on external drive"
date: 2011-11-01
forum: General Help
---

### Post by ade234uk on 2011-11-01
I work in two places. Since BT Yahoo email got hacked I really don't like the idea of having all mail online anymore. Its not just happend with BT it also happend with Google about 8 months ago.

Or though it has big advantages, I would now prefer to drag all email from the server and store it locally using Thunderbird.

I was wondering if its possible to store Thunderbird's profile, which includes all mail, sent, inbox, contacts on an external drive which I carry around with me.

So no matter what machine I am on Thunderbird always has the latest emails displayed.

Now my second problem is the following. I use Xubuntu for home use and Windows for work how would this work since obviously the paths are different.

Your help would be appreciated.

---

### Post by pqwoerituytrueiwoq on 2011-11-01
edit your profiles.ini file or use a sim link
[FONT=Courier New]leafpad ~/.thunderbird/profiles.ini[/FONT] 
swap [FONT=Courier New]leafpad[/FONT] for [FONT=Courier New]mousepad[/FONT] if pre 11.10
change the path to /media/XXXX/{folder to store settings in} (XXXX is the drive for your external device run [FONT=Courier New]ls /media[/FONT] to see all usb storage devices listed)
then move everything in this folder to there
[FONT=Courier New]nautilus ~/.thunderbird/*.default[/FONT]

be sure thunderbird is closed for this process

on windows 
start > run > %appdata%
if access is denied go to [FONT=Courier New]about:support[/FONT] in firefox and click the open profile button then go up a couple folders till you see Thunderbird in one then go in it
you should be able to find the profiles.ini file for Thunderbird from there and edit it

---

### Post by ade234uk on 2011-11-01
Fantastic I will give this a go.
Many Thanks

---

### Post by pqwoerituytrueiwoq on 2011-11-01
since you are using windows and linux be carefuul with addons
windows only and linux only addons
lightening will not work on both oses though i wonder if you can install the windows and linux one

---

### Post by ade234uk on 2011-11-01
I had trouble setting it up. However I just downloaded Thunderbird portable. You probably already know about this. 

I installed Thunderbird portable on my external drive on my brothers machine which has Windows.

I was a little sceptical about this. After installation, I then tried it through Wine on Xubuntu and to my surprise it works. 

This means I can download my emails without having them online.

Quite impressed by this and really easy.

---

### Post by dave0109 on 2011-11-01
I did something similar a while back.  I moved the .thunderbird directory to the new location, then created a symlink from it to my home directory. No need to mess with the profile settings.

Thunderbird doesn't know any different, and if I start it without having the remote disk mounted, then I just get an error about the profile being in use.

---

