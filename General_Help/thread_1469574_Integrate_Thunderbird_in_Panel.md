---
title: "Integrate Thunderbird in Panel"
date: 2010-05-02
forum: General Help
---

### Post by JugglinPhil on 2010-05-02
As you all know, one of the new features in 10.04 is the mail icon in the top right corner, through which you can access Empathy, Gwibber and Evolution.
Is there a way to integrate Thunderbird into this menu, so that it can be accessed quicker and that there is a notification coming up when a new mail is received like it is the case with evolution?

---

### Post by wilee-nilee on 2010-05-02
> **JugglinPhil said:**
> As you all know, one of the new features in 10.04 is the mail icon in the top right corner, through which you can access Empathy, Gwibber and Evolution.
Is there a way to integrate Thunderbird into this menu, so that it can be accessed quicker and that there is a notification coming up when a new mail is received like it is the case with evolution?

Yes, I use alltray it will put what ever you want in that notification area. sudo apt-get install alltray in the terminal or synaptic.

Just found this thread to use alltray and have it autostart it.
[http://ubuntuforums.org/showthread.php?t=974575](http://ubuntuforums.org/showthread.php?t=974575)

---

### Post by TheCheeze on 2010-05-02
There is also an extension called Firetray which actually shows new email counts and supports "close to tray" function.

---

### Post by JugglinPhil on 2010-05-02
> **wilee-nilee said:**
> Yes, I use alltray it will put what ever you want in that notification area. sudo apt-get install alltray in the terminal or synaptic.

Just found this thread to use alltray and have it autostart it.
[http://ubuntuforums.org/showthread.php?t=974575](http://ubuntuforums.org/showthread.php?t=974575)
Hm not quite what I am looking for. As you can see in the screenshot it does not really look good because the area around the icon does not match the theme, what I would prefer is not to add tb to the tray but to the mail icon sub menu on the right of the screenie.

---

### Post by JugglinPhil on 2010-05-02
If this was actually possible it would also be useful for other programs like Skype.

---

### Post by JugglinPhil on 2010-05-02
There must be a way to customize that applet..

---

### Post by scouser73 on 2010-05-02
Here you go: [[COLOR="Red"]**OMG! Ubuntu!: Thunderbird In Mail Applet**[/COLOR]]("http://www.omgubuntu.co.uk/2010/05/how-to-add-thunderbird-to-messaging.html")

---

### Post by JugglinPhil on 2010-05-02
Thanks I will give it a try. However it looks like it only lets you replace evolution with thunderbird, not having them both in there.

---

### Post by godsiem on 2010-06-08
I have followed the instructions (version #2 of the proposed solution) and I have now a nice integration... it notifies me of new messages (showing a green notification) and when I press the menu I have a notification of how many new messages and in which mail box they are... (see the image in attachment).

This is very nice! For the ones using the version #2, remember to get the latest version from the lp:libnotify-mozilla (using bzr branch lp:libnotify-mozilla), and then you have to make the xpi to install the addon in Thunderbird. To do this you compact all the files/directories inside (!! not the whole directory) the  libnotify-mozilla directory as .zip. Then change the extension of the compacted file from .zip to .xpi. After this, you can install the addon in Thunderbird... voilà!

I hope this helps other people. I found this very nice, since I am a Thunderbird/Pidgin user, and with this approach I manage to change the default from evolution/empathy to my preferred ones :)

 Cheers!

---

### Post by luceerose on 2010-06-10
Does this work with thunderbird 3.0.4 ?
I got the xpi file installed & still no tbird in the notifier.

---

### Post by godsiem on 2010-06-11
Hi,

It does work with Thunderbird 3.0.4... However, there are still some issues, namely the notification keeps on, the green envelope, after you have read all the messages in thunderbird. It stops if you click in the green envelope and in the notification of new message, or if you refresh your mail accounts manually... There is a thread in the authors thread that talks about this problem: [https://bugs.launchpad.net/libnotify-mozilla/+bug/429395](https://bugs.launchpad.net/libnotify-mozilla/+bug/429395), lets hope this will be updated soon.

Cheers!

---

### Post by zer010 on 2011-04-05
Ok, I'm running 10.04 and I just installed Thunderbird via ppa,
```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable && sudo apt-get update && sudo apt-get install thunderbird
```
So far, it works pretty good, but I was wondering about integration. I've seen two methods here, alltray and firetray. 
Which one is preferred?

---

### Post by nothingspecial on 2011-04-05
Fire tray works well.

But not with unity.

---

