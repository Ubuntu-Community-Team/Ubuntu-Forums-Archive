---
title: "How do I update directly to Oneiric and skip Natty?"
date: 2011-10-06
forum: General Help
---

### Post by josephellengar on 2011-10-06
Hi there. This is, based on my research, impossible, but I think that someone has to know a way to do this.

First, my computer critical specs: Gnome, Ubuntu 10.10, 2.6.35-22-generic (later kernels don't seem to work), 64-bit, i7 processor, 8gb RAM, HP-dv7t (laptop), Nvidia GeForce, and, if it matters, my OS drive is an intel G2 SSD 160GB, with separate home and OS partitions.

I typically stay on an Ubuntu-6 months release cycle, so I try to give every release an additional 6 months to mature before I upgrade. Right now I have been trying for about a week to upgrade to Natty, but am having serious driver issues. I decided that from now on I will stay on an LTS-only release cycle, but that means that I somehow have to update to Oneiric before Pangolin comes out in April. Therefore, I have to get to Oneiric, but it is not possible for me to upgrade to Natty. My computer just won't allow it. My (seemingly) intractable problems are outlined in [this thread]("http://ubuntuforums.org/showthread.php?t=1853730").

So my question is, is there any way to skip natty and upgrade directly from Meerkat to Ocelot?

*After which I will upgrade to Pangolin and stay on a 2-year cycle.*

---

### Post by bodhi.zazen on 2011-10-06
> **josephellengar said:**
> So my question is, is there any way to skip natty and upgrade directly from Meerkat to Ocelot?

No, that is not possible.

Also, check the Ubuntu release schedule:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Next LTS is 12.04 ;)

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by josephellengar on 2011-10-06
> **bodhi.zazen said:**
> No, that is not possible.

Also, check the Ubuntu release schedule:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Next LTS is 12.04 ;)

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Yeah, I know. I was hoping that I could go directly to Oneiric and then update from there to 12.04. Since once I upgrade to Natty my computer is literally unusable. But if it's not possible ... :(

---

### Post by fantab on 2011-10-07
Like **bodhi.zazen** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11317670#post11317670") said, you cannot upgrade from 10.10 to 11.10.

Since you have decided to stick only to LTS, I would suggest you hang on to your 10.10 and then clean install 12.04 when it is released.

Meanwhile if you want to try UNITY and familiarize with it you can either clean install 11.10, which is due in a few days or install it on a separate partition and dual boot with 10.10.

---

### Post by josephellengar on 2011-10-07
> **fantab said:**
> Like **bodhi.zazen** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11317670#post11317670") said, you cannot upgrade from 10.10 to 11.10.

Since you have decided to stick only to LTS, I would suggest you hang on to your 10.10 and then clean install 12.04 when it is released.

Meanwhile if you want to try UNITY and familiarize with it you can either clean install 11.10, which is due in a few days or install it on a separate partition and dual boot with 10.10.

Good advice. As usual, the people at the forum are the voice of reason. (no sarcasm) But isn't support for Maverick ending soon? I think it's ending at the beginning of next year. Is it safe to go for four or so months without any updates?

---

### Post by grahammechanical on 2011-10-07
I have not tried this for a couple of years, so my memory may be wrong but is not possible to upgrade from one release to the next upwards to the latest without rebooting?

I seem to remember, that as soon as one upgrade ended Update Manager presented a button offering to upgrade to the next in line. And so I went from 9.04 to 10.04.

You say that later kernels do not seem to work. Do they work sufficiently for you to run Update manager and upgrade to 11.04 and then to 11.10?

I do also recommend creating other partitions to test out the latest versions before upgrading a working install. See if you can get the thing to work the way you like before making the switch. I am doing this right now with 11.10.

Does you machine have dual video cards? There is a problem getting drivers that make full use of the graphic capabilities of the Nvidia Optimus technology. If you have that on your laptop, you should know that there have been improvements. Check out something called Bumblebee.

Regards.

---

### Post by thatguruguy on 2011-10-07
> **josephellengar said:**
> Good advice. As usual, the people at the forum are the voice of reason. (no sarcasm) But isn't support for Maverick ending soon? I think it's ending at the beginning of next year. Is it safe to go for four or so months without any updates?

Yes, support for Maverick will end in April of 2012.  As it happens, that's when the next LTS will roll out.

---

