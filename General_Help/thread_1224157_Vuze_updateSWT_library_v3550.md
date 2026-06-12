---
title: "Vuze update/SWT library v3550"
date: 2009-07-27
forum: General Help
---

### Post by Peacefulpieofdeath on 2009-07-27
I updated azureus/vuse to 4.2.0.4 and now i have this.

> Checking for Updates - added
Checking for Updates
    Azureus Core -     Core: latest_version = '4.2.0.4', file = 'Azureus4.2.0.4.jar.torrent'
    Azureus Core - Finished
    Core Patch Checker -     Adding update: Core Patch Checker
    Core Patch Checker - Finished
    SWT library -     SWT: current version = 3448, latest version = 3550
    SWT library -     SWT library loaded from "/usr/share/java" can't be automatically updated from version 3448 to 3550 (must be loaded from "/home/eric/.azureus"). Please see <A HREF="http://www.azureuswiki.com/index.php/SWT_Cant_Auto_Update">the wiki</A> for details.
    SWT library - Failed
Failed
    Azureus Core - Canceled
    Core Patch Checker - Canceled
    Non-mandatory plugins - Canceled
    Mandatory plugins - Canceled
    SWT library - Canceled
Checking for Updates - Canceled
Canceled
    Mandatory plugins -     Failed to load plugin details: Update check cancelled
    Non-mandatory plugins -     Failed to load plugin details: Update check cancelled
    Mandatory plugins - Failed
    Non-mandatory plugins - Failed
Failed
Finished


>     SWT library -     SWT: current version = 3448, latest version = 3550
    SWT library -     SWT library loaded from "/usr/share/java" can't be automatically updated from version 3448 to 3550 (must be loaded from "/home/eric/.azureus"). Please see <A HREF="http://www.azureuswiki.com/index.php/SWT_Cant_Auto_Update">the wiki</A> for details.
    SWT library - Failed

This is what my problem is... i have searched but i dont know how to update swt from 3448 to 3550...

please help... running ubuntu jaunty if that helps. Thanks

---

### Post by Peacefulpieofdeath on 2009-07-27
Please, i would appreciate the help.

---

### Post by Copernicus1234 on 2009-07-27
Im not sure what version the web site offers, but I run 4.2.0.2 and I dont get the offer to update when selecting "check for updates" from within the program, so... I dont know. How did you get this version?

---

### Post by Peacefulpieofdeath on 2009-07-27
I got it from automatic update just after updating to 4.2.0.2 from 3.1.1.0. I had found this fix

> Here’s a quick and dirty workaround.  After using the Vuze updater, run


 mkdir ~/bin
sed 's,/usr/share/java/Azureus2.jar,$HOME/.azureus/Azureus2.jar:/usr/share/java/commons-cli-1.1.jar:/usr/share/java/log4j-1.2.jar,' /usr/bin/azureus > ~/bin/azureus
chmod +x ~/bin/azureus


 log out and log in (to ensure ~/.profile will add ~/bin to your PATH), then run vuze again.

        


I'm guessing that this is my problem. Maybe a way to reverse this?

---

### Post by Peacefulpieofdeath on 2009-07-27
Ok now i changed swt.jar and swt-gtk-3.4.jar from /usr/share/java to ~/.azureus and the problem w/ swt seems done... but now plugins have problems.

> Checking for Updates - added
Checking for Updates
    Azureus Core -     Core: latest_version = '4.2.0.4', file = 'Azureus4.2.0.4.jar.torrent'
    Core Patch Checker -     Adding update: Core Patch Checker
    Azureus Core - Finished
    Core Patch Checker - Finished
    SWT library -     SWT: current version = 3448, latest version = 3550
    SWT library -     Adding update: SWT Library for gtk
    SWT library - Finished
    Mandatory plugins -     Failed to load plugin details: Plugin list load failed, I/O Exception while downloading 'http://azureus.sourceforge.net/update/pluginlist3.php', Connection reset
    Mandatory plugins - Failed
Failed
    Non-mandatory plugins -     Failed to load plugin details: Plugin list load failed, I/O Exception while downloading 'http://azureus.sourceforge.net/update/pluginlist3.php', Connection reset
    Non-mandatory plugins - Failed
Finished

---

### Post by friez on 2009-07-27
uninstall vuze and install the deb from [http://www.getdeb.net/app/Vuze](http://www.getdeb.net/app/Vuze)
 then ```
sudo chmod +x /usr/share/vuze/updateAzureus
/usr/share/vuze/updateAzureus
```
start vuze and update from there

---

### Post by Peacefulpieofdeath on 2009-07-27
I reinstalled but it still does the same thing... says that the plugin list failed to load...

can someone tell me if this work... go to the plugin installation wizard and go by list from sourceforge.net and can you tell me if you get this message.

> Failed to load standard plugin details, Plugin list load failed, I/O Exception while downloading 'http://azureus.sourceforge.net/update/pluginlist3.php', Connection reset


I think its the site that is down, even the [http://forum.vuze.com/](http://forum.vuze.com/) is down for me... can someone verify that also. thx

---

### Post by dlangeliers on 2009-07-29
Any movement on this issue?

I can successfully update Vuze, but now my 'Sites' are gone... so search results never come up regardless of the query.

I'm pretty sure the issue is SWT, but I'm not exactly sure how to check it. When I reinstall 4.2.0.2 everything works fine, as soon as i do the 4.2.0.4 update from within Vuze, I lose all search results.

Cheers,
-Dave

---

### Post by dlangeliers on 2009-07-29
FYI - Just found this post on the Vuze forums:

[http://forum.vuze.com/thread.jspa?threadID=84182&tstart=0]("http://forum.vuze.com/thread.jspa?threadID=84182&tstart=0")

---

### Post by raiwo on 2009-07-30
i think it's rather sad we have so old version of vuze in repos, who is responsible of that?

:confused:

---

### Post by v1nsai on 2009-08-02
I'm having a problem updating vuze too, but mine is telling me that /usr/share/vuze is read-only so it can't be modified.  I've tried sudo chown v1nsai /usr/share/vuze then restarting but same problem.  Everything seems to be working (NOW, been ******* with it for at least an hour >.< ) so I'm not too worried about it, but wanted to cast my lot with the rest of you guys having vuze update probs.

---

### Post by arjmage on 2009-08-29
I had the same problem. I used the getdeb packaged and upgraded to vuze 4.2.0.2 and then the updates would throw up the SWT and core 4.2.0.8 packages. But it would be unable to apply the patch.

/usr/share/vuze is not writable was a problem, and the command

```
sudo chown -R 777 /usr/share/vuze
```

did NOT help the problem. Each time it would start and do the same update attempt again.

However, this command DID help and now vuze updates itself without trouble

```
sudo java -cp ./plugins/azupdater/Updater.jar org.gudy.azureus2.update.Updater updateonly `pwd` ~/.azureus
```

As an aside... I'm no fan of Vuze's graphical display. I like the azureus style simplicity better, and so for others who also prefer that -- go to the preferences > interface and then there is a choose UI option, that lets switch back to the classic view. you may have to enable advanced or expert preferences view for this, I'm not sure.

Hope that helps somebody.

---

### Post by lokutus25 on 2009-10-07
I worked out the update when I noticed that I had both the azureus and vuze packages installed, coming from repos. Maybe I had both from an distro upgrade.
I just did:
> dpkg --remove vuze
dpkg --removed azureus
aptitude install vuze

Running vuze from bash i had a warning to change the /usr/share/vuze permission to enable updates.
> chmod 777 /usr/share/vuze
After that I followed the vuze update procedure and worked nice.
Hope it help.

---

### Post by Tanner2007 on 2010-05-04
Try to reinstall this package 

remove it, install it worked for me

libswt-gtk-3.5-java

---

