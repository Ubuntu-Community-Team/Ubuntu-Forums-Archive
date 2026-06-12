---
title: "Repositories, Synaptic and other such sillyness"
date: 2011-04-10
forum: General Help
---

### Post by Velasquez on 2011-04-10
Hiya!

I had the problem:

"could not download all repository indexes"

On Cruncheee (An EEEPC specific Crunchbang distro), which I managed to "fix" by changing the /etc/apt/sources.list file by replacing it with stuff I found in a guide. (Shown at end)

Now when I press the Reload button on Synaptic no more errors come up! But when I search for "audacious" (music player) I can only find "crunchbang-audacious-theme", and no actual crunchbang installing things.

What have I actually done to my my sources.list file, did I tell it to look elsewhere for servers with lists of dependencies? Is a "repository" just a place on the internet which has lots of dependencies in it? If I were to just add more and more stuff to my sources.list file and kept pressing "reload" on Synaptic, would I eventually find some packages to install Audacious?

What does "sudo apt-get" do? Is that exactly the same as finding something on synaptic and clicking it?

I'm very new to all of this, and would not be offended at someone linking me to some guide to understanding all of this installing on Linux stuff.

Thanks in advance! If I've been too vague or explained things too poorly please ask!

My new sources.list:
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by mikewhatever on 2011-04-10
Dapper Drake was Ubuntu 6.06, and it reached EOL in June 2009. I guess it's time to move on to a more recent release.

---

### Post by Velasquez on 2011-04-10
Oh, so you're saying the information in my sources.list is way outdated, and if I find one for version ten of ubuntu then more software will be listed in my Synaptic?

---

### Post by mikewhatever on 2011-04-10
Well, something like that. As the release reaches EOL, its repositories are gone as well. Dapper-server is still supported (June 2011), and those may be the packages you see in Synaptic.

---

### Post by Velasquez on 2011-04-10
Thankyou very much :)

---

### Post by snowpine on 2011-04-12
Hi Velasquez (you might remember me from the #! forum)

To clarify, you don't upgrade/switch to a different Ubuntu release simply by changing your software sources. That won't do anything except break your system!

Upgrade instructions are found here: 

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

In your case, however, you're trying to upgrade from an end-of-life release (intrepid) so you'll need to follow these instructions:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

As I mentioned on the other forums, much quicker and easier to do a fresh reinstall of the current release, good luck! :)

---

