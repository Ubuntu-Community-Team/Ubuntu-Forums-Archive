---
title: "Different apps version between 10.04 and 11.10"
date: 2012-02-22
forum: General Help
---

### Post by ayozito on 2012-02-22
Hi!

Today I installed back 10.04 because 11.10 is very unstable with Unity and with Gnome3.

Now that I ended the install and configuration of my needed apps, I just noticed that I haven't the same version I had on 11.10 (or on LM 12 too).

For example I use Audacious as music player. Now I have the Winamp-like inferface instead of the inferface I had by default on 11.10 (I mean GUI not skin interface)

Why can I have the latest version using old 10.04?

---

### Post by roelforg on 2012-02-22
> **ayozito said:**
> Hi!

Today I installed back 10.04 because 11.10 is very unstable with Unity and with Gnome3.

Now that I ended the install and configuration of my needed apps, I just noticed that I haven't the same version I had on 11.10 (or on LM 12 too).

For example I use Audacious as music player. Now I have the Winamp-like inferface instead of the inferface I had by default on 11.10 (I mean GUI not skin interface)

Why can I have the latest version using old 10.04?
When the Ubuntu community switched to newer versions, they stopped compiling new versions for 10.04.
Hence, 11.10 has newer versions with other defaults.

---

### Post by ayozito on 2012-02-22
Then.. If I want lastest version I have to switch to 11.10 again? (I don't really want crashes every time :( )

And btw, on 11.10 I have NIC problems with Realtek 8168B..

---

### Post by raja.genupula on 2012-02-22
> **ayozito said:**
> Then.. If I want lastest version I have to switch to 11.10 again? (I don't really want crashes every time :( )

And btw, on 11.10 I have NIC problems with Realtek 8168B..

hmm you can install new version by getting it from their official site .

---

### Post by roelforg on 2012-02-22
> **ayozito said:**
> Then.. If I want lastest version I have to switch to 11.10 again? (I don't really want crashes every time :( )

And btw, on 11.10 I have NIC problems with Realtek 8168B..
Open a thread about the NIC problems on the network&wireless forum and i'll be happy to help.

---

### Post by snowpine on 2012-02-22
Apologies if you already know this, but since nobody has mentioned it yet...

The number of each Ubuntu release indicates its date (year.month). 

10.04 is the April 2010 release. Therefore it uses software versions released prior to April 2010. If you want newer software then the easiest method is to use a newer release (11.10 is the October 2011 release, 12.04 is the upcoming April 2012 release, currently in beta-testing, etc).

If you are willing to install from an unsupported software source, then it should be easy to install a newer version of Audacious (or any other appliciation).  Here are a couple of possibilities I found in 10 seconds using Google:

[http://audacious-media-player.org/download](http://audacious-media-player.org/download)
[https://launchpad.net/ubuntu/+source/audacious](https://launchpad.net/ubuntu/+source/audacious)

---

### Post by ayozito on 2012-02-22
What I wanted is install software from trusted repositories.

Didn't knew that every version only had the software before its launch. I though the software center was update daily.

For solve the problem of audacious I added the WebUpd8 repository.

---

### Post by snowpine on 2012-02-22
> **ayozito said:**
> Didn't knew that every version only had the software before its launch. I though the software center was update daily.

If that were the case, there'd be no need for new releases every 6 months and Ubuntu would be "rolling release" like Arch. ;)

---

### Post by scwizard on 2012-02-22
You can get a newer version by:

Using a backport: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)
Compiling it from source.

EDIT: It's kind of shocking that I'm the first person to mention backports.

Let me go into more detail. The way Ubuntu and Debian's stable branch work, is that software is not updated in between releases, except for security and stability updates.

If you want a newer version of the software there are two main ways you can go about it:
* Compile it from source.
* Obtain a recent binary.

The (semi)supported way to do the later is ubuntu's "backports" repository. What a backport is in the *nix world is a newer piece of software built to run on an older operating system. For instance a 2011 version of a software built to run on a 2010 version of Ubuntu.

If you don't like this model, there are some operating systems that are "rolling release." Meaning that rather than releasing "versions" of the operating system, they will gradually upgrade packages.

Rolling release operating systems have their own challenges, but personally I prefer them for desktop use. In my opinion stepladder release systems are designed for production server environments where the idea is to touch the servers as little as possible. If you want to try a a rolling release operating system, [Debian Wheezy](http://www.debian.org/releases/testing/) is a good candidate, as it uses several conventions that are similar to Ubuntu.

---

### Post by scwizard on 2012-02-22
> **snowpine said:**
> If that were the case, there'd be no need for new releases every 6 months and Ubuntu would be "rolling release" like Arch. ;)
Don't recommend Arch please.

From what I've heard you're much better off with Debian Wheezy if you want software that is "update daily."

---

### Post by snowpine on 2012-02-22
> **scwizard said:**
> Don't recommend Arch please.

From what I've heard you're much better off with Debian Wheezy if you want software that is "update daily."

Please don't tell me what to recommend; I would recommend Arch over Debian Testing any day of the week! (And I have used both extensively, have you? ;))

That being said, if you carefully re-read my post, I did not recommend Arch to the OP, I merely pointed out that "Ubuntu is not in the category of 'rolling release' distros like Arch." Do you agree with that statement?

---

### Post by scwizard on 2012-02-22
> **snowpine said:**
> Please don't tell me what to recommend; I would recommend Arch over Debian Testing any day of the week! (And I have used both extensively, have you? ;))

That being said, if you carefully re-read my post, I did not recommend Arch to the OP, I merely pointed out that "Ubuntu is not in the category of 'rolling release' distros like Arch." Do you agree with that statement?
If you've used both extensively then I suppose you're right.

I heard some pretty bad things about arch, but I guess I was misinformed. Sorry about that.

Also yeah, of course it's a true statement.

---

### Post by ayozito on 2012-02-22
I see Linux Mint is rolling release too (just learnt this concept), maybe I will try it again but using old Gnome because the few days I had it with Gnome3 I got tired about crashes

---

### Post by snowpine on 2012-02-22
> **ayozito said:**
> I see Linux Mint is rolling release too (just learnt this concept), maybe I will try it again but using old Gnome because the few days I had it with Gnome3 I got tired about crashes

"Rolling release" is typically for users who want the latest applications, which means Gnome 3. If you are the type of user who prefers using older, familiar, well-tested software like Gnome 2, then I would question whether rolling release is right for you. (One notable exception is Fuduntu, which is rolling-release based on Fedora but "frozen" at Gnome 2.)

Mint is based on Ubuntu and is not a rolling release distribution. Mint recently added an experimental rolling-release "LMDE" based on Debian Testing, but based on what I've read, I really can't recommend it.

---

### Post by ayozito on 2012-02-22
Aaa Mint isn't? I made a fast search at Google and read that it is.

I want lastest versions, but stable ones... For example Gnome 3 sucks hard due to crashes, so I don't want it by now.

---

### Post by haqking on 2012-02-22
different app versions on a version that was released 2 years before the other one ?

That cant be right, surely not ;-)

---

### Post by snowpine on 2012-02-22
Red Hat Enterprise Linux plans to support Gnome 2 through 2020. (It's definitely not rolling release though! ;))

---

### Post by ayozito on 2012-02-22
Thinking now about the rolling release concept... then what means LTS? because within LTS version doesn't get updates, how will be it fine for the next 5 years?

---

### Post by snowpine on 2012-02-22
> **ayozito said:**
> Thinking now about the rolling release concept... then what means LTS? because within LTS version doesn't get updates, how will be it fine for the next 5 years?

If your system works "fine" today then why would it mysteriously stop being "fine" in 1 year, 2 years, 5 years?

LTS releases are the best choice for servers, corporate environments, schools, etc. where it's important to have a reliable, consistent, familiar system, with no surprises, from day-to-day.

LTS does indeed get "updates" (bug fixes, security patches) but not "upgrades" (leaps from one version of an app to a newer, different version of that app).

Here is a great article on the topic (written for Red Hat but also applies to Ubuntu): [https://access.redhat.com/security/updates/backporting/?sc_cid=3093](https://access.redhat.com/security/updates/backporting/?sc_cid=3093)

---

