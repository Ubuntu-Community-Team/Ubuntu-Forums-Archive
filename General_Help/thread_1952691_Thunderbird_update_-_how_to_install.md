---
title: "Thunderbird update - how to install"
date: 2012-04-04
forum: General Help
---

### Post by mjp29mjp29 on 2012-04-04
Thunderbird reports it needs to update by April certain date.  I download the update and can't figure out how to install it.

Is there code to enter into terminal to update it?

---

### Post by QIII on 2012-04-04
How did you originally install it to begin with?

---

### Post by mjp29mjp29 on 2012-04-04
Using Ubuntu Software Center.  I just want to update it now.  The update simply extracts/unpacks into a folder with a bunch of files in it.

p.s. Will Ubuntu automatically update Thunderbird one day with update manager soon?

---

### Post by QIII on 2012-04-04
Don't try to use the tarball.

Would you go to Help >> About and tell me what version you have?

Also, what version of Ubuntu?

---

### Post by uRock on 2012-04-04
The easiest way to upgrade to a newer version is by adding their PPA, then running upgrade manager or upgrading via CLI. To add the PPA run the folling command in a terminal,```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
```After the terminal is finished you may install updates using the following command,```
sudo apt-get update && sudo apt-get dist-upgrade
```
[http://www.webupd8.org/2011/06/thunderbird-stable-ppa-updated-with.html](http://www.webupd8.org/2011/06/thunderbird-stable-ppa-updated-with.html)

---

### Post by QIII on 2012-04-04
11.0.1 is in the repos.  I submit that using the repos may be better at this point than asking the OP to add a PPA, even though we know for certain that the PPA is safe.

No?

Also, if he's getting that message and Mozilla has just announced that they are dropping support for version 3, I wonder if it is more than it may appear.

---

### Post by uRock on 2012-04-04
> **QIII said:**
> Also, if he's getting that message and Mozilla has just announced that they are dropping support for version 3, I wonder if it is more than it may appear.

Very possible. I have T-Bird in one of my VBox installs, will see what it says.

---

### Post by QIII on 2012-04-04
I hope you understand I am not trying to be contentious.

A red flag comes up for me:  if the OP has access to repos old enough that version 11.0.1 is not avaiable, is he about to go out from under Ubuntu version support?

---

### Post by uRock on 2012-04-04
Yup, the version in 10.04's of Thunderbird repo is going to expire. I would think they will be updating the version in the repo the same way they did for Firefox.

---

### Post by QIII on 2012-04-04
And if the OP is on Maverick, he's about to get two punches!

---

### Post by uRock on 2012-04-04
> **QIII said:**
> And if the OP is on Maverick, he's about to get two punches!

Lol, I created a bug report on Launchpad, [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/973877](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/973877)

---

### Post by mjp29mjp29 on 2012-04-04
> **QIII said:**
> Don't try to use the tarball.

Would you go to Help >> About and tell me what version you have?

Also, what version of Ubuntu?


Thunderbird version 3.1.20

---

### Post by uRock on 2012-04-04
> **mjp29mjp29 said:**
> Thunderbird version 3.1.20

Which version of Ubuntu are you using?

---

### Post by mjp29mjp29 on 2012-04-04
I always let the update manager install the latest version of Ubuntu, but how do I check which version.

Thunderbird version is 3.1.20 by the way.

I have taken no action yet, can I, or should I, just wait for update manager to take care of this one day?

---

### Post by QIII on 2012-04-04
How do you let the update manager do that?  There are misconceptions about how that works.

Edit: Sorry, got off bus and walked home before I had a chance to finish.

Not sure what desktop environment you use, so I can't tell you for sure how to use a GUI tool, but if you do 

```
cat /etc/lsb-release
```in the terminal you'll get the info you need on your version.

---

### Post by mjp29mjp29 on 2012-04-04
> **QIII said:**
> How do you let the update manager do that?  There are misconceptions about how that works.

Edit: Sorry, got off bus and walked home before I had a chance to finish.

Not sure what desktop environment you use, so I can't tell you for sure how to use a GUI tool, but if you do 

```
cat /etc/lsb-release
```in the terminal you'll get the info you need on your version.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"

I suppose my Ubuntu is not updated?  What version is current, 11.x?  How does one update that too.  Or do I need to, I'm running an old Pentium 4 here - will the latest version run fine on it.

---

### Post by holycow131415 on 2012-04-04
> **uRock said:**
> The easiest way to upgrade to a newer version is by adding their PPA, then running upgrade manager or upgrading via CLI. To add the PPA run the folling command in a terminal,```
sudo add-apt-repository ppa:mozillateam/thunderbird-stable
```After the terminal is finished you may install updates using the folling command,```
sudo apt-get update && sudo apt-get dist-upgrade
```[http://www.webupd8.org/2011/06/thunderbird-stable-ppa-updated-with.html](http://www.webupd8.org/2011/06/thunderbird-stable-ppa-updated-with.html)

^Do that. Once you add the ppa, check for updates in the update manager and thunderbird updates should flow through. You can add PPAs for alot of other software that isnt officially being updated in the default repos. Its the best way to update your software.

---

### Post by QIII on 2012-04-04
Current version is 11.10.  Not to worry.  You have some time left since Lucid is an LTS (Long Term Support).  But some time in the next couple of months you should upgrade LTS > LTS and go to 12.04.  DON'T do that yet, because Precise is still in Beta.

OK. 

Now that we know your version, and we know that the current version of Thunderbird isn't in your repo and we don't know when it will be, I finally concur with the PPA approach.  I use the PPA.

The reason I didn't go right there is that if we found that you were running a version that had reached, or was about to reach, end of life, we'd have just gotten TBird updated for you a week or two before you found you couldn't update anything else.

---

### Post by QIII on 2012-04-04
> **holycow131415 said:**
> Its the best way to update your software.

Eh, not necessarily.  There are a lot of crappy PPAs out there and you can gum up the works.

Use them sparingly and be sure they are reputable.

---

### Post by mjp29mjp29 on 2012-04-04
ok thanks.  Thunderbird is upgraded.

Now, how does one upgrade to latest version of Ubuntu, download it since apparently update manager doesn't do that?

---

### Post by QIII on 2012-04-04
Don't rush, since you have some time.  Because you are running an LTS, it might not be worth upgrading to 11.10 because the new LTS comes out this month (although it might take a few weeks for all the kinks to be worked out.  Just do you updates to keep your current version up to date.

Hold off for a few weeks.  Your version is still supported.

I'm going to look for a good tutorial for you to use when the time comes rather than trying to work through it here.  Give me a minute on that.

But remember the three main concepts to keep in mind before starting something serious like upgrading versions.: 

1.  Do backups.

2.  Do backups.

3.  Do backups.

And I generally recommend doing backups, too.

EDIT.  

Here's a sample.  Again, don't do this just yet.  Let the new version be released this month, give it a couple of weeks for the dust to settle and update then.

About half way down you'll see the instructions for upgrading from 8.04 to 10.04 (the last LTS to LTS upgrade).  The process should be nearly identical -- or completely identical.

[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by holycow131415 on 2012-04-04
> **mjp29mjp29 said:**
> ok thanks.  Thunderbird is upgraded.

Now, how does one upgrade to latest version of Ubuntu, download it since apparently update manager doesn't do that?

In about 30 days 12.04 LTS will be coming out of beta. Update manager will tell you (by default i believe). 12.04 is in beta 2, which stable wont change much, and youll be current with updates that flow through if you want to upgrade now.

To upgrade from Ubuntu 11.10 or Ubuntu 10.04 LTS on a desktop system,  press Alt+F2 and type in "update-manager -d" (without the quotes) into  the command box. Update Manager should open up and tell you: New  distribution release '12.04' is available. Click Upgrade and follow the  on-screen instructions.

[https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2](https://wiki.ubuntu.com/PrecisePangolin/TechnicalOverview/Beta2)

Ill tell you though, clean installing is always better.

---

### Post by QIII on 2012-04-04
Or...

do-release-upgrade from the command line, like I pointed to...

---

### Post by uRock on 2012-04-04
For reference, the updating for the version in the repos is in the works. [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/972840](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/972840)

---

