---
title: "Any way to install Ubuntu Netbook Remix through Wubi on a non-Atom notebook?"
date: 2010-05-22
forum: General Help
---

### Post by GhostToast on 2010-05-22
Hi all,

I am curious about Ubuntu Netbook Remix, and I don't have a netbook.  I have a ASUS UL20A-A1 with an Intel Core 2 Duo, and I would like to try out Ubuntu Netbook Remix, but I do not have an Atom processor.  I was wondering if there was any way for me to try out Ubuntu Netbook Remix on my notebook through Wubi?  Or is there a way to install the Ubuntu Netbook Remix interface on a regular Ubuntu installation, so I could easily switch between the regular GNOME desktop and the netbook remix desktop?

Thanks!

-GhostToast

---

### Post by snowpine on 2010-05-22
You do not currently need an Atom processor for Ubuntu Netbook Edition. As of 10.04, there is no longer a separate Ubuntu release or "port" for the Atom. UNE 10.04 should run on any computer that's capable of running Ubuntu and has a supported graphics card. You can add the "netbook launcher" to regular Ubuntu through the Software Center.

---

### Post by warfacegod on 2010-05-22
As far as I know, you never *needed* an Atom to run the Netbook Editions. The whole Atom thing was just about some minor power saving features. I've had 9.04, 9.10, and 10.04 Netbook versions running on my 2.8 GB Hyper Thread Intel P4 with no issues.

---

### Post by snowpine on 2010-05-22
> **warfacegod said:**
> As far as I know, you never *needed* an Atom to run the Netbook Editions. The whole Atom thing was just about some minor power saving features. I've had 9.04, 9.10, and 10.04 Netbook versions running on my 2.8 GB Hyper Thread Intel P4 with no issues.

I believe that 8.04 was the only Ubuntu Netbook release that required an Atom processor. Support for the Atom is built in to current versions of the Linux kernel, so a separate Atom release is no longer necessary.

---

### Post by warfacegod on 2010-05-22
> **snowpine said:**
> I believe that 8.04 was the only Ubuntu Netbook release that required an Atom processor. Support for the Atom is built in to current versions of the Linux kernel, so a separate Atom release is no longer necessary.

I didn't know 8.04 even had a Netbook version. Even still, that release was over two years ago. Why is this Atom thing *still* persisting? I run across threads like this one fairly often. Its either you need an Atom or Netbook runs better on Atom.

---

### Post by snowpine on 2010-05-22
> **warfacegod said:**
> Why is this Atom thing *still* persisting?

Because of documentation [like this]("https://help.ubuntu.com/community/Installation/SystemRequirements#Ubuntu%20Netbook%20Edition"):

> Ubuntu Netbook Remix is designed to run well on netbooks with typically minimal specs, i.e.:

    * Intel Atom processor @ 1.6 GHz
    * 512 MiB of system memory (RAM)
    * 4 GB of disk space
    * Screen of 1024x600 resolution
    * Graphics chipset with support for visual effects 

It is easy to read that as "Netbook Remix is designed for the Atom processor."

---

### Post by warfacegod on 2010-05-23
I see your point. Perhaps its time for Canonical to clarify that a little better.

---

