---
title: "Suggestion for apt-get/dpkg"
date: 2009-07-21
forum: General Help
---

### Post by SnappyU on 2009-07-21
Hi all,

Anyone who uses Ubuntu for a while will encounter the need to add repositories so that a certain app can be installed.

This can either be done via the synaptic gui or the commandline with some editing of the sources.list file.

Since this is pretty much standard, is it possible to write an app to read an install metafile that contains the respository and package name and install the said package(s)?

1. Metafile
2. App MetaInstaller

1. Metafile
This defines the following:
1. Repositories needed
2. Packages to be installed

2. App MetaInstaller
This app does not do the installing itself, but adds the repositories defined in the Metafile and calls apt-get or ipkg to install the package(s).
Program flow:
1. Read Metafile - Store repository links and package names
2. Add or update repository links to /etc/apt/sources.list
3. Call apt-get to update package list
4. Install using apt-get for packages defined

This will allow users to do a One-Click-Install from app web sites, instead of having to either use Synaptic or a text editor to manually add repositories and then install the app using synaptic or the terminal console.

---

### Post by scaine on 2009-07-21
This is proposed for Karmic - sorry, no links, but a quick search in that forums should show you that it's on its way.

---

### Post by SnappyU on 2009-12-12
Thanks Scaine for the info. :)

---

### Post by Zorael on 2009-12-12
> **SnappyU said:**
> This will allow users to do a One-Click-Install from app web sites, instead of having to either use Synaptic or a text editor to manually add repositories and then install the app using synaptic or the terminal console.

This is always the subject of hot debate.

I don't believe any system should be set up to be able to install applications from web sites with only one click. Installing applications means writing to outside of your home directory (unless you fakeroot), and that *implies* trusting the distributor.

While adding a .repo file extension that automatically adds a repository would certainly be convenient, it's the first (or second) step on the path to malware. It makes it even easier to apply [social engineering](http://en.wikipedia.org/wiki/Social_engineering_%28security%29), which even at present isn't impossible.

```
Your Ubuntu is slow! Download this to clean your registry!

We have detected viruses in your Ubuntu! Download this to be safe!

Download this new codec to speed up your videos!
```
The PPA system is a lesser demon. It's awesome as it allows people to host their own code, but at the same time you should only trust Canonical's code and the code of *those you trust*. That's not easy in an Internet community.

To redeem it, the source of the binaries hosted is always available for scrutiny. In the case of a binary-only download (from the "web"), it's a black box - you can only see what files it installs, and sort of guess what the files are doing by observing them (or reverse-engineering them).

Any Joe can go create a PPA, download the mplayer source and modify it to wipe your home directory after a period of time, then upload it to his PPA as a version update to what's in the repositories. Then he can go to the forums and create a howto describing how to install a fresh and much faster mplayer for faster video. The very very large majority will not look at the source, and those who install it will technically be "infected", to use the virus term. If the deletion of the home directory is delayed, the cause isn't even immediately obvious to the user.

But someone is bound to look at the source. Perhaps someone following mplayer's development who wants to see which revision this is, and what really differs with the source of the repository mplayer. You can't do this if the source isn't hosted. PPAs always have it, but not all deb repositories are PPAs.

I'm not even sure I like the new **add-apt-repository** command, which I guess is what scaine was referring to. Nor do I really enjoy the idea of an **apt://** protocol, but at least that can only invite users to install a package from the repositories they already have set up.

The real killing blow would be to be able to specify a repository right away, like **apt://mplayer@apt.freehosting.com.tw**. Et voila; an .exe installer.

---

### Post by SnappyU on 2010-02-01
@Zorael:  Requiring users to copy and paste lines after lines of script to execute commands or adding an app via multiple steps through ppa merely make it more convoluted to install.  It does not make it safer.

If a user has decided to install an app, going through 3 or 5 steps or a single click is just a matter of difficulty, not safety.

Sudo apt-get requires just an authentication check anyway, and not a source-code verification.  Present PPA apps can be simplified with a single-click install.
Trust should be established through code review and code signature authentication.  Security through convolution is only as good as security by obfuscation.

---

### Post by SnappyU on 2010-08-13
It seems like getdeb.net has implemented the one click install for a few months now.  It works for some browser but not for others.  I got it working for a netbook running Lucid but not for another notebook running Jaunty.

There is also a way to add a ppa directly into synaptics package manager, and the source repos and signature key will be imported automagically.  Just do an update and you are ready to install the new apps.

---

### Post by mcduck on 2010-08-13
> **SnappyU said:**
> It seems like getdeb.net has implemented the one click install for a few months now.  It works for some browser but not for others.  I got it working for a netbook running Lucid but not for another notebook running Jaunty.

There is also a way to add a ppa directly into synaptics package manager, and the source repos and signature key will be imported automagically.  Just do an update and you are ready to install the new apps.

They are just using apturl, which has been around in Ubuntu for several versions now.

[https://wiki.ubuntu.com/AptUrl]("https://wiki.ubuntu.com/AptUrl")

It still uses the repositories, and you still have to add the repository yourself. (which, in my opinion, is a good thing.)

Apturl originally had a feature that allowed it to automatically add a repository, but I'm not sure if that still exists, I've never seen it used as such feature would definitely cause security problems..

(It's still able to temporarily *enable* a repository, but it must be already configured in your system so it doesn't *add* repositores for you)

Personally, I don't think that adding repositories by just clicking on a web site wold be smart. While I do think that making things easier and simpler is a good thing, making shooting yourself in foot easier isn't smart. Adding a repository should require a bit more consideration than just clicking a link on a web page.

---

### Post by Zorael on 2010-08-13
Ages old but I seem to have missed this reply.

> **SnappyU said:**
> Trust should be established through code review and code signature authentication.  Security through convolution is only as good as security by obfuscation.

I'm not *actively* advocating security through convolution, but I will say that I **trust** the review process of code uploaded to the official Canonical repositories more than I **trust** what someone has uploaded to their personal ppa, more than I **trust** any external non-launchpad ppa that may *or may not* be hosting the actual source alongside the binaries they offer.

In the perfect and boring world people would only install packages from the official repositories. That way they would only use programs whose code had gone through the proper channels to ensure a malware-free binary. A quick '**grep ^deb /etc/apt/sources.list.d/*.list | grep -v deb-src | wc -l**' shows I'm using 28 external sources (as it happens, all launchpad ppas), so I'm not an example of that ideal.

Launchpad only accepts source uploads, and always keeps the source available for download even after binaries have been compiled and packaged. So it's a lesser demon; the code still hasn't gone through security review the way "official" packages have, but the code is *there* for anyone to review. Launchpad guarantees this, and we make the decision to **trust** that guarantee. The vast majority of external apt repositories offer source and binaries in the same way, but there's nothing from keeping Evil Ed from simply disabling the source section of his **fastubuntu.mine.nu** repository. Launchpad isn't there to police him.

I concede that my feelings toward **add-apt-repository** is in lieu with security-by-convultion, in the sense that it will make more people use ppas. That is, in itself, a good thing. But it also means moving from Canonical's protective ward. The code is still available for review (thanks to Launchpad), but there's no guarantee it *has* been reviewed. So it's against the ideal world but closer to the real one.

---

### Post by SnappyU on 2010-10-28
> **Zorael said:**
> Ages old but I seem to have missed this reply.



I'm not *actively* advocating security through convolution, but I will say that I **trust** the review process of code uploaded to the official Canonical repositories more than I **trust** what someone has uploaded to their personal ppa, more than I **trust** any external non-launchpad ppa that may *or may not* be hosting the actual source alongside the binaries they offer.

In the perfect and boring world people would only install packages from the official repositories. That way they would only use programs whose code had gone through the proper channels to ensure a malware-free binary. A quick '**grep ^deb /etc/apt/sources.list.d/*.list | grep -v deb-src | wc -l**' shows I'm using 28 external sources (as it happens, all launchpad ppas), so I'm not an example of that ideal.

Launchpad only accepts source uploads, and always keeps the source available for download even after binaries have been compiled and packaged. So it's a lesser demon; the code still hasn't gone through security review the way "official" packages have, but the code is *there* for anyone to review. Launchpad guarantees this, and we make the decision to **trust** that guarantee. The vast majority of external apt repositories offer source and binaries in the same way, but there's nothing from keeping Evil Ed from simply disabling the source section of his **fastubuntu.mine.nu** repository. Launchpad isn't there to police him.

I concede that my feelings toward **add-apt-repository** is in lieu with security-by-convultion, in the sense that it will make more people use ppas. That is, in itself, a good thing. But it also means moving from Canonical's protective ward. The code is still available for review (thanks to Launchpad), but there's no guarantee it *has* been reviewed. So it's against the ideal world but closer to the real one.
Thanks for sharing your thoughts.  It has helped me understand better your viewpoints. :)

I should go enable subscription to posts that I create or comment on.  :)

---

