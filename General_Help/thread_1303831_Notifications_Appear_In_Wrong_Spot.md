---
title: "Notifications Appear In Wrong Spot"
date: 2009-10-28
forum: General Help
---

### Post by cesiel1990 on 2009-10-28
I recently upgraded from Ubuntu 9.04 to 9.10 and I started having this issue with my notifications.  Rather than showing up right below the system panel.  They show up slightly lower.  Attached is a picture to show I mean.  Does anyone know how I could fix this?

---

### Post by mcduck on 2009-10-28
Sorry, that's by design (to keep them from covering the minimize/restore/close buttons in the top right corner of the window title bar).

At this point the notifications are not configurable, so the only way to change that would be downloading the source code, modifying it, and compiling the app yourself.

---

### Post by Anonymousable on 2009-10-28
> **mcduck said:**
> At this point the notifications are not configurable, 
Bug :P

But seriously, there's not much time to fix it >.>
Will probably be a post-release update. I hope.

---

### Post by mcduck on 2009-10-28
> **Anonymousable said:**
> Bug :P

But seriously, there's not much time to fix it >.>
Will probably be a post-release update. I hope.

Not likely, since at this point it's by design. So it's a "feature".

And after release only updates provided are security updates and fixes for serious bugs. So never just to provide new features.

If we are lucky, the notifications might become configurable in the next release.

---

### Post by cesiel1990 on 2009-10-28
The notifications just seem awkward when they show up there haha...

---

### Post by Anonymousable on 2009-10-28
And seriously, there should be a way to dismiss them... They don't get in the way, because they disappear as soon as you move the mouse over, but it's really annoying that they pop up again after.

---

### Post by mcduck on 2009-10-28
> **cesiel1990 said:**
> The notifications just seem awkward when they show up there haha...

I agree, I don't like the location either. Besides they are click-through anyway so I don't see this as sensible change, but that's just the way it is so we'll pretty much just have to live with it for now.

---

### Post by cesiel1990 on 2009-10-28
Well I hope they modify this so we can at least edit the location in the future.  This has really bothered me. :p

---

### Post by dj-toonz on 2009-10-28
The devs who wrote this software, don't care, as threes loads of bug reports and every ones been shot down with Changed in notify-osd (Ubuntu):
statu New &#8594; Invalid ,  with this a feature, so learn to live with, if you don't like it tough attitude, we know better then the user. 

for example

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/345317](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/345317)
[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/419894](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/419894)

---

### Post by mcduck on 2009-10-29
> **dj-toonz said:**
> The devs who wrote this software, don't care, as threes loads of bug reports and every ones been shot down with Changed in notify-osd (Ubuntu):
statu New &#8594; Invalid ,  with this a feature, so learn to live with, if you don't like it tough attitude, we know better then the user. 

for example

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/345317](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/345317)
[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/419894](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/419894)

The first one was marked as invalid because the bug was reported against wrong package (notify-osd). As you may notice, it's status is "confirmed" for *Nautilus*.

The second one is actually already fixed. Most of the messages in the thread are not actually related to the bug the report was about.

[https://wiki.ubuntu.com/NotifyOSD]("https://wiki.ubuntu.com/NotifyOSD")

Also note that there's a huge difference between a feature request and a bug report. Requesting features through a bug report will most likely result in the bug report marked as invalid.

---

### Post by cesiel1990 on 2009-10-29
Someone has already submitted the idea to move it back to the cornor on Ubuntu Brainstorm.  If you liked the original position vote for it.  I did:
[http://brainstorm.ubuntu.com/ideatorrent/idea/19526](http://brainstorm.ubuntu.com/ideatorrent/idea/19526)

---

### Post by potam on 2009-10-31
I don't like this new "feature". It is because the first osd slot is reserved for brightness/volume/etc. But come on, this must be at least configurable! (I know the gravity key setting, but the first slot is still reserved at the top right). :(

---

### Post by redman5087 on 2009-10-31
> **potam said:**
> i don't like this new "feature". It is because the first osd slot is reserved for brightness/volume/etc. But come on, this must be at least configurable! (i know the gravity key setting, but the first slot is still reserved at the top right). :(

+1

---

### Post by djodjoman on 2009-11-02
This is the second "by design" i see on this release wich i didn't like. First one was the fact i couldn't disable animations (wich i did after someone found a solution where i had to edit a compiz text file somewhere). And now this! I mean, this behavior is really strange and does seems like a bug, even though it is not (and that just doesn't sound fine). So at least we agree this "by design" solution wasn't very smart. Could guys at least please re-think it? Try another solution?

---

### Post by padrehomer on 2009-11-02
> **cesiel1990 said:**
> I recently upgraded from Ubuntu 9.04 to 9.10 and I started having this issue with my notifications.  Rather than showing up right below the system panel.  They show up slightly lower.  Attached is a picture to show I mean.  Does anyone know how I could fix this?

How did you do the compact clock?

---

### Post by mcduck on 2009-11-04
> **padrehomer said:**
> How did you do the compact clock?

The clock applet accepts HTML formatting (configurable through gconf-editor).

[http://www.omgubuntu.co.uk/2009/09/karmic-tray-icons-match.html]("http://www.omgubuntu.co.uk/2009/09/karmic-tray-icons-match.html")

Anyway, yu left me wondering what could be te "design feature" related to anjimations oyu mentioned above? As I haven't found anything that would require editing some text file to configure/disable. If it was some Compiz animation, you could have simply used CompizConfig Settings Manager to change the settings, or gconf-editor if you didn't want to install extra applications for the purpose.

---

### Post by m4tic on 2009-11-04
where's the source?

---

### Post by jmatties on 2009-11-05
I find that the distance between the lines with that font is too large for a panel height of 23 pixels. Maybe that's just my display resolution though.

---

### Post by potam on 2009-11-15
Check [this link]("http://www.ubuntugeek.com/how-to-restore-notifications-position-in-ubuntu-9-10-as-they-did-in-ubuntu-9-04.html") for a patched version of notify-osd. With that package, notification works just like in Jaunty.

---

### Post by ldjuda on 2009-11-16
> **potam said:**
> Check [this link]("http://www.ubuntugeek.com/how-to-restore-notifications-position-in-ubuntu-9-10-as-they-did-in-ubuntu-9-04.html") for a patched version of notify-osd. With that package, notification works just like in Jaunty.
Great find, will give it a try... thanks for posting the link.

---

