---
title: "New mail notification applet"
date: 2010-04-30
forum: General Help
---

### Post by IamPi on 2010-04-30
in Lucid ive been trying to get the mail applet to light up green by sending myself mail. Does this applet only light up when IMs r received or does this also work with evolution and if so what might i have done wrong in evolution, ive tried it with evolution open and evolution closed.

---

### Post by Absorbed on 2010-04-30
I think I've got a similar problem.

I've installed Lucid, and rather than use checkgmail, I've decided to give evolution a try, using the mail notification applet. I'm using my gmail account with IMAP.

Unfortunately, it doesn't seem to tell me when I've got new mail. I've also sent myself emails, and I've received emails from others, but all I ever see if a white envelope.

I checked the plugins in evolution, and there is a mail notification plugin, and its seems to be installed and working. Keeping evolution open doesn't seem to make any difference.

Any help would be much appreciated.

---

### Post by ValentinV on 2010-04-30
You could try Specto it does a good job in notifying you of new mails and other stuff change and it can open evolution when you open mails  that changed

---

### Post by IamPi on 2010-05-06
so applet=fail

---

### Post by Noo 2 Ubuntoo on 2010-05-06
> **Absorbed said:**
> I think I've got a similar problem.

I've installed Lucid, and rather than use checkgmail, I've decided to give evolution a try, using the mail notification applet. I'm using my gmail account with IMAP.

Unfortunately, it doesn't seem to tell me when I've got new mail. I've also sent myself emails, and I've received emails from others, but all I ever see if a white envelope.

I checked the plugins in evolution, and there is a mail notification plugin, and its seems to be installed and working. Keeping evolution open doesn't seem to make any difference.

Any help would be much appreciated.

Try this:

1. Open Synaptic package manager (in administrator mode) ensuring you have BOTH  these packages installed (my upgrade only came with one of them installed)

(a) mail-notification-evolution 5.4.dfsg.1-1ubuntu:5.4.dfsg.1-1ubuntu:evolution support for mail notification

(b) mail-notification 5.4.dfsg.1-1ubuntu:5.4.dfsg.1-1ubuntu: mail notification in system tray

2. Open evolution going to Edit - plugins and check the box for "mail notification" and "Jean-Yves Lefort's Mail Notification"

3. Go to Applications - Internet - Mail Notification and click "Mail Notification" which should appear as an icon in notification area in the panel at the top of your screen.

4. Right click the "Mail Notification" icon in the top panel, then click "properties" and add your evolution mailbox from the drop down menu that appears and your finished UNLESS

5. you get a message that mail notification cannot contact evolution in which case open a terminal (in administrator mode) typing the following:

sudo ln -s /usr/lib/evolution/2.24/plugins/org-jylefort-mail-notification.eplug /usr/lib/evolution/2.28/plugins/
sudo ln -s /usr/lib/evolution/2.24/plugins/liborg-jylefort-mail-notification.so /usr/lib/evolution/2.28/plugins/

Press enter and exit terminal. I did a restart to make sure it updated and then repeat steps 1 - 4 to be sure of everything.

Step 5 only applies to evolution 2.28 which ships with Karmic Koala as can be seen through the references to "2.28" in the terminal command at step 5 above. It should also work with evolution version 2.26 in Jaunty Jackalope by changing the "2.28" to "2.26". 

**NOTE:**

 I haven't installed Lucid yet so be careful around steps 1(a) and (b) - they may have been updated to a later version for Lucid. If you go to step 5 you will have to substitute "2.28" with whatever version of evolution ships with Lucid. 

A feature of this notifier which some view as a drawback is that, once installed,  it won't work unless you keep evolution open.

---

### Post by OldGoat58 on 2010-05-06
> **IamPi said:**
> in Lucid ive been trying to get the mail applet to light up green by sending myself mail. Does this applet only light up when IMs r received or does this also work with evolution and if so what might i have done wrong in evolution, ive tried it with evolution open and evolution closed.


I'm probably wrong, and I am sure someone will correct me, but if you "right click" in the "Panel" and click on "Add to Panel" there is the option to add "Notification Applet" and "Notification Applet Session".  Highlight each one individually and click "add".  That is how I got the notification to work.  I did notice that in 10.04 LTS the round dot has been replaced with an envelope.

Hope this helps.
Mike
Fairless Hills, PA

](*,)

---

### Post by CiscoPenguin on 2010-05-06
I have been looking for something that will work with Thunderbird... any suggestions?

---

### Post by Noo 2 Ubuntoo on 2010-05-06
> **CiscoPenguin said:**
> I have been looking for something that will work with Thunderbird... any suggestions?

Have you looked at Mozilla's addons? I don't use Thunderbird so can't comment on how good these are, maybe this [URL="https://addons.mozilla.org/en-US/thunderbird/search?q=new+mail+notification&cat=all"]will help.

---

### Post by CiscoPenguin on 2010-05-06
Thanks!

---

