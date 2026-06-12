---
title: "How to remove envelope icon from Indicator applet (10.04)"
date: 2010-05-03
forum: General Help
---

### Post by Flake Remix on 2010-05-03
I have already removed all the apps related to chatting/mail/social, but the icon doesn't disappear. If I remove Indicator applet I loose volume icon, which I actually want to keep.

[IMG]http://i40.tinypic.com/jaks4g.png[/IMG]

---

### Post by iamnotthemessiah on 2010-05-03
i think u go into synaptic and uninstall indicator-messages but keep indicator-sound, then restart the indicator applet

---

### Post by spiky001 on 2010-05-03
have a look here **#4** worked for me

[http://ubuntuforums.org/showthread.php?t=1469771&highlight=add+volume+control](http://ubuntuforums.org/showthread.php?t=1469771&highlight=add+volume+control)

---

### Post by Flake Remix on 2010-05-03
Thanks to you both :)

---

### Post by matbonucci on 2010-05-04
> **iamnotthemessiah said:**
> i think u go into synaptic and uninstall indicator-messages but keep indicator-sound, then restart the indicator applet
thank you, it worked

---

### Post by 13east on 2010-07-31
> **iamnotthemessiah said:**
> i think u go into synaptic and uninstall indicator-messages but keep indicator-sound, then restart the indicator applet

thx... worked perfectly... after removing "indicator-messages" just remove the applet from panel and add it back again... the evolution icon goes away.

---

### Post by QwUo173Hy on 2010-08-05
I also want to get rid of  the envelope, but I am not the only user of this machine so uninstallation is not an option. Is there another way I can remove it?

---

### Post by stinkeye on 2010-08-05
> **jarlath said:**
> I also want to get rid of  the envelope, but I am not the only user of this machine so uninstallation is not an option. Is there another way I can remove it?
Remove the Indicator Applet from the panel.
and add
```
gnome-volume-control-applet
```
to startup applications
Which will give you the old karmic style sound icon in the notification area upon restart.



Alt+F2 ...enter and run
```
gnome-volume-control-applet
```
to start immediately.

---

### Post by QwUo173Hy on 2010-08-05
Thanks Stinkeye. That's further than I want to go as I use the other elements of the Indicator Applet (Battery, Volume, Dropbox etc.) but I might try it out all the same.

---

### Post by TNAFan on 2010-08-19
sudo apt-get remove indicator-messages

killall gnome-panel

Done

---

### Post by zami on 2010-08-23
> **stinkeye said:**
> Remove the Indicator Applet from the panel.
and add
```
gnome-volume-control-applet
```
to startup applications
Which will give you the old karmic style sound icon in the notification area upon restart.



Alt+F2 ...enter and run
```
gnome-volume-control-applet
```
to start immediately.

Is there a similar applet available for the power indicator?  Separate from the indicator applet?  Then I could just ditch the indicator applet entirely.  

-zami

---

### Post by stinkeye on 2010-08-24
Do you mean a battery indicator?
You could have a look at using AWN as one of your panels.
Has many applets including a battery monitor.
I got rid of a lot of the stuff on the top panel and just use it as a
temperature and hardware monitor.
I use AWN as the bottom panel.
I'm on a desktop so it shows no batteries.

---

### Post by zami on 2010-08-24
Stinkeye,

I did mean a battery indicator.

Thanks for the suggestion and taking the time to upload a picture.  That's helpful!  I didn't realize AWN could be set to look like a panel like that.  I've only ever seen it used as a Mac-like doc (which doesn't really appeal to me).

Off to try AWN now... 

Thanks again!

-zami

---

### Post by Linfreak on 2010-09-26
Off-topic:

Stinkeye, your desktop looks really cool. Can you tell what theme you have used and also other UI tweaks you have done to make it look that good?
:)

Thanks,
Siva

---

### Post by stinkeye on 2010-09-26
> **Linfreak said:**
> Off-topic:

Stinkeye, your desktop looks really cool. Can you tell what theme you have used and also other UI tweaks you have done to make it look that good?
:)

Thanks,
Siva
The top panel is using **Hardware Monitor** and **sensors-applet** with conky
underneath in the same color.
The bottom panel is AWN.
Everything else on the desktop is drawn with conky except the cairo-clock.
Icons are [**_[COLOR="DarkRed"]Gartoon Redux   1.10[/COLOR]_**]("http://gnome-look.org/content/show.php/Gartoon+Redux?content=74841")

Conky is very customizable and I use scripts for the gmail and calendar, while the weather is from a local surf site using curl to 
download the image and display with conky.
If there is anything in particular you want or need a hand with, let me know. 
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

### Post by Linfreak on 2010-09-29
Thanks.. :)

---

### Post by Lutshow on 2010-10-10
> **TNAFan said:**
> sudo apt-get remove indicator-messages

killall gnome-panel

Done
now that's an answer!
thanks

---

### Post by Dex73 on 2010-10-15
> **stinkeye said:**
> Remove the Indicator Applet from the panel.
and add
```
gnome-volume-control-applet
```
to startup applications
Which will give you the old karmic style sound icon in the notification area upon restart.


Sweet! No more unnecessary app launcher that I never use cluttering up the panel!

---

### Post by ridgeland on 2010-10-17
Thank you iamnotthemessiah,
I went to Synaptics
found indicator-messages
removed it
rebooted
And now that useless to me envelope is gone.
Thank you.

---

### Post by djben75 on 2011-02-08
> **TNAFan said:**
> sudo apt-get remove indicator-messages

killall gnome-panel

Done

Thanks worked perfectly!!:p

---

### Post by Doogie128 on 2011-04-02
> **iamnotthemessiah said:**
> i think u go into synaptic and uninstall indicator-messages but keep indicator-sound, then restart the indicator applet

  This worked like magic,  thanks!

---

### Post by toineurlings on 2011-05-22
a better question... how do I return it after deleting it... I now use thunderbird with Imap and I want an email indicator...

I got the volume control in my indicator applet but it isn't represented in start-up applications

---

### Post by rocuan on 2011-10-19
> **TNAFan said:**
> sudo apt-get remove indicator-messages

killall gnome-panel

DoneQuick & Easy solution worked for me

---

### Post by ProntoAnthony on 2011-10-19
> **iamnotthemessiah said:**
> i think u go into synaptic and uninstall indicator-messages but keep indicator-sound, then restart the indicator applet

Thank you!

---

