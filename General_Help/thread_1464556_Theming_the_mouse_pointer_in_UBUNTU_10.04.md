---
title: "Theming the mouse pointer in UBUNTU 10.04"
date: 2010-04-28
forum: General Help
---

### Post by koushh on 2010-04-28
Hi All,

I was trying to apply a new mouse pointer theme in my UBUNTU 10.04 x64. Strange thing is that as long as my pointer is on top of some window like Firefox, Thunderbird, even the terminal the theme is working fine.  

As soon as I move the cursor to the desktop I can see that old ugly pointer !

Can anyone please help me in finding what is going wrong when it in on normal desktop wallpaper area ?

Thanks,
Koushik

---

### Post by vrhahaha on 2010-04-28
the fastest way of seeing the full change without the need to see CLI is to log out then log in again
hope this helps

cheers

---

### Post by koushh on 2010-04-28
I tried that as well but no luck....

---

### Post by lockalidiot on 2010-04-28
I have the same issue. For some reason disabling desktop effects seems to work. Compiz is screwing with the cursor themes somehow.

---

### Post by spayman on 2010-04-28
[B]hi dude !
well first , can u tell me how u r changing ur mouse cursor ? lol 
you should try gcursor    applications > ubuntu store > search for (gcursor) 
install it , appears in system > preferances > cursor select :) 
i think that's the best way , if your not using it , well do !
peace ![/B]

> superman@ubuntu:-$ Who is me ?
> superman =)

---

### Post by koushh on 2010-04-28
Installing a pointer theme is simple... you can download and drag-drop the tar.gz file into the appearance window. Now select the theme you just installed...

Atleast that is how it used to work earlier...

---

### Post by HazelIced on 2010-04-30
Same thing keeps happening to me.
The pointer theme that I want is selected, but the cursor only uses that theme when its on some interactive thing I guess.
For example, in a text box it uses the theme.
When I want to resize windows it uses the theme.
When a webpage is loading it uses the theme.
But pretty much any other time using the computer it does not use the theme. And I tried other themes that came with Ubuntu but it wasn't working either.

I too have Ubuntu 10.04 x64.

---

### Post by Srinivasanr.cs on 2010-04-30
I just upgraded from 9.10 to 10.04 using alternate iso and after enabling extra visual effects i face the same problem[IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG][IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG].

> Problem : Applied cursor is used only on applications like firefox etc and a transparent black cursor appears on titlebar,desktop,taskbar and all menus.
Please suggest some fix.
If i use None as visual effects there is no problem

---

### Post by Talys on 2010-04-30
It's been reported as a bug here: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/459647](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/459647)

For now, here's a temporary work around from that thread:  
From the command line, run 
```
sudo update-alternatives --config x-cursor-theme
```
and manually select the cursor you want.  This will change the cursor icon, but size changes don't carry over.

---

### Post by bgreenaway on 2010-05-02
I have the same problem. With extra visual effects on, I end up with a mix of old cursor and parts of customized Comixcursor theme.

---

### Post by HazelIced on 2010-05-02
I got it to work!
Put your Cursor's folder in the "/usr/share/icons" folder, and then go inside the "/usr/share/icons/default" folder, edit the index.theme folder and after the = sign replace whatever it says (Mine said "DMZ-White") with the name of the theme as it appears in the icons folder.
You should be able to go to the System -> Preference -> Appearance and customize and then click on your cursors theme name.

---

### Post by wallawally on 2010-05-04
> **HazelIced said:**
> I got it to work!
Put your Cursor's folder in the "/usr/share/icons" folder, and then go inside the "/usr/share/icons/default" folder, edit the index.theme folder and after the = sign replace whatever it says (Mine said "DMZ-White") with the name of the theme as it appears in the icons folder.
You should be able to go to the System -> Preference -> Appearance and customize and then click on your cursors theme name.

worked perfect! thanks

---

### Post by Srinivasanr.cs on 2010-05-04
> **HazelIced said:**
> I got it to work!
Put your Cursor's folder in the "/usr/share/icons" folder, and then go inside the "/usr/share/icons/default" folder, edit the index.theme folder and after the = sign replace whatever it says (Mine said "DMZ-White") with the name of the theme as it appears in the icons folder.
You should be able to go to the System -> Preference -> Appearance and customize and then click on your cursors theme name.

[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG][IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]It didnt work for me. I tried your steps.

---

### Post by Ubunthree on 2010-05-04
I had this problem as well. I found some rather tedious but (so far) successful workarounds at [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141500](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141500).

Scroll down to post #12 and read from there. #12 has worked for me (so far!), though the file in question was named *index.theme* rather than *x-cursor-theme.* Haven't tried the other solutions yet, as I rarely change my mouse pointer.

(edit)...which is the same solution as what HazelIced said up there. Missed it somehow. Oh well, I can confirm it then, I guess!

---

### Post by HazelIced on 2010-05-04
> **Srinivasanr.cs said:**
> [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG][IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]It didnt work for me. I tried your steps.

Did you see your theme's name on the selection screen? I saw it twice and for some reason one worked and the other one didn't, was mostly just try each and see which one worked.

---

### Post by therealKerb on 2010-05-05
> **HazelIced said:**
> I got it to work!
Put your Cursor's folder in the "/usr/share/icons" folder, and then go inside the "/usr/share/icons/default" folder, edit the index.theme folder and after the = sign replace whatever it says (Mine said "DMZ-White") with the name of the theme as it appears in the icons folder.
You should be able to go to the System -> Preference -> Appearance and customize and then click on your cursors theme name.

Thanks for this one.  This issue has been driving me nuts.

Cheers.

---

### Post by resthavener on 2010-05-06
Tried installing gcursor in 10.04 - didn't work for me.  Have tried various other bits of advice - none of them worked except I get a double cursor part of the time (in system bar and desktop).  Plus the wretched window buttons keep changing back to the left after I spent 30 minutes finding out how to move them.

All this not calculated to inspire confidence or attract converts.

Interestingly absolutely no probs with 64 bit RC install, only with production 32 bit upgrade from 9.10

---

### Post by GoldenYellow on 2010-05-10
> **HazelIced said:**
> I got it to work!
Put your Cursor's folder in the "/usr/share/icons" folder, and then go inside the "/usr/share/icons/default" folder, edit the index.theme folder and after the = sign replace whatever it says (Mine said "DMZ-White") with the name of the theme as it appears in the icons folder.
You should be able to go to the System -> Preference -> Appearance and customize and then click on your cursors theme name.


Next do a reboot or logout and login for changes to work. Works fine! Thank You.

---

### Post by zirrush on 2010-05-14
Bout to try the workaround here.  From past experience, this has been an issue of compiz vs. X.  Past ubuntu releases, the compiz config had an option for your cursor theme which you had to change in order to use the theme. Also, you'd have to go through your appearance settings in X and change to the same theme otherwise the theme would jump back and forth when going from being over say your window manager versus firefox. (fox would use the X11 theme while the window manager would switch over to the compiz theme).  For some reason, the compiz release on ubuntu 10 doesn't have the option for setting the cursor theme.  Just wanted to share my 2 cents


EDIT:
workaround fixes it for me as well

---

### Post by Apache0c on 2010-05-14
Ooops, didnt read the second page before posting...

---

### Post by vamc on 2010-05-26
> **HazelIced said:**
> I got it to work!
Put your Cursor's folder in the "/usr/share/icons" folder, and then go inside the "/usr/share/icons/default" folder, edit the index.theme folder and after the = sign replace whatever it says (Mine said "DMZ-White") with the name of the theme as it appears in the icons folder.
You should be able to go to the System -> Preference -> Appearance and customize and then click on your cursors theme name.
Thanks, your steps worked for me.

---

### Post by rocuan on 2010-07-05
> 
Put your Cursor's folder in the "/usr/share/icons" folder, 
and then go  inside the "/usr/share/icons/default" folder, 
edit the index.theme  folder and after the = sign replace whatever it says 
(Mine said  "DMZ-White") with the name of the theme
This was irking me as well thanx!
Worked for me with minor modifications.
My index.theme was sym linked to -> /etc/alternatives/x-cursor-theme -> /usr/share/icons/DMZ-White/cursor.theme
So index.theme could not be modified
Solution:
1. back up original
```

sudo mv index.theme index.theme.bak

```2. edit the index.theme, replacing =DMZ-White
3. remove / replace link(s)
```

sudo rm /etc/alternatives/x-cursor-theme
sudo rm /usr/share/icons/DMZ-White/cursor.theme
sudo ln -s index.theme /etc/alternatives/x-cursor-theme

```

---

### Post by aqk on 2010-07-10
WHY do I have to do all these friggin sudos?
I HAVE my Ubuntu 10.4 up-to-date, and from what I have seen and read so so far, this "feature" / this BUG has been around since 2007!

FWIW, I have managed to change my cursors to **[COLOR="Red"]red inside various apps (FF, Terminal, etc)[/COLOR]** using the system / preferences / appearance...   route, but I still have the li'l white HARD TO SEE arrow on the desktop!
It is always getting lost. And please don't teel me to use that "Ctrl" option to find it.
And-
 **[SIZE="3"][B] IT IS HARD TO SEE**[/SIZE][/B]!
I grow olddd (-T.S.Eliot),  my eyesight isn't what it used to be, and I want **BIG CURSORS!!**

Does EVERY Karmic user in the world have this idiotic problem? 
Do they just blindly accept that Ubuntu is limited to a small cursor? 
Why isn't this "feature" fixed? grrr....!

---

### Post by bluepicaso on 2010-07-30
Try here,
[http://ubuntuforums.org/showthread.php?p=9486267](http://ubuntuforums.org/showthread.php?p=9486267)

---

### Post by FireStorm102389 on 2010-08-14
I don't have any problems with the cursor themes when i install one from the software center, HOWEVER, when it comes to downloading one from gnome-look that i like, i have no idea how to manually install it.../usr/shares/icons i believe is the folder i have to drop my cursor theme into? but how do I make that theme the default one? that cursor select program doesn't work for some reason!

---

### Post by vince2678 on 2010-08-20
Compiz cannot update the mouse cursor theme when it is updated in GNOME.   Install this package to allow compiz to notice the change and feel  free  to modify it however you want. PLEASE read he control info!

Unfortunately only works with GNOME. If anyone has LXDE and XFCE please   send me info on how it stores info about cursor theme and size and the   program used for changing cursor theme. I have KDE in a VM so I'll try   something there.
 
 LINK: [_http://ubuntuforums.org/showthread.php?t=1557297_]("http://ubuntuforums.org/showthread.php?t=1557297")

READ CAREFULLY!

---

### Post by AbhiramH on 2010-10-04
Here is a full video tutorial on how to change your ubuntu cursor theme :

[http://www.youtube.com/watch?v=CvS9kh_bMyM](http://www.youtube.com/watch?v=CvS9kh_bMyM)

Thanks,
Abhiram.

---

### Post by Fancycakes on 2010-11-11
I hope you guys all know that /usr/share/icons/default/index.theme was a symbolic link to /etc/alternatives/x-cursor-theme... Right?  Editing the file does work, but the way you were talking made me a little uneasy.  Well, that taken care of, I still need to get a way to change my GDM theme.

---

### Post by vince2678 on 2010-11-12
x-cursor-theme by default points to the DMZ cursor theme.

---

### Post by consoleArt on 2010-11-28
somehow i found the fix to be very simple...

disable the desktop effects and enable again...

system --> preferences -->  appearance --> 

select visual effects tab and set the option to NONE...
you mouse icons are normal...

activate the EXTRA effects now...it will open a small status bar saying searching for drivers or something...after that the mouse icons are normall...
i had this problem for many days and it got solved...hope this is useful...thnx
Jag

---

### Post by rfithen on 2011-09-27
This totally workd for me.

Acer Aspire 5532 Laptop, Ubuntu 10.04 - x86

Thanks.

> **spayman said:**
> [B]hi dude !
well first , can u tell me how u r changing ur mouse cursor ? lol 
you should try gcursor    applications > ubuntu store > search for (gcursor) 
install it , appears in system > preferances > cursor select :) 
i think that's the best way , if your not using it , well do !
peace ![/B]

---

### Post by rfithen on 2011-09-27
This also workd! on another machine.

> **Talys said:**
> It's been reported as a bug here: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/459647](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/459647)

For now, here's a temporary work around from that thread:  
From the command line, run 
```
sudo update-alternatives --config x-cursor-theme
```and manually select the cursor you want.  This will change the cursor icon, but size changes don't carry over.

---

