---
title: "Outdated packages and how to update them"
date: 2009-11-05
forum: General Help
---

### Post by Rovanion on 2009-11-05
The thread title might be quite misleading. This is not a guide on how to update the packages that are outdated in the official repository. Rather the opposite, I'm posting here with the question of how to do so.
 It seems like about every package in the official, atleast in the universe repo, are outdated by some time. And some does not even run in ubuntu any more, yet they are in the repository. As an example we have the kompozer package that is so outdated that it krashes if you open up an arcive menu. Other applications such as Kdenlive are since long depricated and no longer supported by the developers. In the case of Kdenlive, which is a non-linear video editing tool, the version 0.7.3, as opposed to the current version 0.7.6, misses a great set of tools that are vital for editing and have a good set of crash bugs fixed.

Now to the point: How can I help out with this issue. How can I as a user who spend quite some time helping people out with problems that are directly linked to outdated packages help the lot of them at the same time and contribute updated packages to the repositories? Because seriously. There are applications which crash a lot in the repos because they are old and do not match the newer versions of Gtk+ or other libraries that are packed with newer versions of Ubuntu.
How can I contribute?

---

### Post by alphaniner on 2009-11-05
I don't know about updating packages in the repos, I suspect there is a lot of red tape involved.  I think a better alternative is to learn what it takes to make good, universally compatible .deb files and start your own PPA and/or upload to getdeb.net.

---

### Post by snowpine on 2009-11-05
Hi Rovanion, you misunderstand how Ubuntu works. 

The release name will tell you exactly how "outdated" each package is. For example, 9.10 is the "October (10) 2009 (9)" release. This means it will always use whichever version of an application was stable as of October 2009. 

For example, when Firefox 4.0 comes out, Ubuntu 9.10 users will continue to use FF 3.5, as that was the stable version in October 2009.

Six months from now, you can upgrade to 10.04 and get a whole new batch of six-month-newer applications.

Hope that clears up the mystery for you. :)

---

### Post by Rovanion on 2009-11-05
As it is now you are correct. I can absolutely add a PPA for each and every application which is essentially what I have to do today. Except for some cases where a PPA is not availabel.

The thing is that most of the users I encounter in an IRC channel do not know at all what I'm talking about when I tell them to add a PPA. The result is that new users have to go trough all these hoops to get a simple video editing application running and that is not the human way of doing it. My point is that the applications in the universal and other repositories are sometimes severely outdated and that it's no good for the user experience at all.

So I'm wondering. How can I get involved in updating the universal repositories. Or are these locked down by conanical and untouchable?

---

### Post by snowpine on 2009-11-05
ps I forgot to mention the "backports" project... it sounds like exactly what you need:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Ubuntu becomes "outdated" (by your definition) as soon as it is released... that is the price you pay for using a stable Linux distribution. For a certain type of user, I would recommend a rolling release distro (like Arch or Sidux) but if your friends can't follow the easy 3-step directions to add a PPA, they're not going to have much luck with Arch. :)

---

### Post by Rovanion on 2009-11-05
I'm not a fan of fighting over semantics but I would not call an application that crashes when the Archive menu is used stable. And it has been that way trough 9.04 and now in 9.10.

But thanks for the link to UbuntuBackports. I'll look into it.

---

### Post by alphaniner on 2009-11-05
As for kompozer, there are known issues with the version in the repos and the GTK version used by Ubuntu:

[QUOTE="http://kompozer.net/download.php"]KompoZer 0.7 is not compatible with GTK &#8805; 2.14 &#8212; expect crashes.[/QUOTE]

Ubuntu 9.04 uses GTK version 2.16 (I think).

And anyhow, the version in the repos is 0.7.10, which is considered the current stable release by the kompozer folks.

---

### Post by snowpine on 2009-11-05
> **Rovanion said:**
> I'm not a fan of fighting over semantics but I would not call an application that crashes when the Archive menu is used stable. And it has been that way trough 9.04 and now in 9.10.

But thanks for the link to UbuntuBackports. I'll look into it.

Nobody is fighting; you asked for help and this is a friendly discussion. :)

The word "stable" in reference to Linux distributions has absolutely nothing to do with reliability, bugs, crashes, etc.

Rather, "stable" means "no longer receiving major updates." Ubuntu is considered a stable distro because its users can feel confident the functionality of their system will never change in a significant way. (Only minor bug fixes and security patches.)

An "unstable" distro (like Arch or Debian Sid) is also known as "rolling release" and will give its users new versions of applications as they become available. This type of distro doesn't have distinct releases (Intrepid/Jaunty/Karmic/etc.); you install it once and keep using it forever.

A poorly-designed "stable" distro might have lots of bugs and crash all the time, while an excellent "unstable" distro might actually be very reliable. See the difference?

Anyway, to your original point, kdenlive 0.7.6 was released on October 8, 2009... it doesn't matter how awesome, incredible, cool, "stable", etc. it is... Ubuntu 9.04 came out in April 2009, so it will never, ever give you kdenlive 0.7.6 as an automatic update. We can argue it until the cows come home, but that's simply not how Ubuntu is designed.

That doesn't mean you can't use 0.7.6 in Jaunty... on the contrary, there are several ways to do it. A PPA is always my recommendation, but you could also simply download the latest version from kdenlive.org (I call this "the Windows way") and then of course there is the backports project. I'm not sure why you're anti-PPA... a PPA is basically saying "I want a stable system, except for one particular application I would like to keep up to date." System->Administration->Software Sources->Third-Party Software... it's easy!

---

### Post by Rovanion on 2009-11-06
I do myself have nothing against PPA's. And I do use them, tough I mostly add them trough the terminal.
The thing being that I'm usually stationed in a help IRC channel and I do at times encounter people who are having applications crashing on them that are directly from the official repos. I then have to guide them on to a new way of getting applications.

You may want to consider this a papercut. The new user having to go trough adding new repos on his second day of Linux.

And I guess there is really nothing that I can do, about the standard Ubuntu way. Maybe it should be considered by some derivative to use backports by default.

But it's a papercut.

---

