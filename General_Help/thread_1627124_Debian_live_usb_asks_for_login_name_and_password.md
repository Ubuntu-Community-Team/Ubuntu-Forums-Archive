---
title: "Debian live usb asks for login name and password"
date: 2010-11-21
forum: General Help
---

### Post by beew on 2010-11-21
Hi,

I am not sure where to post this, I seem to remember there is a section for questions about other distros but I can't find it anymore. 

I have made a live usb from a Debian testing live image (.img) using the dd command. It all worked well and it booted flawlessly. But then when it booted into the Debian screen it asked for my user name and password. I never set any user name and password so of course I couldn't log in.

Please give me some advice. Maybe I need to edit some files in the usb?

---

### Post by cogier on 2010-11-21
I would like to see a reply to this. I booted a Linux Format Ubuntu 10.10 live DVD in an old laptop and also got a login request.

No amount of guessing got me anywhere.

---

### Post by Verbeck on 2010-11-21
for debian, try *live* as both user name and pass
source : [http://wiki.debian.org/DebianLive/FAQ#Q.3AWhatistheroot.2BAC8-userpassword.3F](http://wiki.debian.org/DebianLive/FAQ#Q.3AWhatistheroot.2BAC8-userpassword.3F)

for ubuntu, the user name is *ubuntu* . no pass

---

### Post by coffeecat on 2010-11-21
> **beew said:**
> I am not sure where to post this, I seem to remember there is a section for questions about other distros but I can't find it anymore. 

That section was closed a long time ago. The forum now generally discourages support questions about other distros and OSs unless the problem is directly related to Ubuntu. I'm sorry I can't help you with your particular question - my experience of true Debian is virtually non-existent.

> **cogier said:**
> I booted a Linux Format Ubuntu 10.10 live DVD in an old laptop and also got a login request.

Was that one of their now-discontinued ecodiscs which some people had issues with? Whatever - you are not meant to get the login request when you boot up from an Ubuntu live CD, but if you do this usually means a bad disc, a bad DVD drive or some other cause for a misread. The login name and password are 'ubuntu' and a blank password - just press enter - but if you get a login screen on first bootup this generally fails. Probably because something has already gone wrong.

---

### Post by beew on 2010-11-21
I tried the following combinations for user name and password and none worked:

user live

live live

debianlive debianlive

What are these guy thinking to ask for login for a live usb and the username and password are nowhere to be found???

---

### Post by beew on 2010-11-22
OK. That's it. I give up. I have tried several different images and different combinations of user names and passwords from various Debian sources and none work. I was reading the Debian forums and found that this problem has gone back quite a few years. Is this a joke?! In the Debian forums they were wondering why Debian was not as popular as Ubuntu. Well at least for Ubuntu you can actually use your live usb or live CD.

I am now posting from a Fedora live usb with kde Desktop. It is surprisingly nice. Never thought I would like kde, and for the first time wireless actually works with knetwork manager.

---

