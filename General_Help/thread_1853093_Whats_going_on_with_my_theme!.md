---
title: "Whats going on with my theme!?"
date: 2011-10-01
forum: General Help
---

### Post by iNeed Help on 2011-10-01
This just started happening... It changes to a theme I never even used. It has a grey top bar and when I try to change back, only window borders change, the top (Applications, Places, System, bar) is still this ugly grey one? Help?

[IMG]http://i.imgur.com/LxP5G.png[/IMG]

---

### Post by holy_bazooka on 2011-10-01
Go to System -> Administration -> Additional Drivers and see if you need to actvate anything.
Also if running VBox then check [this]("https://forums.virtualbox.org/viewtopic.php?f=6&t=41127&p=185018").

---

### Post by iNeed Help on 2011-10-01
> **holy_bazooka said:**
> Go to System -> Administration -> Additional Drivers and see if you need to actvate anything.
Also if running VBox then check [this]("https://forums.virtualbox.org/viewtopic.php?f=6&t=41127&p=185018").

I am running VMware, not sure if thats the same. I'll try to see if I need to activate anything.
Nope... :( They're all activated.

---

### Post by holy_bazooka on 2011-10-01
Well I am running VBox and it hasn't helped me either.
Ugly Theme is still there.
:(

---

### Post by CatKiller on 2011-10-01
Press Alt-F2 and run gnome-settings-daemon and then nautilus -q.

---

### Post by foureyesboy on 2011-10-01
> **iNeed Help said:**
> I am running VMware, not sure if thats the same. I'll try to see if I need to activate anything.
Nope... :( They're all activated.

Have you installed the VMware Tools on the guest OS?

---

### Post by iNeed Help on 2011-10-01
> **foureyesboy said:**
> Have you installed the VMware Tools on the guest OS?

I tried but it keeps giving me an error. How do I do it? I may be doing something wrong.

---

### Post by iNeed Help on 2011-10-01
> **CatKiller said:**
> Press Alt-F2 and run gnome-settings-daemon and then nautilus -q.

I'm confused, I ran those, and nothing happened?

---

### Post by Frogs Hair on 2011-10-01
See this link for a possible solution . [http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

---

### Post by iNeed Help on 2011-10-01
> **Frogs Hair said:**
> See this link for a possible solution . [http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

Awww. D: Didnt work.

---

### Post by iNeed Help on 2011-10-01
Anyone? :p

Man, this sucks. I have to use stupid Windows 7... I hate this ugly theme D:

---

### Post by iNeed Help on 2011-10-01
Seriously...???

---

### Post by arcturus.red on 2011-10-01
Have patience, it takes a long time to get a reply on this forum. 

Have you tried the basic stuff? Like customising the theme and changing the option in the "control" tab?

If that doesn't work....

In the gnome-setting-daemon.desktop file that you edited, did you try changing the sleep value to something higher?

---

### Post by cariboo on 2011-10-01
Please wait at least 24 hours before bumping your thread, we are all volunteers here, and it may be that the person that can answer your question hasn't seen it yet.

---

### Post by towheedm on 2011-10-02
This looks like you have 'Ubuntu Classic Desktop' selected at the Login screen.  Check at the buttom of the login screen and select the Ubuntu Desktop entry.

---

### Post by Krytarik on 2011-10-02
> **towheedm said:**
> This looks like you have 'Ubuntu Classic Desktop' selected at the Login screen.  Check at the buttom of the login screen and select the Ubuntu Desktop entry.
This is actually quite funny! :D
If one doesn't take the *real* point of this thread too serious. ;-)

---

### Post by towheedm on 2011-10-02
> **Krytarik said:**
> This is actually quite funny! :D
If one doesn't take the *real* point of this thread too serious. ;-)

So what's so funny and what is the real point of this thread?

The screenshot looks rather familiar, like when I have to run Natty using the Classic Desktop because my hardware does not run GNOME 3 or Unity or whatever very well.  Also, I'm not able to change the theme when in classic desktop.

---

### Post by Krytarik on 2011-10-02
> **towheedm said:**
> The screenshot looks rather familiar, like when I have to run Natty using the Classic Desktop because my hardware does not run GNOME 3 or Unity or whatever very well.  Also, I'm not able to change the theme when in classic desktop.
So, you are presented with the fallback theme, too?
(which is Raleigh, btw. - under "Customize -> Controls")

---

### Post by towheedm on 2011-10-02
> Also, I'm not able to change the theme when in classic desktop.My mistake, it can be changed, have done so my sister's machine which I've set to Classic Desktop although her machine runs GNOME 3 and Unity rather well.  I just don't have the inclination to learn Unity at the moment.
> 
So, you are presented with the fallback theme, too?So it's referred to as the fallback theme in Ubuntu as well.  Thought it was only in Fedora 15.

---

### Post by Krytarik on 2011-10-02
> **towheedm said:**
> So it's referred to as the fallback theme in Ubuntu as well.  Thought it was only in Fedora 15.
I'm not talking about the Gnome Fallback Session ;) (which can be installed in Oneiric 11.10 now, too).

---

### Post by towheedm on 2011-10-02
Ah, thanks for that.  I now understand there's a difference between the fallback theme and session.

So Ubuntu's Classic Desktop is not really a fallback session, just a different DE.

---

### Post by Krytarik on 2011-10-02
> **towheedm said:**
> So Ubuntu's Classic Desktop is not really a fallback session, just a different DE.
To be exact, it's not even that :razz: , as Unity is based on Gnome (which is the DE part here), it's just a plugin of Compiz, and Gnome Panel is not coming up.

---

### Post by towheedm on 2011-10-02
Now I'm lost.  'Ubuntu Desktop' as selected from GDM uses GNOME 3 and Unity as the DE, 'Ubuntu Classic Desktop' as selected from GDM uses GNOME 2.32 as the DE.

What is a plug-in of Compiz, Unity?  If it's a plug-in of Compiz, why is it a top level component of the 'ubuntu-desktop' meta-package?  Isn't this why removing Unity removes the ubuntu-desktop package?

---

### Post by CatKiller on 2011-10-02
No it doesn't. It uses Gnome 2 & Compiz.

Included in ubuntu-desktop just means installed-by-default.

---

### Post by iNeed Help on 2011-10-02
So still no definite fix? ... :(

Well, could it be that I tried to install compiz, but since VMware doesn't support compiz, it messed up the gnome stuff?

---

### Post by foureyesboy on 2011-10-02
> **iNeed Help said:**
> I tried but it keeps giving me an error. How do I do it? I may be doing something wrong.

Just saying you encounter an error instead of telling what exactly the error message is doesn't give too much information for people here trying to help.

What version of VMware are you using?  There is blogging mentioning about VMware Tools problem of 3.1.2 with kernel 2.6.38 which is used in Natty and that the problem is resolved in 3.1.3.

---

### Post by Krytarik on 2011-10-02
Please see this earlier thread, it's about VMware being part of the cause, too:

[http://ubuntuforums.org/showthread.php?t=1807459](http://ubuntuforums.org/showthread.php?t=1807459)

If you want to try LightDM as a workaround, see here how to install it:

[http://www.tuxgarage.com/2011/06/testing-new-login-manger-for-ubuntu.html](http://www.tuxgarage.com/2011/06/testing-new-login-manger-for-ubuntu.html)

---

### Post by iNeed Help on 2011-10-03
I am running VMware v3.1.4

I can't install vmware tools or whatever because I keep getting an error.

---

### Post by Krytarik on 2011-10-03
> **iNeed Help said:**
> I can't install vmware tools or whatever because I keep getting an error.
Again, really!? Guess you need to figure it out on your own eventually, if you are either not willing or able to provide any details. This is in stark contrast to your earlier repeatedly crying for help, btw. But good luck! Did you have a look at my suggestion, btw.?

---

### Post by iNeed Help on 2011-10-04
Yeah, I looked at your posted threads, nothing worked.. D:

It says "There was a problem updating the VMware tools. If this problem persists contact VMware support or your system administrator"
I couldn't get it EXACTLY because the message it in a error dialog, and I had to close it if I wanted to do anything.

---

### Post by iNeed Help on 2011-10-05
I INSTALLED VMWARE TOOLS!

I installed it but nothing happened in Ubuntu... Those files are supposed to show up right?

---

