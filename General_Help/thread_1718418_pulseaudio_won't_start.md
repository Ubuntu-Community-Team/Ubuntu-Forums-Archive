---
title: "pulseaudio won't start"
date: 2011-03-31
forum: General Help
---

### Post by alexchamberlain on 2011-03-31
Hi all,

pulseaudio will not start. The reason for this is as follows...

E: core-util.c: Home directory /home/alex not ours.

/home/alex is owned by root as it is an NTFS partition (dual-boot), and hence, can not be chowned by me.

I think I need to persuade pulseaudio to go elsewhere, but this is as far as I have got in sorting out the problem. Any help would be greatly appreciated.

---

### Post by alexchamberlain on 2011-03-31
I think this could be sorted by running pulseaudio in system mode. Anybody know how?

---

### Post by Kickofighto on 2011-07-10
> **alexchamberlain said:**
> I think this could be sorted by running pulseaudio in system mode. Anybody know how?

I'm having same problem exactly. Did you get it working in the end? not just pulse but some of the alsa functionality is also missing. Thinking of reformatting home partition to fat32 at this stage

---

### Post by CatKiller on 2011-07-10
> **alexchamberlain said:**
> 
/home/alex is owned by root as it is an NTFS partition (dual-boot), 
Don't do this.

If you want a partition accessible from Linux and Windows, use a different partition and mount it somewhere else. NTFS can't handle Unix-style permissions, which causes problems like this one.

---

