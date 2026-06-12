---
title: "adobe flash player update problem"
date: 2010-11-15
forum: General Help
---

### Post by kolo-01 on 2010-11-15
i'm getting an error when i try to update the adobe-flash-plugin with update manager and package manager, the message says

W: Failed to fetch [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65-1maverick1_i386.deb](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65-1maverick1_i386.deb)
  403  Forbidden

anyone have any idea why i am forbidded to update or have the same problem..

---

### Post by sikander3786 on 2010-11-15
Go to Software Center > Edit > Software Sources and change your update server to Main. Now try,

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Post the errors if any.

---

### Post by jmszr on 2010-11-15
kolo-01,

I suggest that you use the FLASH-AID add-on for Firefox. It will: "Remove conflicting flash plugins from Ubuntu Linux systems and install the appropriate version according to system architecture.":[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) .

I know that doesn't answer your question; but it should get flash installed for you.

---

### Post by gandaran on 2010-11-15
> **kolo-01 said:**
> i'm getting an error when i try to update the adobe-flash-plugin with update manager and package manager, the message says

W: Failed to fetch [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65-1maverick1_i386.deb](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.1.102.65-1maverick1_i386.deb)
  403  Forbidden

anyone have any idea why i am forbidded to update or have the same problem..
you could remove the canonical flash package and install the ubuntu supported adobe flash (flashplugin-installer) package instead.

---

### Post by MyR on 2010-11-15
> **gandaran said:**
> you could remove the canonical flash package and install the ubuntu supported adobe flash (flashplugin-installer) package instead.

This is what I needed to do. Solved.

---

### Post by ajgreeny on 2010-11-15
> **MyR said:**
> This is what I needed to do. Solved.
But which version of flash is then installed?

The upgrade offered is from 10.1.102.64 to 10.1.102.65, and as far as I can see the flashplugin-installer still has the non-updated 10.1.102.64 version, so there is no point in uninstalling the adobe version and then reinstalling the same plugin version, but from a different source repository.

I will wait and see if the upgrade problem is solved over the next few days.  Such things are usually sorted pretty quickly, either to make them work, or just taken down from the repository.

---

### Post by MyR on 2010-11-15
You're right; goot catch. it installed 10.1.102.64.

---

### Post by Mike3 on 2010-11-15
Same problem here. Hopefully one of the admins will catch this & report it upstream.

---

### Post by kolo-01 on 2010-11-15
i think i got it when it was a bit too hot off the press, it worked fine a few hours later, so quick- people using ubuntu are bound to grow in numbers with people fixing things at that speed, cheers

---

### Post by Enigmapond on 2010-11-15
I'm still getting the error...so it's not fixed yet...at least not for Lucid.

---

### Post by ajgreeny on 2010-11-16
11am GMT Wed 16 Nov:

I changed from the UK server repositories to the Main server in my software sources, and now suddenly the package is updating fine.

There must be a problem with the .deb package on the UK repositories, I think.

---

### Post by MyR on 2010-11-16
> **ajgreeny said:**
> 11am GMT Wed 16 Nov:

I changed from the UK server repositories to the Main server in my software sources, and now suddenly the package is updating fine.

There must be a problem with the .deb package on the UK repositories, I think.

I was having the problem on the US repo.

---

### Post by Stormsy on 2010-11-16
I had to re-install Ubuntu as my HDD decided to fail on me! :O  (Not much of a problem as the machine Ubuntu is installed on is a secondary machine, only used for messing about...)

Installed Ubuntu 10.04; updated it and looked in the Software Centre for the "Ubuntu Restricted Extras" package for Flash.  I installed that, and to just check, used FireFox's plug-in checker to make sure everything was up-to-date.

Well; it told me that I needed to update Flash.  Strange I thought, usually software from the Software Centre are up-to-date.  Checked the version in the Software Centre and the version was; 10.1.102.64 rather than; 10.1.102.65 from Adobe's site.

It took me the last 2 hours to install Ubuntu (and configure it of course to my needs) as well as to realise the problems with Flash... >_<

Not sure what's going on.  Is there anyway to notify someone who monitors the repo's to update this?? :S

Or (sudden brainwave) does it take some time (considering how many repo's there are on the servers around the world) to actually upload the updated version of Flash?

Cheers,
Stormsy.

---

### Post by ajgreeny on 2010-11-16
> Or (sudden brainwave) does it take some time (considering how many  repo's there are on the servers around the world) to actually upload the  updated version of Flash?
If the server you use for updates does not contain the new version of flash you will not be notified of the update, so your last point is not an answer.  The UK servers must have had the .deb sitting there, but it was impossible to get it to download, that is why I believe it must have been a bad package on that server, and perhaps some other servers as well.

---

