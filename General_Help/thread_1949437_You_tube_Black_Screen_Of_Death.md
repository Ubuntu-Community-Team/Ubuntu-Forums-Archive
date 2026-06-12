---
title: "You tube Black Screen Of Death"
date: 2012-03-30
forum: General Help
---

### Post by Agent26 on 2012-03-30
You tube Black Screen Of Death...
Hi there all, today I have encountered a problem...My flash player has stopped working. It is not a problem with the player as I reinstalled it. After a little searching I found this solve from the Gogle people themselves but unfortunatly its zero use to me as they have left out Linux users for a fix.
Here it is..

They strive to make it better but only seem to support the locked down rip off operating systems.
[http://support.google.com/youtube/bin/answer.py?hl=en&answer=1209379](http://support.google.com/youtube/bin/answer.py?hl=en&answer=1209379)

Has anybody else had this prob.
Oh Youtube was fine until yesterday too.

Thankyou

---

### Post by winh8r on 2012-03-30
You might like to try following the link in my sig below "Help with Flash" and install and run the Flash Aid wizard, to ensure that your flash set up is optimized for your system.

Hope this helps.

---

### Post by Agent26 on 2012-03-30
Thanks Winh8r, Thats got the flash on fire fox up and running again but i am an opera user.
What would be lovely is a deb file for the plugin for opera.

Or even better a deb flash player installation file.
I can only find the yums and tar but dont know what to do with them. I know im suppost to extract them, copy into my system somewhere but it's a bit more technical than that.

---

### Post by Agent26 on 2012-03-30
Oh dear. My flash player has packed up again. 
theres nothing I can do now. It looks like they are trying to force me onto windows again.
Why cant google sort it out and stop condensing everyone into one place and forcing people to all have Windows.. something is a misss. If they hadnt optimised  for the windowsI could still watch vids.
Sorry rant over. 
Perhaps I will never use a flash again.

---

### Post by GreatDanton on 2012-03-30
Maybe you should try this:
[http://ubuntuforums.org/showthread.php?t=1942988&highlight=youtube](http://ubuntuforums.org/showthread.php?t=1942988&highlight=youtube)

Cheers

---

### Post by lovinglinux on 2012-03-31
> **Agent26 said:**
> Thanks Winh8r, Thats got the flash on fire fox up and running again but i am an opera user.
What would be lovely is a deb file for the plugin for opera.

Or even better a deb flash player installation file.
I can only find the yums and tar but dont know what to do with them. I know im suppost to extract them, copy into my system somewhere but it's a bit more technical than that.

It works for Opera as well. Just install using Flash-Aid and Opers will use the same plugin.

> **Agent26 said:**
> Oh dear. My flash player has packed up again. 
theres nothing I can do now. It looks like they are trying to force me onto windows again.
Why cant google sort it out and stop condensing everyone into one place and forcing people to all have Windows.. something is a misss. If they hadnt optimised  for the windowsI could still watch vids.
Sorry rant over. 
Perhaps I will never use a flash again.

Disable hardware acceleration in Flash settings. Open an YouTube video, right click on the black screen, select Settings.

---

### Post by Agent26 on 2012-03-31
Hi  Loving Linux and all else who have tried to help me.
Just my luck that the flash aid doesn't work for me nor does the lower quality add on , Veiwtube script reinstalling Frefox/Opera don't either. I have come to the conclosion that it's something up with my computer. I am unable to right click the black screen as I just get the box that comes up when you click any web page and no flash settings.
Whats weird is this problem just spang up the day before yesterday.

I have an idea but I don't have the coding knolage to do it.
Does anybody know the code to disable this hardware acceleration without the graphical inter phase.
P.S I have read all th suggested threads to to no avail. If this doesn't work It must be my computer.

---

### Post by lovinglinux on 2012-03-31
> **Agent26 said:**
> Hi  Loving Linux and all else who have tried to help me.
Just my luck that the flash aid doesn't work for me nor does the lower quality add on , Veiwtube script reinstalling Frefox/Opera don't either. I have come to the conclosion that it's something up with my computer. I am unable to right click the black screen as I just get the box that comes up when you click any web page and no flash settings.
Whats weird is this problem just spang up the day before yesterday.

Do you have an nVidia card? It seems this problem only affects nVidia users. I running Flash on Opera, Firefox and Chrome fine here.

Perhaps you could try to downgrade. you can get old deb files from [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/)

Be aware that old versions will probably be insecure. So, use NoScript to block flash elements from untrusted sites.

---

### Post by lovinglinux on 2012-03-31
> **Agent26 said:**
> Does anybody know the code to disable this hardware acceleration without the graphical inter phase.

Try this:

> **mc4man said:**
> I'd go with an older flash version but if you wish to disable hw acceleration in the flash settings you must do it in the player while it's  in fullscreen
(scrollbars make the settings box unclickable

If that doesn't work, then try this:

Open /etc/adobe/mms.cfg with an editor using admin privileges.

```
gksudo gedit /etc/adobe/mms.cfg
```

Add this line:

```
EnableLinuxHWVideoDecode=1
```

This doesn't disable HW acceleration and probably will make flash unstable, but it is a workaround.

---

### Post by Agent26 on 2012-04-25
Hi there Loving Linux, First a quick apology as I took ages to reply. I totally forgot and was getting used to no player.
The problem is now solved just today and you gave some exelent advice.
I do have a NVIDA card and I changed it in an experiment to an older one and that sorted the flash player by adobe????? But I dicided to get control of my NVIDIA card as it is better.
My Solotion was to get rid of Adobe flash altogether and get the SWFDEC flash player available in the software center.
But thankyou for those codes. Thats More codes learnt and in my book I have for linux. I find building up a book of solotion codes is very handy!

Thank you to all who helped with ideas and sorry again for taking ages to reply.

I will just add that the problem with adobe seems to be paticually common and hard to fix so my advice to anyone who has a simular problem is to forget the Adobe player and get the mentioned SWFDEC from the software center....easy.:D:D:D
I will mark this thread solved.
Thankyou.

---

