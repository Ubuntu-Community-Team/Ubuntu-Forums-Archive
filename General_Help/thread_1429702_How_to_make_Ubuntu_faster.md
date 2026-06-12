---
title: "How to make Ubuntu faster"
date: 2010-03-14
forum: General Help
---

### Post by malikge on 2010-03-14
Hello.
I am using Ubuntu 8.10 and on surfing the net I found out how to make ubuntu perform faster. I came across this site.

[http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_]("http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_")

 But when I try to implement the thing in the site it did not work.
when I enter the following command,
```
$ sudo gedit /etc/sysctl.conf
``` to change the vm.swappiness=10. It did not show "vm.swappiness".
When I try this command
```
sudo gedit /etc/inittab
```
it shows a blank page.
Any help on that? Or any other way by which I can make it perform fast.
Thanks

---

### Post by oldos2er on 2010-03-14
First of all, you should be using **gksu gedit**, not sudo.

You have to add the line **vm.swappiness=10** to sysctl.conf.

The file /etc/inittab doesn't exist because Ubuntu uses Upstart. See [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

---

### Post by Rocket2DMn on 2010-03-14
As a side note, Ubuntu 8.10 reached End Of Life next month, and will no longer be supported.  I suggest either upgrading to a supported version (e.g. 8.10->9.04, or even 8.10->9.04->9.10).  If you don't like to upgrade your system every 6 months, you might consider doing a fresh install of 10.04 when it is released next month since it is a LTS release and will be supported on the desktop for 3 years.

The file /etc/inittab is not used in Ubuntu (and actually doesn't exist).  It is a configuration file used by the legacy init system.  Ubuntu uses Upstart rather than init.

---

### Post by malikge on 2010-03-14
Ok Thanks for replay.
I came to know few weeks back that 8.10 is supported until April 2010.
Is it possible to upgrade to newer versions without effecting my personal setting. For example Themes, softwares and other applications.

---

### Post by Slim Odds on 2010-03-14
> **malikge said:**
> Ok Thanks for replay.
I came to know few weeks back that 8.10 is supported until April 2010.
Is it possible to upgrade to newer versions without effecting my personal setting. For example Themes, softwares and other applications.

For the more part, yes. But backup important files!!!

Sometimes certain applications are removed from the distro (rarely). Most stuff will be moved forward to the latest versions.

I recently upgraded a machine from 8.10->9.04->9.10 (64 bit) without issue.

---

### Post by nexx on 2010-03-14
To make my system faster I disabled compiz, it really makes a difference on my 500mb thinkpad T43. Do other peoples have the same issue ?

---

### Post by Rocket2DMn on 2010-03-14
> **malikge said:**
> Ok Thanks for replay.
I came to know few weeks back that 8.10 is supported until April 2010.
Is it possible to upgrade to newer versions without effecting my personal setting. For example Themes, softwares and other applications.

Yes, but you have to take the upgrade path from one version to the next, you cannot skip versions.  So you would go 8.10->9.04->9.10 then to 10.04 when it is released next month.  If you have /home mounted on a separate partition, you could reinstall and keep your settings, but you would just have to re-install your non-default applications as well (their settings are still kept).

It's OK to take the upgrade path, it may just take longer is all.  By the time you get to the latest, you may need to tweak some things because programs and other settings do not always remain constant between versions of Ubuntu.

---

### Post by dcstar on 2010-03-14
> **malikge said:**
> Hello.
I am using Ubuntu 8.10 and on surfing the net I found out how to make ubuntu perform faster. I came across this site.

[http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_]("http://www.zolved.com/synapse/view_content/28224/How_to_tune_your_Ubuntu_PC_for_faster_performance_")
.........

What a joke, telling people to remove some TTYs that use about 600 KiB of memory each!

Big performance gain there..... if you only have 128M of RAM.

---

### Post by colobix on 2010-03-14
You should do 1 or 2 things.
1. upgrade your RAM, or
2. install xubuntu instead.

---

### Post by malikge on 2010-03-15
Thanks all for replying.
Before that I was planning to upgrade it to 10.04, but now will have to upgrade it to 9.04.
Thanks again.

---

### Post by rahilm on 2010-03-15
> **Rocket2DMn said:**
> Yes, but you have to take the upgrade path from one version to the next, you cannot skip versions.  So you would go 8.10->9.04->9.10 then to 10.04 when it is released next month.  If you have /home mounted on a separate partition, you could reinstall and keep your settings, but you would just have to re-install your non-default applications as well (their settings are still kept).

It's OK to take the upgrade path, it may just take longer is all.  By the time you get to the latest, you may need to tweak some things because programs and other settings do not always remain constant between versions of Ubuntu.
I think you can do LTS-LTS upgrades without going through the beta versions in between. You can go directly 8.04-10.04. I still have to confirm this though.

---

### Post by Slim Odds on 2010-03-15
> **rahilm said:**
> I think you can do LTS-LTS upgrades without going through the beta versions in between. You can go directly 8.04-10.04. I still have to confirm this though.

This is true, but he said that he was using 8.10

---

### Post by Rocket2DMn on 2010-03-15
The only time you can jump releases is from LTS -> LTS.  So, if you were using 8.04, then you could go 8.04->10.04.  I would recommend upgrading all the way to 10.04 when it is released, since 9.04 will only be supported for another 6 months before you will be forced to upgrade again, and you will still be using an outdated version.

EDIT: Sorry, I missed some of the later posts.  Rahilim, yes, you can go LTS -> LTS.

---

### Post by malikge on 2010-03-16
I am using 8.10, can I directly go to 9.10?

---

### Post by NightwishFan on 2010-03-16
It is not supported to do so, I wouldn't try. Just do the version to version upgrade or back up and do a fresh install. I always have a separate /home partition to keep data and settings.

---

### Post by colobix on 2010-03-16
I have 9.4 installed, so how will it be for me when the 10,4 comes out?
Will it be possible for me to upgrade to 9,10 or will it go directly to 10,4

---

### Post by NightwishFan on 2010-03-16
Upgrade first to 9.10, then to 10.04. It means a bit of downloading, but it should turn out fine. Run the janitor when your done to get some tweaks. I am using 10.04 right now, and I like it so far. (Except indicators)

---

### Post by Slim Odds on 2010-03-16
It's been explained quite a few times.....

LTS to LTS is fine.

Any other release must go through all previous releases.

---

### Post by malikge on 2010-03-16
ok... Now I know what is LTS and how does the upgrade procedure goes.
Now to upgrade it to 10.04 first I have to make a back up of my /home partition and then do a fresh installation of 10.04 and then replace it's home directory with previous one?

---

### Post by Slim Odds on 2010-03-16
> **malikge said:**
> ok... Now I know what is LTS and how does the upgrade procedure goes.
Now to upgrade it to 10.04 first I have to make a back up of my /home partition and then do a fresh installation of 10.04 and then replace it's home directory with previous one?

That will work.

I always install with a separate partition for /home
Then I can always do a fresh install without having to mess with /home

---

