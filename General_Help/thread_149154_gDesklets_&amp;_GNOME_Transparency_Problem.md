---
title: "gDesklets &amp; GNOME Transparency Problem"
date: 2006-03-23
forum: General Help
---

### Post by dpholmes on 2006-03-23
Hi guys,
I've very new to the world of Linux, but I'd be very grateful if I could get some help on this little aesthetic problem I'm having.

I installed gDesklets the other day and everything worked fine, the desklets were transparent as they were supposed to be.  Then I began playing around with different desktop themes.  I restarted my computer and when it rebooted the transparency was gone and I was left with a black background for my desklets (unless I was using the "Brushed" theme for GTK2, then the background was the same as seen in your windows when you change the 'controls' of a theme).

I've read that other people have solved this problem by clicking the 'Notification' icon in the system tray, going to 'Configure', and unclicking the 'Enable Translucency' button... but I can't find the 'Notification' icon (maybe I disabled it from starting up?).

Any help would be great, I'm assuming that by playing around with themes (maybe installing a metacity theme?) that it messed with my transparency, but I don't know how to undo this.  

Cheers,
-Doug

---

### Post by sampoerna on 2006-03-23
Hi there,
To bring back the notification bar, 
1. Click on any gnome panel, select 'Add to panel...'
2. Select 'Notification Area' under utilities
3. restart your gnome by logging out and in or press CTRL + ALT + BACKSPACE.

After that you should be able to see the gDesklet icon in the notification area, right click on it, configurations... and uncheck the 'Translucency'

hope this will help ;) .

---

### Post by dpholmes on 2006-03-23
sampoerna:
So I added the Notification Area, but it doesn't show gDesklets running there.  I think I disabled it when I first installed gDesklets, but now I can't find the option to have it run in the Notification Area... any suggestions on how to get it back there?
Cheers,
-Doug

---

### Post by the_purulent on 2006-03-23
shouldn't you be able to access it from the gdesklets application itself?
alt+f2 then type gdesklets

seems like there should be a way to access all of the options from within the application itself.

---

### Post by dpholmes on 2006-03-23
the_purulent,
i agree it seems like you should be able to access all the options from within the application, but it doesn't appear to let me, unless I'm missing something.
Cheers,
-Doug

---

### Post by dpholmes on 2006-03-23
I've tried removing and reinstalling gDesklets without any luck, is there any setting or configuration file that states which programs will run in the Notification Area?

---

### Post by dpholmes on 2006-03-23
sorry to keep posting, but i fixed it....
to get the the configuration window up if you've lost the icon in the notification area just type 'gdesklets configure' in your terminal, then simply uncheck 'enable translucency' and everything will work fine.
cheers!

---

### Post by the_purulent on 2006-03-24
Glad that worked out for you.  I wish I could have been more help, but I was at work and had no access to my ubuntu pc :)

---

