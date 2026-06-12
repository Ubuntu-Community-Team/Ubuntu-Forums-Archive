---
title: "Update Firefox to 3.5.7"
date: 2010-01-07
forum: General Help
---

### Post by artshark on 2010-01-07
Hey I am running FF3.5.3 and want to upgrade to 3.5.7. There is no .deb available, merely a tarball. How do I upgrade this, over-writing and hopefully keeping the extensions from my 3.5.3 install.
Thanks!

---

### Post by dcstar on 2010-01-07
> **artshark said:**
> Hey I am running FF3.5.3 and want to upgrade to 3.5.7. There is no .deb available, merely a tarball. How do I upgrade this, over-writing and hopefully keeping the extensions from my 3.5.3 install.
Thanks!

3.5.6 is already in the repositories and will be updated to the newer version, why aren't you using that?

---

### Post by Strongman332 on 2010-01-07
add this ppa to your repositories.

[https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa)

---

### Post by artshark on 2010-01-07
> **Strongman332 said:**
> add this ppa to your repositories.

[https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa")
thanks
where do i put the string key and fingerprint?

---

### Post by snowpine on 2010-01-07
Be patient; you'll get the new version in a couple of days, once the Ubuntu team has had a chance to test it. :)

---

### Post by artshark on 2010-01-07
> **snowpine said:**
> Be patient; you'll get the new version in a couple of days, once the Ubuntu team has had a chance to test it. :)
its old; FF for me on ubuntu has never had auto update. i don't mind manually updating, just not sure whats the best way

---

### Post by snowpine on 2010-01-07
> **artshark said:**
> its old; FF for me on ubuntu has never had auto update. i don't mind manually updating, just not sure whats the best way

Use the Update Manager or the terminal commands:

```
sudo apt-get update
sudo apt-get upgrade
```

Updating individual applications separately is "The Windows Way."

---

### Post by artshark on 2010-01-07
> **snowpine said:**
> Use the Update Manager or the terminal commands:

```
sudo apt-get update
sudo apt-get upgrade
```Updating individual applications separately is "The Windows Way."
i can just add the sources.list "urls", i don't have to worry about the key string and fingerprint?

---

### Post by mcduck on 2010-01-07
> **artshark said:**
> its old; FF for me on ubuntu has never had auto update. i don't mind manually updating, just not sure whats the best way

The default behavior for the Update Manager is to tell you about available updates only once a week (unless there are security updates). If you update manually the count resets, so if you run manual update often you'll never see the Update Manager pop up on it's own.

The update check frequency can be changed in System/Administration/Software Sources, on the Updates-tab. And if you want the update manager to show available updates immediately instead of once in every seven days you can change that through gconf-editor (disable apps/update-notifier/auto_launch to show icon in notification area immediately when updates are available, or change the value of apps/update-manager/regular_auto_launch_interval to keep the default behavior but change the frequency)

---

### Post by snowpine on 2010-01-07
> **artshark said:**
> i can just add the sources.list "urls", i don't have to worry about the key string and fingerprint?

I don't understand the question. Firefox is installed by default in all Ubuntu releases; it is not necessary to edit sources.list or worry about key strings and fingerprints to use/update Firefox.

---

### Post by mcduck on 2010-01-07
> **artshark said:**
> thanks
where do i put the string key and fingerprint?

The fingerprint works automatically, you don't need to worry about that. But you should add the key, otherwise you'll get a warning about unsecure updates every time you update or install any software.

Here's a guide for adding PPA repositories: [https://launchpad.net/+help/soyuz/ppa-sources-list.html]("https://launchpad.net/+help/soyuz/ppa-sources-list.html")

Anyway, I'd recommend just being patient, the update will most likely appear in Ubuntu's own repositories in a day or two. :)

---

### Post by ptn107 on 2010-01-07
This is the list of bugs fixed in 3.5.7[1].  Absolutely nothing on this very short list will benefit you.  Honestly do you really need to manually update Firefox before the Ubuntu devs push out an update?  This is exactly why people encounter problems later on.  Let Update Manager take care of it please.

[1]_[https://bugzilla.mozilla.org/buglist.cgi?quicksearch=ALL%20status1.9.1%3A.7-fixed]("https://bugzilla.mozilla.org/buglist.cgi?quicksearch=ALL%20status1.9.1%3A.7-fixed")_

---

### Post by mkvnmtr on 2010-01-07
I used Ubuntu Tweek to add the dev repository for Firefox and am running 3.5.8pre. I have to agree it is not really that much benefit. I just like to fool around. Ubuntu Tweek makes adding repositories very easy and it gets done correctly.

---

### Post by artshark on 2010-01-07
> **ptn107 said:**
> This is the list of bugs fixed in 3.5.7[1].  Absolutely nothing on this very short list will benefit you.  Honestly do you really need to manually update Firefox before the Ubuntu devs push out an update?  This is exactly why people encounter problems later on.  Let Update Manager take care of it please.

[1]_[https://bugzilla.mozilla.org/buglist.cgi?quicksearch=ALL%20status1.9.1%3A.7-fixed]("https://bugzilla.mozilla.org/buglist.cgi?quicksearch=ALL%20status1.9.1%3A.7-fixed")_
but all i have is 3.5.3....have any of the versions since that been major? stability [for ff] is fine, i just want any speed i can get, as i am on a netbook.
thanks guys!

---

### Post by llawwehttam on 2010-01-07
Personally I have always used ubuntuzilla.
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

---

### Post by scouser73 on 2010-01-07
[[COLOR="Red"]**Download Firefox 3.5.7**[/COLOR]]("http://www.mozilla-europe.org/en/firefox/")

**1** - Right click & Extract the Firefox tar.bz2

**2** - Enter **gksudo nautilus** in Terminal

**3** - Copy & paste the Firefox file that you have just extracted to **/opt**

Enter these commands in Terminal

> sudo -i
Enter your password if asked
> cd /opt
> chown -R username firefox
[COLOR="Red"]**The username is your name**[/COLOR]

**4** - Right click on the Ubuntu start logo, select **Edit Menus**, 

**5** - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

**6** - In the Name field, type **Firefox**

**7** - In the Command field type **/opt/firefox/firefox**

**8** - In the Comment field type **Firefox**

You will now have Firefox installed.

---

### Post by mcduck on 2010-01-07
> **artshark said:**
> but all i have is 3.5.3....have any of the versions since that been major? stability [for ff] is fine, i just want any speed i can get, as i am on a netbook.
thanks guys!

No, Ubuntu doesn't usually provide any major updates for software after release, only security updates and bug fixes.

What comes to Firefox, the updates are just security fixes. Which makes them worth installing, but in my opinion not really something worth of going through all the work of a manual install just to get the update couple of days before it appears as automatic update anyway...

(actually the latest version is most likely in the proposed-repository already so if somebody here really, really can't wait for couple of days then it might be a better idea to enable the proposed-repository instead of installing the new version from outside of Ubuntu. Proposed is where all new packages go for some testing before they are moved into normal repositories, it's intended for testers but impatient people might like using it as well ;))

---

### Post by nanotube on 2010-01-07
> **artshark said:**
> Hey I am running FF3.5.3 and want to upgrade to 3.5.7. There is no .deb available, merely a tarball. How do I upgrade this, over-writing and hopefully keeping the extensions from my 3.5.3 install.
Thanks!

suggest you use the ubuntuzilla repository, which has the latest releases of all the mozilla software:
[http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)

---

