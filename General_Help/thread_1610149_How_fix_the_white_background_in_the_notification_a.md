---
title: "How fix the white background in the notification area (Lotus)"
date: 2010-10-31
forum: General Help
---

### Post by Vegaxus on 2010-10-31
Hi again.

I have an ugly view of my notification area due to i installed the last version of Lotus Symphony 3. Now, my notification area show like this:

[IMG]http://img183.imageshack.us/img183/8352/notification.png[/IMG]

Is it a bug from Lotus Symphony or from Ubuntu?

By the way, the icon of Lotus is a .png file with transparent background.

---

### Post by devondashla on 2010-10-31
It's a lotus problem. Banshee used to do the exact same thing.

It's just a bug, and there's probably a report of it already. Hopefully it'll be fixed for you sometime soon. All I can tell you is to just ignore it, and know there's nothing wrong with the app or ubuntu itself.

---

### Post by Vegaxus on 2010-10-31
ok, thanks.

I thought i could make a partial fix in the opt/ibm/lotus/symphony folder so far but i did not know the origin of this kind of bug.

For example, now you talk about the same bug in banshee, Is this bug due to an error with the icon image (like no transparent background or the format file must be svg instead of png extension) or is due to a script bug?

thanks to reply. regards

---

### Post by devondashla on 2010-11-01
> **Vegaxus said:**
> ok, thanks.

I thought i could make a partial fix in the opt/ibm/lotus/symphony folder so far but i did not know the origin of this kind of bug.

For example, now you talk about the same bug in banshee, Is this bug due to an error with the icon image (like no transparent background or the format file must be svg instead of png extension) or is due to a script bug?

thanks to reply. regards

Honestly, I have no idea what causes it. I would assume it's just the way they setup the notification options, but you never know.

---

### Post by gandaran on 2010-11-01
try a deferent gkt theme, some themes don't have this issue

---

### Post by jesuisbenjamin on 2010-11-01
The issue (with Banshee and others) was true in 10.04 for me, but solved in 10.10.
The SVG vs. PNG may indeed be the cause. Did you try to use a svg file? 
The icons should be in /usr/share/lotus/ 

B.

---

### Post by Vegaxus on 2010-11-01
As **gandaran** says, the bug just does not exit under "dust sans" gtk theme neither under Highcontrastinverser theme.

I tried to see the gtkrc file in both themes trying to know how fix it but i do not understand anything is written in those files. :(

Is not there any program in linux to change gtk themes? this bug looks really ugly.

---

### Post by jesuisbenjamin on 2010-11-01
There is a program for that, i am not on my comp right now so i can't check. But in Ubuntu Software Center you should find it by searching for "theme". 
Imma follow this thread, let us know if/how you solve this.

Goodluck.

PS: Dust Sand/s theme is the nicest imo.

---

### Post by Vegaxus on 2010-11-01
i was wrong, the bug was not really solved with other themes i made a test i now i could confirm that is a exclusive bug of the Symphony software not from ubuntu or gnome.

well, dust sans and highcontrastinverser do not use pixmap png file on the gnomel-panel and both use the same background color for the panel and the nautilus background. That is the reason why Dust sans and Hihgcontrastinverser seem to have solved this bug although is a fake one.

To change the white background, just need to change the gtkrc file the hex number: \nbg_color:#F2F1F0\.

Now, if i want to remove the "fake transparent" from the other tray application like VLC, Opera, Tomboy, Rhythmybox, etc. I just to add a # in the beginning of the line <<class "PanelApp*"  style "panel">>> in the file gnome-panel.rc

So i wonder... What kind of link exists between that command: <<class "PanelApp*"  style "panel">> and the notification area which affects on all software trays and not on the symphony tray?

What a mess...

---

### Post by drbraniac on 2010-11-18
While this isn't quite a solution, it is a workaround I've found. 

If you navigate to the directory ```
/opt/ibm/lotus/Symphony/framework/shared/eclipse/plugins/com.ibm.symphony.standard.branding_3.0.0.20101015-2340/icons
```

(If you find that the directory I linked to above doesn't work, try searching for the file "symphony16.png" in Tracker search tool or another desktop search app and then open the folder in which it is found). 

You will find a file called "symphony16.png". This is the image file which determines what icon will be shown in your notification area for IBM Lotus Symphony. 

I found that by modifying this png file such that its background is of your panel's background image or color, the icon will blend in better to the notification area. 

I set the png to dimensions 22px by 22px in GIMP (the dimensions correspond with whatever height your panel is set to), and then copied the panel background image for the theme I use as the background for symphony16.png. 

See my attachments to view how the symphony notification area icon looks like now. Note that I also changed the icon itself.

---

### Post by munky99999 on 2010-11-19
This is a problem with the notification area.

If you customize your gnome theme and change window background colour. 

Alltray has the problem also.

The fix is changing the icon to remove transparency as the old patch just broke for me today.

---

