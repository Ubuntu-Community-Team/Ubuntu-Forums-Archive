---
title: "Problem installing Dropbox"
date: 2009-12-06
forum: General Help
---

### Post by 2benglish on 2009-12-06
I have downloaded and unpacked the dropbox .deb file on 9.10. The link to start it sits there in Applications-Internet.

When I try to start dropbox the following happens. A screen appears telling me to download the daemon. I go ahead with this. It downloads. Then it unpacks. That's it. After that there doesn't seem to be any change, but my computer carries on as if nothing had happened. I never get to the stage to enter my dropbox login details.

Anyone know what I'm missing?

---

### Post by raktarok on 2009-12-06
From a terminal, do this:
```
dropbox start -i
```
Does the dropbox icon appear in the notification area now? 
If there are any errors, post them here.

Also check if dropbox is in startup applications list. (System > Preferences > Startup Applications> If there is an entry, then you should see the panel icon once you relogin.

Hope this helped!

---

### Post by 2benglish on 2009-12-06
Unfortunately that command takes me through the same process of downloading and unpacking the daemon, but nothing after that.

I have now added Dropbox to the list of start up applications in preparation for when we get this solved!

---

### Post by 2benglish on 2009-12-07
Still no joy on this.
In my home directory I have a folder called .dropbox-dist. Does that help?

Every time I try to start dropbox it goes through downloading the daemon and after the depackage nothing seems to have changed.

Have I missed a setting somewhere?

---

### Post by 2benglish on 2009-12-07
[http://dev.squarecows.com/2009/10/16/installing-dropbox-in-ubuntu-9-10/]("http://dev.squarecows.com/2009/10/16/installing-dropbox-in-ubuntu-9-10/")

This didn't do it for me either.

---

### Post by howefield on 2009-12-07
What version of Ubuntu are you using ?

I had this issue on occasion with Jaunty, but with Karmic it has never failed to setup properly.

With Jaunty, I found rebooting after installing the initial deb file, then downloading daemon worked most of the time, but not all. Sometimes it took a few reinstalls to pick up.

---

### Post by 2benglish on 2009-12-07
9.10 and 9.10 studio, on different machines, but still I get the same result.

Reinstalling hasn't worked for me yet.
On both these machines I have my home folder on a separate partition. Could that have anything to do with things?

---

### Post by howefield on 2009-12-07
> **2benglish said:**
> ...On both these machines I have my home folder on a separate partition. Could that have anything to do with things?

No, I wouldn't think so. 

Guess I'd completely remove it, including the folders in your /home and sudo apt-get clean to remove any downloaded files in the cache, and try again.

---

### Post by AlanR8 on 2009-12-07
I had a few similar problems on 9.10 in the Beta testing phase but these days it all seems to work for me!

I, like you, set DropBox up as an application to start at launch but with the command:

Code:

> dropbox start -i

Do you have a short cut to DropBox on your "Start Menu" under the Internet folder? If you have that indicates all is well. I remember when I had a similar issue if I clicked the start menu short cut, for a short period of time, a few seconds, the DropBox icon would appear on the upper panel notification area. If I was quick and clicked on it, the wizard would kick off.

Putting DropBox in the start up group has worked for me for a while now

---

### Post by 2benglish on 2009-12-07
> Guess I'd completely remove it, including the folders in your /home and sudo apt-get clean to remove any downloaded files in the cache, and try again.

Thanks, but this didn't change anything.


> Do you have a short cut to DropBox on your "Start Menu" under the Internet folder?

Yes


> I remember when I had a similar issue if I clicked the start menu short cut, for a short period of time, a few seconds, the DropBox icon would appear on the upper panel notification area. If I was quick and clicked on it, the wizard would kick off.

I'm not getting any new icons appear in the notification area.


Have also started a thread on the dropbox forums.

---

### Post by YesSir on 2009-12-23
Same problems here, this solved mine:

[http://danielschultz.wordpress.com/2009/11/09/dropbox-behind-a-proxy/](http://danielschultz.wordpress.com/2009/11/09/dropbox-behind-a-proxy/)

Proxy problems... :(

---

### Post by profichiller on 2010-02-13
I had the same problem. The following Steps worked for me:
**[COLOR=Red]_But be careful. Please make a Backup of your Dropbox Folder before you do that._[/COLOR]**
[FONT=Arial][COLOR=Black]
[/COLOR][/FONT]```
sudo apt-get remove nautilus-dropbox
 rm -rf ~/.dropbox
 rm -rf ~/.dropbox-dist

```and after that

```

dropbox start -i
```Found here:[URL="http://forums.dropbox.com/topic.php?id=15791"]
http://forums.dropbox.com/topic.php?id=15791[/URL]

**[COLOR=Red][/COLOR]**

---

