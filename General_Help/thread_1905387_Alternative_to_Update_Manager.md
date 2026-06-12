---
title: "Alternative to Update Manager?"
date: 2012-01-06
forum: General Help
---

### Post by frankuf on 2012-01-06
I have installed Ubuntu 11.10 three months after release. The install had to run without Internet connection because I only have slow and expensive (USB modem) broadband.

Now the Update Manager is reminding me that some 350 updates are waiting to be downloaded and installed, something short of 400 MB. Well, I cannot do it. And pick and install is a pain in the anatomy.

So I'm looking for an alternative to Update Manager or a tweak to Update Manager with following additional features:

-   Software which is not installed is not listed.
-   Sofware can be locked and when locked will not be listed.
-   Entries can be all tagged/untagged in one swoop.

---

### Post by cotcot on 2012-01-06
Welcome to the forum.
[[COLOR="Red"]Synaptic[/COLOR]]("https://help.ubuntu.com/community/SynapticHowto") is a good alternative, also for the Ubuntu Software Center. It was installed by default in earlier versions but was (IMHO unfortunately) replaced since 11.10 by Ubuntu Software Center.

---

### Post by papibe on 2012-01-06
Hi frankuf.

Check 'Synaptic'. You can installed on the Software Center.

Also you can use the 'apt-get' command tool. For example:
```
sudo apt-get update
```
will update the information without actually upgrading. Then
```
sudo apt-get upgrade
```
will apply all changes. Alternatively you can just upgrade one package (and its dependencies) by doing:
```
sudo apt-get upgrade package_name
```
In doubt, you can do a simulate upgrade (that does not actually upgrade anythong, but it displays all information as if it were):
```
sudo apt-get -s upgrade
```
Hope it helps.
Regards.

---

### Post by bsniadajewski on 2012-01-06
+1 on Synaptic, or if you are in Kubuntu (KDE), you could try Muon as well.  Muon will still work in Gnome/Unity, though installing it could bring in a slew of QT/KDE dependencies.

```
sudo apt-get install synaptic
```

or

```
sudo apt-get install muon --no-install-recommends
```

---

### Post by snowpine on 2012-01-06
I use the terminal, personally:

```
sudo apt-get update 
sudo apt-get dist-upgrade
```

400mb updates is normal, and I highly recommend you install them all, if you want a secure and stable Ubuntu. :)

---

### Post by ice60 on 2012-01-06
you could try updating on another computer with something like this -
[https://launchpad.net/keryx](https://launchpad.net/keryx)

i haven't used it so don't know much about it. 

also, make sure you at least update internet facing apps like your browser so they are secure and safe to use.

[http://www.webupd8.org/2010/03/keryx-0924-offline-installer-for-apt.html](http://www.webupd8.org/2010/03/keryx-0924-offline-installer-for-apt.html)

---

### Post by grahammechanical on 2012-01-06
You can go to System Settings and open Software Sources. You can un-check certain things and that might go some way to solving this problem. On the Ubuntu Software tab there are four things that can be un-checked. You might want to leave things as they are on the Update tab but it is up to you.

Using another program to update your system will not help you because the same number of updates will be produced. Won't they?

If you can be content with just security updates then you can wait until a distribution is released to update the programs and applications.

I do not know about you but I find that it is quicker to download an ISO to burn to disk that it is to upgrade to a new release on-line. Update manager will let you upgrade from a CD. Did you know that?

I know how you feel. I used to use dial-up.

Regards.

---

### Post by topsites on 2012-01-06
As a general rule it's only that first update that is such a bear, once over that hump it's not so bad so long you connect on a regular basis you'll have a few packages here and there.

What I do on my netbook is I carry with me a physical network cord (longer is better) and anytime I am someplace I can physically connect my computer to  ... 
It helps if you know the folks, and if you don't, ask, most people don't mind letting you piggyback off their network for a bit.
Then CLICK I have that thing plugged in before anyone knows the difference and 30-45 minutes later all is well.

Yes sir, sneak-a-net.

---

### Post by Seq on 2012-01-07
> **frankuf said:**
> I have installed Ubuntu 11.10 three months after release. The install had to run without Internet connection because I only have slow and expensive (USB modem) broadband.

Now the Update Manager is reminding me that some 350 updates are waiting to be downloaded and installed, something short of 400 MB. Well, I cannot do it. And pick and install is a pain in the anatomy.

Unfortunately due to the way debian packages are updated, a small update (like a default config change) results in the entire package being downloaded (including images, etc).

If you're ever distro hopping, Fedora supports Delta RPMs, which only contain the difference between your current and the updated version. A little easier on a metered internet connection.

> **frankuf said:**
> So I'm looking for an alternative to Update Manager or a tweak to Update Manager with following additional features:

-   Software which is not installed is not listed.
-   Sofware can be locked and when locked will not be listed.
-   Entries can be all tagged/untagged in one swoop.

- Update manager should list only software that is installed. There could be rare cases where an update to an installed package depends on a new non-installed package, but those kinds of updates are extremely rare within a release (upgrading to a new version, all bets are off)

- You can use [dpkg to 'Hold' a package at a specific version]("https://help.ubuntu.com/community/PinningHowto#Apt.2BAC8-Dpkg"). Synaptic also allows you to do this, but calls it 'Lock'. I believe you can also use apt-pinning to pin to a specific version, which may be easier to manage as you can specify those restrictions in plain files.

- Synaptic is a GUI that exposes much more functionality than the Software Centre and Update Manager. You could list all available updates, and lock packages from that list. Or manually select which updates to apply. That should solve your need for tagging in one swoop.

---

### Post by frankuf on 2012-01-07
Thanks to all posters. Quite useful tips, actually.

Fact is that I was already using a mix of apt-get, Synaptic, Ubuntu Software Center, Update Manager and with no joy.

That mix may have been deadly or maybe some hidden bugs in Update Manager surfaced. Things like Synaptic asking twice for the password and Update Manager taking an eternity to check repositories.

In the end, Update Manager got stuck. I requested a fresh desktop start (alt-ctrl-backspace is active), keys and mouse were dead. I could do nothing but press alt-printscreen-k. Kernel panic, I pulled the plug.

After booting from my old LTS 10.04, I repaired the 11.10 file system and tracked down all its settings and data for Update Manager. I killed them mercilessly with deep pleasure in my heart.

The best tip I got was about using Synaptic to manage upgrades. Strangely, I overlooked that feature for years. It is still a chore but not the Update Manager pain.

Future looks bleak. Synaptic is obsolete and on its way out. Just try to install 'build-essential' which does not exist any more. Synaptic will oblige and report 'not found'.

Hello Canonical: give Synaptic a lease of life.

---

### Post by Paqman on 2012-01-07
I'd strongly advise install all of the security updates that are available if you're connected to the internet. You could disable updates to the others if you want.

A good way to avoid the big update offered post install is to use the minimal ISO to install. That way you only download the latest packages at install time, instead of wsting 700MB on the disk then having to do 400MB straight after.

If you're on a slow and expensive connection installing a custom system that only contains packages you actually use would also cut down on the size of updates.

---

### Post by philinux on 2012-01-07
> **Paqman said:**
> I'd strongly advise install all of the security updates that are available if you're connected to the internet. You could disable updates to the others if you want.

A good way to avoid the big update offered post install is to use the minimal ISO to install. That way you only download the latest packages at install time, instead of wsting 700MB on the disk then having to do 400MB straight after.

If you're on a slow and expensive connection installing a custom system that only contains packages you actually use would also cut down on the size of updates.

+1 and in update manager just untick the Recommended Updates it will untick all recommended packages leaving the security updates.

---

### Post by pretty_whistle on 2012-01-07
> **topsites said:**
> As a general rule it's only that first update that is such a bear, once over that hump it's not so bad so long you connect on a regular basis you'll have a few packages here and there.

What I do on my netbook is I carry with me a physical network cord (longer is better) and anytime I am someplace I can physically connect my computer to  ... 
It helps if you know the folks, and if you don't, ask, most people don't mind letting you piggyback off their network for a bit.
Then CLICK I have that thing plugged in before anyone knows the difference and 30-45 minutes later all is well.

Yes sir, sneak-a-net.
Your idea is a good one.  :)

You can go to a Starbucks and while connected to their network download all the updates.

I don't know if that's sneaky or more like you can do what you want while connected.  They expect as much.

---

