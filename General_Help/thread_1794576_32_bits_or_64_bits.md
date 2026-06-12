---
title: "32 bits or 64 bits"
date: 2011-07-01
forum: General Help
---

### Post by Beatboxx on 2011-07-01
I'm about to install the Ubuntu server edition, but I don't know if I need 32 bits or 64 bits. I know that 32 bits is limited to ~3.5GB of Ram. I got 4GB. My CPU is the Intel pentium G620 (Sandy bridge), and supports 64 bits. Will I be able to run all my software, like google chrome, boxee etc? Ow, and I'm going to setup Raid 1, maybe Raid 5 in the future.

---

### Post by amauk on 2011-07-01
64bit is no problem

Just FYI, the server edition is (obviously) for servers, and so does not have a graphical interface - text consoles only

So I'm a little confused about the references to GUI apps (google chrome & boxee) if you intend this to be a server
You can install a GUI on a server, but maybe use the regular desktop version instead

---

### Post by slooksterpsv on 2011-07-01
> **Beatboxx said:**
> I'm about to install the Ubuntu server edition, but I don't know if I need 32 bits or 64 bits. I know that 32 bits is limited to ~3.5GB of Ram. I got 4GB. My CPU is the Intel pentium G620 (Sandy bridge), and supports 64 bits. Will I be able to run all my software, like google chrome, boxee etc? Ow, and I'm going to setup Raid 1, maybe Raid 5 in the future.

Server edition won't have a GUI so you'll need to install one. Also 64-bit does support google chrome, boxee, pretty much 95% of anything/everything. The other 5% may be things that they haven't done a 64-bit build of but you may get it to work using ia32-libs and forcing the installation.

Overall yes 64-bit will work and you will need to install a GUI if you use the server edition.

---

### Post by Beatboxx on 2011-07-01
Thanks everyone! And how do I install graphic user interface? I want server edition because I need raid

---

### Post by Genius2999 on 2011-07-01
> **Beatboxx said:**
> Thanks everyone! And how do I install graphic user interface? I want server edition because I need raid
```
sudo aptitude install ubuntu-desktop
```

or if you don't want OpenOffice and associated junk

```
sudo aptitude install --no-install-recommends ubuntu-desktop
```

I think, feel free to someone to correct me :)

---

### Post by Beatboxx on 2011-07-01
What I want is an HTPC/server in one. All it needs to do is a little apache, mysql, ftp and I use rsync for backing up. I use boxee for the HTPC part. I got two 2TB disks (they're exact the same) and I want them in Raid 1. Can I just install Ubuntu server 11.04 64 bits on the 2 empty disks (I'm going to formatt them, ext4), and then after install do 

```

sudo aptitude install ubuntu-desktop

```

Install boxee, and everything, including Raid, works fine?

---

### Post by slooksterpsv on 2011-07-01
> **Genius2999 said:**
> ```
sudo aptitude install ubuntu-desktop
```

or if you don't want OpenOffice and associated junk

```
sudo aptitude install --no-install-recommends ubuntu-desktop
```

I think, feel free to someone to correct me :)

How can you say "junk" none of it's "junk" it's all useful, valuable software, so =P

Yes everything should work, if not let us know and we'll see if we can help you troubleshoot and fix it. Boxee is neat, just wish Linux supported the Netflix portion :(

---

