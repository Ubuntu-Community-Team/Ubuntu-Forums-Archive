---
title: "running programs"
date: 2011-05-24
forum: General Help
---

### Post by magodiafano on 2011-05-24
Hello I have a problem with the running applications in particular with skype.
When I press X, skype continues to run even if for awn it's closed. So I have not ways to use the same running skype ( i should go on  "system monitor" but it's awkward)

I remember that in ubuntu 10 (now I am using 11.04) when I opened skype, a little icon appeared on the upper right of the panel... how can I do the same thing in ubuntu 11.04?

---

### Post by jamesjenner on 2011-05-24
Hmm interesting. I run skype and I get the indicator on the top right no problems at all. From memory when I first upgraded to 11.04 it didn't display but now it does. I don't believe I did anything other than install the regular updates. Maybe there was a fix in one of the various updates over the last few weeks.

Have you installed all the updates and what version of Skype are you running? In the meantime you should be able to click on the menu and choose exit.

Cheers,

James.

---

### Post by magodiafano on 2011-05-24
I have installed all the updates and I have tried to uninstall and then install skype but the problem comes back.
Do you know a way to make skype icon appeared on the top right as ubuntu 10?

---

### Post by magodiafano on 2011-05-24
is there someone could help me?

---

### Post by jamesjenner on 2011-05-24
> **magodiafano said:**
> I have installed all the updates and I have tried to uninstall and then install skype but the problem comes back.
Do you know a way to make skype icon appeared on the top right as ubuntu 10?

Hmm. I noticed last night that my skype icon wasn't coming up anymore and I had an error in one of my logs, but I didn't have a chance to investigate. I could have sworn it was working. So looks like I'm in the same boat as you. I'll have a look tonight (it's now just past 8am for me) and post some further information to see if someone can provide some assistance.

---

### Post by Benchrest on 2011-05-24
Your not alone. I am using Ubuntu Classic if that makes a difference. At first I would have the Skype icon but then it was intermittent and then not at all. I have to go to system monitor to stop Skype. In the lower left of the Skype panel is a blue icon clicking on it gives an option to quit. Also I noticed the icon up above would disappear when I use Skype.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Skype is a pain sometimes. I use this:

[http://ekiga.org/](http://ekiga.org/)

---

### Post by jamesjenner on 2011-05-25
> **linuxinstalledfromhdd said:**
> Skype is a pain sometimes. I use this:

[http://ekiga.org/](http://ekiga.org/)

Correct me if I'm wrong, but after looking at the web site I would say that you cannot call land lines. To me this is something that is very attractive with Skype. So for now I would rather get skype working (and I have some credit on Skype, so I would like to use it up).

---

### Post by linuxinstalledfromhdd on 2011-05-25
Oh I also use Google Talk and have a Google Voice account. Works great in 10.10. Don't need a land line anymore.

---

### Post by jamesjenner on 2011-05-25
> **linuxinstalledfromhdd said:**
> Oh I also use Google Talk and have a Google Voice account. Works great in 10.10. Don't need a land line anymore.

Ahh, I'll have to look into it. Still, would like to get skype behaving correctly under Unity. :)

---

### Post by linuxinstalledfromhdd on 2011-05-25
Here's one way.

Click on top left corner of Unity. Type in the search box for Login.  Unlock. And select from the dropdown menu Ubuntu Classic. And exit to  save. Reboot to make sure the changes have taken effect.

---

### Post by jamesjenner on 2011-05-25
> **linuxinstalledfromhdd said:**
> Here's one way.

Click on top left corner of Unity. Type in the search box for Login.  Unlock. And select from the dropdown menu Ubuntu Classic. And exit to  save. Reboot to make sure the changes have taken effect.

Well you are correct, that may fix the problem. However I wish to continue to use Unity, switching DE's to me doesn't seem an appropriate solution for such a minor problemo. :O

---

### Post by linuxinstalledfromhdd on 2011-05-25
Well it was just a suggestion. Besides they are going to switch to Gnome 3 in the next release, how important is it?

---

### Post by jamesjenner on 2011-05-25
> **linuxinstalledfromhdd said:**
> Well it was just a suggestion. Besides they are going to switch to Gnome 3 in the next release, how important is it?

But it is my understanding that they will be continuing with Unity. So I would like to get it sorted however not by reverting to Gnome.

---

### Post by jamesjenner on 2011-05-25
Okay. Looked at my logs and found the following entries in the syslog:

> May 24 19:32:20 james-Ubuntu kernel: [ 1537.283397] process `skype' is using obsolete setsockopt SO_BSDCOMPAT```
May 24 23:11:19 james-Ubuntu gnome-session[1589]: EggSMClient-WARNING: Desktop file '/home/james/.local/share/applications/skype.desktop' has malformed Icon key 'skype.png'(should not include extension)
``````
May 25 17:08:13 james-Ubuntu gnome-session[1595]: WARNING: Could not launch application 'skype-wrapper.desktop': Unable to start application: Failed to execute child process "skype-wrapper" (No such file or directory)
```Not sure if this could be causing the problem. I suspect that the later one may be a left over from my upgrade to 11.04 from 10.10... :confused:

Just started up skype now and monitored the syslog, no entries at all but the icon came up on the area at top right, also closed and it stayed there. I'll keep an eye on it tonight and see if I can pinpoint when it fails.

:edit:

I've also noticed that when switching desktops (ctrl alt arrow) that the skype icon flickers, may be nothing but it is annoying :)

---

### Post by Benchrest on 2011-05-25
It appears the problem occurs with both Unity and Ubuntu Classic. I am running Classic.

---

### Post by Benchrest on 2011-05-25
I have been looking a EKIGA and it appears you cannot call someone who is on Skype. Even if it would I think they would also need to set up a EKIGA account. I would be interested in a product that could have a video call to a skype user where the skype user wouldn't know if you are using skype or something else. Otherwise I need to stay with skype and fix this problem.

---

### Post by jamesjenner on 2011-05-25
Well it worked fine last night, going to see if I can make it stop working tonight.

---

