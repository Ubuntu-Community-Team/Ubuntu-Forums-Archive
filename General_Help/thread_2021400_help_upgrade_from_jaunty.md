---
title: "help upgrade from jaunty"
date: 2012-07-09
forum: General Help
---

### Post by beanco on 2012-07-09
Hi all!

I just got a different computer with jaunty on it at work.

The linux guy is on vacation. I want to get upgraded now, not in September.

I want to do it from the command line.

I do not want to burn a disk, use a flash drive etc.

So, what's the fastest way ... heck even installing a new version is fine because i do not need anything on this box...


thanks

robi

---

### Post by Rex Bouwense on 2012-07-09
Jaunty has reached its end of life and I'm not sure if the repositories are still functional but one way to do it would be to upgrade from 9.04 to 9.10 and then to 10.04 Lucid (which is a long term support version supported until April of next year).  From there you can update to the current version 12.04 which is the next LTS version.  That is a long and tedious way to upgrade.  If I were you I would simply download the current version and burn it to a disk.  It would be much quicker.  In any event I would definitely back up any data that I had on the computer, just in case.

---

### Post by Topsiho on 2012-07-09
You don't say why you don't want to burn a disk, and why you want to use the command line. I think you don't want the only practical route to go.

Download Ubuntu 12.04, burn it as an image to a CD-Rom (I always use rewritables for this so I can reuse them for a next version), at the lowest possible speed, and then install the new Ubuntu over the old one. If you have a separate /home version (which I advise), then do NOT have it formatted during the install, and so preserve your data and configurations. But anyhow: backup your data first.

So I quite agree with Rex.

Upgrading from one version to the next one is very time consuming, AND may mean enormous downloads, depending on what you have installed on your computer. It's also more risky. Having to do this several times ...

Wish you luck :)

Topsiho

---

### Post by jmfal on 2012-07-09
Welcome to Ubuntu

Read this before you start

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

Click on "read upgrade notes " in first paragraph .

---

### Post by arubislander on 2012-07-09
I would also like to pitch in my vote (for what it counts) to doing a fresh install. An upgrade throught the various versions will take a very long time and the result is not guaranteed to be satisfactory.

---

### Post by beanco on 2012-07-09
So it seems a fresh install is the way to go....

At work, when I got the new machine I had no access to CDs or Flash drives. That's why I wanted to go the CLI route... and because I like doing stuff from the CL... I am not good at it but I like it....


Now, fresh install from teh CL?


Thanks

Robi

---

### Post by beanco on 2012-07-09
> **jmfal said:**
> Welcome to Ubuntu

Read this before you start

[http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

Click on "read upgrade notes " in first paragraph .


The upgrade manager did not work. I forgot to mention that in the OP....

Sg about no more support if I remember correctly....

Robi

---

### Post by Topsiho on 2012-07-09
Forget about using the command line until after the install :)
You have enough opportunity to get aquainted with it later.

Just install from the LiveCD and first thing after that, you install all the updates, as the LiveCD represents the situation at the time it was released, end of April (August 23 (I believe) a new "point"release will be published, which represents the situation at that time).

This update you can do from the command line if you wish. You can get the information you need with

man apt-get

in a terminal.

Every command that is affecting the system should be done as (temporary) root, by preceding the command with sudo, and typing your password (entered during the install) when being asked for it.

Topsiho

---

### Post by beanco on 2012-07-09
> **Topsiho said:**
> Forget about using the command line until after the install :)
You have enough opportunity to get aquainted with it later.

Just install from the LiveCD and first thing after that, you install all the updates, as the LiveCD represents the situation at the time it was released, end of April (August 23 (I believe) a new "point"release will be published, which represents the situation at that time).

This update you can do from the command line if you wish. You can get the information you need with

man apt-get

in a terminal.

Every command that is affecting the system should be done as (temporary) root, by preceding the command with sudo, and typing your password (entered during the install) when being asked for it.

Topsiho

Topsiho,

I know about sudo and being root etc.....

I just remember the sys-op at another place I work at taking my laptop and opening a terminal and upgrading, or actually I think it was a fresh install all from the command line and I thought it was all cool.....


Robi

---

### Post by Topsiho on 2012-07-10
:)

If you read man apt-get you know how he ***upgraded*** from the command line.
As I respect your appetite for the command line (I am glad, that is) I let you find out for your self how the sys-op did this.

Upgrading however is different from doing a fresh install. The latter you do from a LiveCD (or an alternate CD, which is a little less graphic, and might come in handy, when the LiveCD fails, as it has an other installer).

There are distributions that let you install from scratch, you may find out, eg. at distrowatch. That is really cool, installing from source. Compiling your own kernel, as lean as possible, just for your own hardware. But I have no experience with that. If you go that way, you'll learn a lot, I guess.

Topsiho

---

