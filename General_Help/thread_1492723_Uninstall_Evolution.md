---
title: "Uninstall Evolution"
date: 2010-05-25
forum: General Help
---

### Post by Ron O on 2010-05-25
Can I safely remove Evolution from Ubuntu Lucid if I use the Software Center or Synaptic? 

Can I do so and still retain a system clock in the taskbar? 

Can I assume that any dependencies affecting other applications will be left in place?

---

### Post by eeried on 2010-05-25
Hello Ron O,

Best thing to do is launch Synaptic and search for Evolution. Mark various packages for complete removal and look carefully at what will be removed as well.

Then go to each of the programs or lib you can do without and mark them for complete removal. Do read the description for each program or lib before uninstalling.

For instance, I haven't removed something called like "evolution data server" (not the exact name) because it removed the calendar applet which I suspect is the one in the upper bar :confused:

Better remove less than too much :-)

---

### Post by Ron O on 2010-05-25
You've confirmed my fears. I tought Synaptic would not uninstall any library that is used by another application. I f you have to analyse it personally, it is too risky for someone at my level in Linux. I think I'll leave Evolution in place, remove the panel icon, and configure it's replacements with launchers and/ or preferred applications (or whatever it is called).

---

### Post by wojox on 2010-05-25
This will uninstall Evolution and leave what's needed:

```
sudo apt-get remove evolution evolution-common evolution-couchdb evolution-exchange evolution-indicator evolution-plugins evolution-webcal
```

---

### Post by SoFl W on 2010-05-25
I removed it from another install but I read this and probably wont be doing it again:
> **Never remove any application that's part of the  default installation of Ubuntu**

3. Even when you never use a particular default application: don't remove it. Reason: the default installation is an intertwined system that's dependent on shared supporting files, which makes the operating system run stable. 

When you remove a default application, you run a  risk of seriously damaging the system. With some default applications this  risk is bigger than with others, but it's best to avoid this risk  altogether.

If you want to, you can remove an unused application  from the menu, but don't remove it from the system.

This limitation applies only to those applications, that are part of the default installation of Ubuntu. Applications that you've added yourself, you may remove without problems.[Seven fatal mistakes]("http://sites.google.com/site/easylinuxtipsproject/fatalmistakes")[]("http://sites.google.com/site/easylinuxtipsproject/fatalmistakes")

---

### Post by eeried on 2010-05-26
> Never remove any application that's part of the default installation of Ubuntu

This is what I don't like about Ubuntu. No software like an email client should be part of the system. We should be able to remove it completely without any collateral damages.

Many thanks wojox for your suggestion for the removal of Evolution. Have you noticed any adverse effects? I'll give it a try anyway.

---

### Post by eeried on 2010-05-27
Hello,

After rummaging in Synaptic, I would suggest this:

```
sudo aptitude purge evolution evolution-common evolution-couchdb evolution-exchange evolution-indicator evolution-plugins evolution-webcal libedata-cal libedata-book libebackend libegroupwise libexchange-storage libgdata-google libgdata
```

libgdata-google, libgdata: Google services.

What do you think?

Always check if one package isn't linked to many others that you may not wish to uninstall, like evolution-data-server-common which is linked to gnome-panel, gnome-session (sounds ominous) and many other little programs.

I'm not sure you can remove evolution-data-server-common and then reinstall gnome-panel, etc. without evolution-data-server-common being reinstalled as well.

If you have a go at it, do all the removal and reinstalling from a tty (Ctrl-Alt-F1) and before logging in because you may loose some important part of GNOME and see your system act very weird. If you act before the X server is running, you are much freer but you may also break the system a little.

---

### Post by Ron O on 2010-05-27
This is what I anticipated when I posed my original question. Remember the Windows lawsuit when Gates maintained that Internet Explorer could not be broken away from Windows? I expected better from Ubuntu. It also makes me uncomfortable with the package managers that are suposed to retain the shared dependencies when you do an uninstall.

If we have to keep Evolution on board, the least Ubuntu could do is is get the Evolution team to fix the bugs that have been complained about since Feisty (as far back as I go) or before- a calendar program with alerts that are utterly unreliable. That's why I wanted to uninstall Evolution, not to recover hard drive space, but because the application is a disgrace. Sorry to put it so indelicately.

---

### Post by howefield on 2010-05-27
> **Ron O said:**
> Remember the Windoze lawsuit when Gates maintained that Internet Explorer could not be broken away from Windoze?

This has what to do with Ubuntu and Evolution ?

> If we have to keep Evolution on board,

If you feel so bad about Evolution, there are many options open to you that do not include having the application on your system.

> but because the application is a disgrace. Sorry to put it so indelicately.

You must be due a refund. ;-)

---

### Post by lisati on 2010-05-27
> **Ron O said:**
> 
If we have to keep Evolution on board, the least Ubuntu could do is is get the Evolution team to fix the bugs that have been complained about since Feisty (as far back as I go) or before- a calendar program with alerts that are utterly unreliable. That's why I wanted to uninstall Evolution, not to recover hard drive space, but because the application is a disgrace. Sorry to put it so indelicately.

Have you filed a bug report at [launchpad]("http://launchpad.net/")?

---

### Post by timgood on 2010-05-27
> **lisati said:**
> Have you filed a bug report at [launchpad]("http://launchpad.net/")?

I filed reports about a bug in Evolution that deletes all mail (junk and not junk) in the deleted items folder when junk is purged. This is a known bug that goes back over 5 years. Nothing has been done about it and the bug is still there. As a result, I lost mail. Evolution could be so much more than it is if bugs like this were fixed.

---

### Post by jerrrys on 2010-05-27
> **wojox said:**
> This will uninstall Evolution and leave what's needed:

```
sudo apt-get remove evolution evolution-common evolution-couchdb evolution-exchange evolution-indicator evolution-plugins evolution-webcal
```

i just did it.  and it did a better job of removing than my old way...Thanks

---

### Post by wojox on 2010-05-27
> **eeried said:**
> Hello,

After rummaging in Synaptic, I would suggest this:

```
sudo aptitude purge evolution evolution-common evolution-couchdb evolution-exchange evolution-indicator evolution-plugins evolution-webcal libedata-cal libedata-book libebackend libegroupwise libexchange-storage libgdata-google libgdata
```

libgdata-google, libgdata: Google services.

What do you think?

Always check if one package isn't linked to many others that you may not wish to uninstall, like evolution-data-server-common which is linked to gnome-panel, gnome-session (sounds ominous) and many other little programs.

I'm not sure you can remove evolution-data-server-common and then reinstall gnome-panel, etc. without evolution-data-server-common being reinstalled as well.

If you have a go at it, do all the removal and reinstalling from a tty (Ctrl-Alt-F1) and before logging in because you may loose some important part of GNOME and see your system act very weird. If you act before the X server is running, you are much freer but you may also break the system a little.

I'm not to sure about those libraries. I would just leave them. Evolution-data-server is linked to gnome-panel because I think I remember reading it is used to run the clock/calendar.

---

### Post by jerrrys on 2010-05-27
so far no surprises

---

### Post by dcstar on 2010-05-27
> **Ron O said:**
> 
.........
If we have to keep Evolution on board, the least Ubuntu could do is is get the Evolution team to fix the bugs that have been complained about since Feisty (as far back as I go) or before- a calendar program with alerts that are utterly unreliable. That's why I wanted to uninstall Evolution, not to recover hard drive space, but because the application is a disgrace. Sorry to put it so indelicately.

I don't seem to have any issues with my Calendar notifications - when this changed behaviour many releases ago I just had to adapt to the different way of doing things, but that is the way with any software, and various Evolution bugs that I have reported have been fixed or resolved fairly promptly.

If you don't want to use it then simply DON'T USE IT, there is no need to uninstall it and complain that it is difficult to do.

Oh, and I have been using Evolution quite successfully since I started using 4.10 in late 2004.

---

### Post by yippy on 2010-05-28
> **dcstar said:**
> If you don't want to use it then simply DON'T USE IT, there is no need to uninstall it and complain that it is difficult to do.

Evolution takes hard drive space.

If you ever set it up and then decide not to use it, the data server polls periodically and sucks up system resources.

It leaves a "Set up mail..." line in the notifier, and Ubuntu provides no way to change that without going to the console.

But finally, why have an application on your system that you're not using?  That's silly.

I completely agree with the OP.  Evolution would be awesome if it worked right, but it's been in a mediocre half-built state since, well, Warty Warthog.  Every year or two I come back to it to see if it's worth using yet, but after a couple of days I can't stand it anymore and get rid of it again.

I used Thunderbird with Lightning for several years, but now I'm finding pure Gmail is the best tool on Linux so far for integrating email, calendar, and tasks.  Sorry, Evolution, you're not even a contender anymore.

---

### Post by jerrrys on 2010-05-28
the only reason i removed it was back in 8.04 days it was buggy, and now just see no reason to bring it back to life...

---

### Post by Ron O on 2010-05-28
I'd like to see how you are using the calendar if the notifier is not giving you trouble. I had an appointment for 10AM one day and set an alarm to activate one day in advance (10 AM the previous day). At 8 PM on the evening prior to the appointment,  I received no notification of the next morning's appt. What good is that? See also bug 147163 opened in 07 that still has current entries.

I am not "complaining" about the difficulty of removing Evolution, just trying to find out if it can be done safely. All this talk about if you don't like it, don't use it and you must be due a refund is counterproductive. I guess the launchpad bug reporting system could save a lot of time and effort if they stopped working on issues and just put a banner on the screen that says "If you don't like it, don't use it!".

The only reason I went to the Forums rather than to the bug reporting system was to see what other people might have encountered trying to remove this application. I have given up on the prospects of it EVER being fixed.

---

### Post by jerenept on 2010-05-28
You need to read what is being uninstalled, look at every depedency being removed. Apparently, back in 8.10 days, gnome-panel depended on evolution. I do not think that removing evolution is necessary though. It doesn't take up much space, and, if not running, it takes up no CPU.

If u don't like evolution, try Sunbird. It is in the repos. Install it from Software Center.

---

### Post by spike_naples on 2010-06-09
Thank you for this. I was able to install Tunderbird and am quite pleased with it. I was also able to uninstall Evolution and so far, after some days I have not noticed any glitches.

---

### Post by germanix on 2010-06-09
This is the way I did it and it works perfectly for me:
Open up the terminal and type the following:
sudo aptitude purge indicator-messages 
then press enter
you will be asked for your password.
Enter your password, it will then ask if it should continue, answer with y for yes.
This will remove the envelope icon from the panel. You will not see the immediate removel but it will not be there anymore after a newstart.

---

### Post by Ron O on 2010-06-10
Jerenept-- I have never felt the need to analyze dependencies for a program removal because I thought that Apt and Synaptic's reason for existing was largely to do just that. Besides, most of us do not have the knowledge and skills to do this. I guess I have just been lucky so far in removing packages.

Sunbird IS listed in the Software Center in Lucid, but I don't know why. You cannot install it since it has been de-certified for use in Lucid. Too bad too. That's what I was using before this upgrade, and it's a great application. There are a few threads you can find in Google on this. 

Another app that is in Synaptic is Preload, a read-ahead daemon that I used in Jaunty that significantly increased my applications speed (not just boot-up speed like the Ubuntu read-ahead routine). It's in there, but it does not work in Lucid.

---

### Post by Ron O on 2010-06-10
germanix- I am assuming that this works AFTER you have uninstalled Evolution?

It's a great tip- getting that notification icon for a program I will never use was one reason for wanting to uninstall Evolution to begin with.

BTY. XFCE's tiny calendar applet called Orage that comes with Xubuntu seems to work fine in Ubuntu. Very lean, and I haven't missed a notification yet.

---

### Post by germanix on 2010-06-10
> **Ron O said:**
> germanix- I am assuming that this works AFTER you have uninstalled Evolution?

It's a great tip- getting that notification icon for a program I will never use was one reason for wanting to uninstall Evolution to begin with.

No, your assumption is incorrect. Actually this was all that I did. I wanted to envelope icon to go as I do not use Evolution. This did the trick for me. I do not know if this command also deletes other packages connected to Evolution or not and I did not want to fiddle with it. "Do not fix a system that is working!" The envelope was gone and all else works, so that is good enough for me.

---

### Post by Ron O on 2010-06-10
When I right click on the envelope and click about, I get "Indicator Applet 0.3.7" which also contains a speaker icon for sound and adds the Amarok icon when I start Amarok music player, and probably a lot of other applications as well. Since your workaround is only a purge, I think it leaves the indicator applet in place and functional, so if I were to open Evolution again (which I won't, the envelope would come back again.

---

### Post by spike_naples on 2010-06-14
Still no problem after some days plus four days from posting my first reply. 

Thanks people. You really are a Godsend to us less educated about Ubuntu/Linux.

---

### Post by astowe32 on 2010-09-13
Has anyone done a dist upgrade after removing the evolution packages? Wondering if the dependencies break this functionality due to broken dependencies.

---

### Post by ST.x on 2010-10-01
> **astowe32 said:**
> Has anyone done a dist upgrade after removing the evolution packages? Wondering if the dependencies break this functionality due to broken dependencies.

Yeah I'm wondering about this before upgrading to Maverick.

---

### Post by migs73 on 2010-10-01
Removed:- Hadn't read full thread. Forgot I don't have Autopager installed on my XP firefox!!

---

### Post by migs73 on 2010-10-01
Removed;- Duplicate post (I'm not doing very well on this one!)

---

### Post by spike_naples on 2010-10-20
> **spike_naples said:**
> Thank you for this. I was able to install Tunderbird and am quite pleased with it. I was also able to uninstall Evolution and so far, after some days I have not noticed any glitches.

5 months have passed and so far the installation of Evolution has not caused any negative effects. At least that's how I feel about it. Everything has been running smooth and everything seems to integrate and coexist harmoniously.

I'm happy with my Thunderbird mail client. 

Thank you!

---

### Post by ST.x on 2010-10-20
> **spike_naples said:**
> 5 months have passed and so far the installation of Evolution has not caused any negative effects. At least that's how I feel about it. Everything has been running smooth and everything seems to integrate and coexist harmoniously.

I'm happy with my Thunderbird mail client. 

Thank you!

Did you also upgrade to Maverick?

Cheers

---

### Post by spike_naples on 2010-11-12
Just a curious question, I just did a fresh install of Maverick and I was wondering if this wourk work just as well as in previous versions of Ubuntu?

---

### Post by ssulaco on 2010-11-12
> **germanix said:**
> This is the way I did it and it works perfectly for me:
Open up the terminal and type the following:
sudo aptitude purge indicator-messages 
then press enter
you will be asked for your password.
Enter your password, it will then ask if it should continue, answer with y for yes.
This will remove the envelope icon from the panel. You will not see the immediate removel but it will not be there anymore after a newstart.

> **germanix said:**
> No, your assumption is incorrect. Actually this was all that I did. I wanted to envelope icon to go as I do not use Evolution. This did the trick for me. I do not know if this command also deletes other packages connected to Evolution or not and I did not want to fiddle with it. "Do not fix a system that is working!" The envelope was gone and all else works, so that is good enough for me.
Couldn't you just right click the evolution icon and remove from panel?

---

### Post by astowe32 on 2010-11-12
> **ST.x said:**
> Did you also upgrade to Maverick?

Cheers

I did and it still is working fine.

  Allen...

---

### Post by CoolJohnB on 2010-11-12
When I uninstalled evolution I had no problems but strangely the sound/speaker icon has gone from the top panel, anyone any ideas how I can get it back?

---

### Post by fredthomke on 2010-12-18
When I right-clicked and removed the Mail icon, I too lost the sound icon -- why the heck mail was associated with sound makes no sense to me.  However, I poked around Google and found a way to put back a Sound icon so I can adjust speaker levels:

1) Click on System > Preferences > Startup Applications


2) In the Startup Programs tab, click the Add button


3) In the Add Startup Program dialog box type the following:

Name:  Sound Icon (or whatever you want to name this thing)

Command: gnome-volume-control-applet

Comment: Controls speaker level (or whatever you want to write, or leave blank)


4) Click the Save button


5) Make sure your new item "Sound Icon" has a checkmark otherwise it won't start at the next boot.  Click Close.

Reboot to see your Sound Icon in the notification area of the panel.

---

