---
title: "Please help me install this PPA."
date: 2010-03-30
forum: General Help
---

### Post by Viper2 on 2010-03-30
I am brand new to Ubuntu Linux, and I noticed that Firefox images on Ubuntu are more pixelated than Firefox images in Windows XP and Vista.

So I tried to install the PPA for firefox-smooth-scaling shown here: 

[https://launchpad.net/~firefox-smooth-scaling/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=jaunty]("https://launchpad.net/%7Efirefox-smooth-scaling/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=jaunty")

 This is how i tried to install it:

1.  I opened the terminal

2.  I typed "sudo add-apt-repository ppa:firefox-smooth-scaling/ppa"

3. Then I got some messages and the last line ended with "imported: 1"

4. Then I typed "sudo apt-get update"

I restarted Firefox hoping that my images would be less pixelated, but nothing changed.  Do I have to activate this PPA in some way?  How exactly do I do that?

Any help will be appreciated.

Thank you very much.

---

### Post by sisco311 on 2010-03-30
You have to upgrade firefox:
```
sudo apt-get install firefox
```

---

### Post by soulspit on 2010-03-30
Hi there,

I'm also having this problem, and have read all about it but am still unable to fix it, though it does seem that the answer should be here as the OP says: [https://launchpad.net/~firefox-smooth-scaling]("https://launchpad.net/%7Efirefox-smooth-scaling")

I found that I was finally able to install Tom Jaeger's update for xulrunner on that ppa (xulrunner 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1+tjaeger1) for Karmic only after checking "pre-released updates" and "unsupported updates" under software sources in my package manager.  This way, the update did appear and I was able to install it from the package manager.

However, after restarting Firefox the problem persists.  When I try to upgrade Firefox as suggested, I'm just told that "firefox is already the newest version" and nothing happens.  Do I have to wait for a new update that will get Firefox to upgrade and take into account this update I've just installed?  I was thinking about removing Firefox and reinstalling it, but I was worried that that might interfere with the plugins I have installed (for example, it took a little bit of fiddling to get Java working and it'd be a pain for a newbie like me to do it again).

Any other thoughts?

Thanks for your time.


[Edit: does it make a difference that I'm running Kubuntu, not Ubuntu? Since the xulrunner + tjaeger package appeared for me in KPackageKit I assumed it would work.]

---

### Post by Viper2 on 2010-03-30
There must be some way to activate this PPA.  Can someone please help?  My firefox is already the most current version.

---

### Post by wojox on 2010-03-30
What happens if you just run:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

---

### Post by Viper2 on 2010-03-30
> **wojox said:**
> What happens if you just run:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

I haven't tried running all those updates from terminal yet.  I have only done the "sudo apt-get update" in terminal, and the I ran the "update manager" through the main menu under System-->Administration.

But I would just like to know how to fully install this PPA.  Can anyone help?

---

### Post by wojox on 2010-03-30
It should be installed. What does this return:

```
ls /etc/apt/sources.list.d
```

---

### Post by Viper2 on 2010-03-30
> **wojox said:**
> It should be installed. What does this return:

```
ls /etc/apt/sources.list.d
```

It returns this:

```
firefox-smooth-scaling-ppa-karmic.list
```

---

### Post by Arand on 2010-03-30
First of all, that PPA is intended for 9.10 (Karmic) and 10.04 (Lucid) only, which version of ubuntu are you running (your link seems to indicate 9.04 (Jaunty)?)

xulrunner-1.9.1 is the name of the (source-)package hosted by that PPA for Karmic.
This package is installed by default in Karmic so it's a simple upgrade.

instruction for installing would be:```
sudo add-apt-repository ppa:firefox-smooth-scaling/ppa
sudo aptitude update
sudo aptitude safe-upgrade
```(aptitude can be exchanged with apt-get if preferred)

I tested in Karmic myself and the scaled smoothing seems to work fine:
[[IMG]http://img229.imageshack.us/img229/4093/screenshot1qo.th.png[/IMG]](http://img229.imageshack.us/i/screenshot1qo.png/)
(Smoothed scaled image to the left)

- Arand

---

### Post by Viper2 on 2010-03-30
> **Arand said:**
> First of all, that PPA is intended for 9.10 (Karmic) and 10.04 (Lucid) only, which version of ubuntu are you running (your link seems to indicate 9.04 (Jaunty)?)

xulrunner-1.9.1 is the name of the (source-)package hosted by that PPA for Karmic.
This package is installed by default in Karmic so it's a simple upgrade.

instruction for installing would be:```
sudo add-apt-repository ppa:firefox-smooth-scaling/ppa
sudo aptitude update
sudo aptitude safe-upgrade
```(aptitude can be exchanged with apt-get if preferred)

I tested in Karmic myself and the scaled smoothing seems to work fine:
[[IMG]http://img229.imageshack.us/img229/4093/screenshot1qo.th.png[/IMG]]("http://img229.imageshack.us/i/screenshot1qo.png/")
(Smoothed scaled image to the left)

- Arand

I am running 9.10 Karmic, so should I delete the PPA and reinstall it?  If so, what exactly should I type in terminal?  If not, what step did I miss?  Can I reinstall it over itself?

---

### Post by Arand on 2010-03-30
As per your post #8 the PPA seems to be enabled correctly.

What does this return?:```
aptitude show xulrunner-1.9.1 | grep Version
```
- Arand

---

### Post by Viper2 on 2010-03-30
> **Arand said:**
> As per your post #8 the PPA seems to be enabled correctly.

What does this return?:```
aptitude show xulrunner-1.9.1 | grep Version
```- Arand

It returns this:

```
Version: 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1
```Is this the correct version?

---

### Post by Arand on 2010-03-30
> **Viper2 said:**
> It returns this:

```
Version: 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1
```Is this the correct version?

No, that is the default version that comes with Karmic and not the one from the PPA.
First verify that the "link" for the PPA is correct (execute first line, verify output with second line):```
cat /etc/apt/sources.list.d/firefox-smooth-scaling-ppa-karmic.list

deb http://ppa.launchpad.net/firefox-smooth-scaling/ppa/ubuntu karmic main
```If there is a # in front of the line, the PPA is disabled, if it doesn't match at all the installation of the PPA didn't work, in those cases go to:

(menu)System>Administration>Software Sources>(tab)>Other Software

...and from there either re-enable the PPA (if it was disabled with a #)

or remove it and re-install it by the "add" function, the line to add is similarly: ppa:firefox-smooth-scaling/ppa


When You've made sure the PPA "link" is correct
Try running these commands:```
sudo aptitude update
sudo aptitude safe-upgrade
aptitude show xulrunner-1.9.1 | grep Version
```If it was installed correctly it would now instead output```
Version: 1.9.1.8+build1+nobinonly-0ubuntu0.9.10.1+tjaeger1
```

---

### Post by Viper2 on 2010-03-30
WOW!! Thank you very much for the help everyone!!  Firefox images look MUCH better now!!

---

### Post by krismatth3 on 2010-03-30
Disregard.

---

