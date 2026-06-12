---
title: "Question about next upgrade"
date: 2009-10-14
forum: General Help
---

### Post by tadpole1954 on 2009-10-14
Hi.  I just started using jaunty a week or so ago.  I like it.  I've been using pclinuxos for a few months and had some problems so I decided to try ubuntu.  I never could use it before because of the intramfs issue I had.  Anyway, I'm here now.

My question deals with the upcoming karmic koala upgrade.  I seem to remember hearing about a lot of problems with the last upgrade or the one before.  I, like most everyone else I suppose, don't need more problems.  I had plenty with my last os.

How is the upgrade done?  By that I mean what is my responsibility?  Can I wait for awhile before I upgrade?  or do I upgrade when it becomes available?  

Will I have to do a clean install or does it just update the os?

If someone could spare a couple of minutes to explain I would appreciate it.  Thanks.

---

### Post by amingv on 2009-10-15
Since a picture is worth a thousand words, then a ~3min video (assuming framerate=60fps) is worth 10,800,000 words.

[http://www.youtube.com/watch?v=FId_uK4vx4w&feature=fvw](http://www.youtube.com/watch?v=FId_uK4vx4w&feature=fvw)

(It's updating to 8.04 LTS, but I think it's still pretty much the same, I usually upgrade through the console so I may be wrong.)

Fresh installing is not necessary, and yes, you can choose to hold it, but keep in mind the current version will stop being maintained sooner or later.

---

### Post by Sef on 2009-10-15
> Fresh installing is not necessary, and yes, you can choose to hold it, but keep in mind the current version will stop being maintained sooner or later.


True, a clean install is not necessary.  However, there are less problems with a clean install than an upgrade.  If you do upgrade, it is best to uninstall any proprietary software.

---

### Post by donato roque on 2009-10-15
A regular Ubuntu release (non-LTS) is supported for 18 months.  Ubuntu 9.04 Jaunty came out April 2009.  An LTS long term support release is supported for three years (desktops) and five years for servers.

This means your version will still be supported after Karmic Koala is released this month.  If you don't want to upgrade to Karmic, you still enjoy the security updates for your version free.

Having said these, I want you to know that it is easy to upgrade. If you have a reliable internet connection just let Software Source handle the upgrade.  When Karmic final release becomes available it will ask your confirmation for the upgrade.

---

### Post by tadpole1954 on 2009-10-15
Thanks for the quick response.  If I choose to do a clean install, will I reformat my / partition and just install there?  Is there anything in the /home partition that will need replaced?  Or should I just backup my /home and start from scratch?

---

### Post by amingv on 2009-10-15
> **tadpole1954 said:**
> Thanks for the quick response.  If I choose to do a clean install, will I reformat my / partition and just install there?  Is there anything in the /home partition that will need replaced?  Or should I just backup my /home and start from scratch?

Generally, I set up my computers to have /home on a entirely separate partition, this way if I do a clean install I just format the old / partition and tell the installer to mount my old home partition in /home.

By doing this I keep all of my documents, files and settings (even firefox sessions stay alive). Additional programs you installed will need to be installed again, but once they are they'll also have all their settings back.

If a script/configuration file in /home needs to be replaced (because of a new version of the software that uses it, for example), it will usually be done automatically.

If /home is in the same partition as /, then you'd need to backup all the data that you don't want to loose.

Either way it's good to have a backup at least of the very important files. Stuff happens, and it's better to be safe than sorry.

---

### Post by tadpole1954 on 2009-10-16
Thanks.  I have my /home in a separate partition.  I think that will be the way I will do it.

---

### Post by amingv on 2009-10-16
Good.
Keep another thing in mind: once you reinstall, use the same username you have now. If not a new folder will be created under /home with the new username and you'll have to move your data there. Nothing big, just a heads up.

---

