---
title: "How to stop Update Notifier &quot;need&quot; to upgrade to Karmic"
date: 2009-12-18
forum: General Help
---

### Post by Sciamano on 2009-12-18
Hi,
I'm running Kubuntu Jaunty, and the Update Notifier icon continuously sit in the tray with the icon telling me that an upgrade to 9.10 is available.
After all this time, I KNOW that Karmic is out, but I don't want to upgrade (especially because of [this]("http://ubuntuforums.org/showthread.php?t=1311386")).
Is there a way to tell Update Notifier to stop notifying me of the existence of Karmic?
Thanks

---

### Post by northern lights on 2009-12-18
Go to *System > Preferences > Startup Applications* and untick Update Notifier.

Run regular manual updates or add a cronjob to do it, say, weekly.

---

### Post by philinux on 2009-12-18
Sys>admin>software sources>Updates.

Release Upgrade drop down. Set this to never.

---

### Post by Sciamano on 2009-12-18
> **philinux said:**
> Sys>admin>software sources>Updates.

Release Upgrade drop down. Set this to never.

Thanks philinux, this worked!

---

### Post by slakkie on 2009-12-18
And for cli lovers:

Check the file /etc/update-manager/release-upgrades. Prompt=normal is needed when upgrading from any version to a newer version, Prompt=never will never upgrade your OS. Prompt=lts will make sure you upgrade from LTS to LTS. You need to be root to edit this file.

---

### Post by thieved on 2009-12-23
Why does this make absolutely no sense to me? I am running Kubuntu, not Ubuntu, so I know nothing of this 'System' place that you speak of. Help?

---

### Post by Sciamano on 2009-12-24
> **thieved said:**
> Why does this make absolutely no sense to me? I am running Kubuntu, not Ubuntu, so I know nothing of this 'System' place that you speak of. Help?

KMenu -> Applications -> System -> Software Sources

I have this menu voice, but I'm not sure everyone else does: I've installed Synaptic because I don't like KPackageKit, and I'm not sure whether this voice was present before installing it, too.

---

