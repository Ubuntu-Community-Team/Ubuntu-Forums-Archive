---
title: "can we play directly .iso video??"
date: 2009-07-10
forum: General Help
---

### Post by abhilashm86 on 2009-07-10
i downloaded a video which strangely has .iso format, so can we play it directly, which player supports it, the file is 350MB,
do i need to write it to cd and then play or can i directly convert to other foramt??

---

### Post by eival on 2009-07-10
try right cliking on the file an choose properties an rename .iso to .avi

if you see the current icon used for the file change to a picture/image then it will play in VLC player.

---

### Post by Cl0ud9 on 2009-07-10
You can mount an iso to the cdrom mount point with
```

sudo mount -o loop ~/file_location/filename.iso /media/cdrom0

```

---

### Post by jpt266 on 2009-07-10
I use Gmount-Iso to mount the iso file. I use mount point cdrom0, then you can use or play the iso file.

Try that.

JT.

---

### Post by waznot on 2009-07-10
> **Cl0ud9 said:**
> You can mount an iso to the cdrom mount point with
```

sudo mount -o loop ~/file_location/filename.iso /media/cdrom0

```

Along the same lines...

Is it possible to tinker this so an APTonCD ISO (aptoncd.iso) can be added to the repository for Synaptic Package Manager as if you were adding a CD?

Or perhaps, put in a different way, can you make the computer think it has more CD drives than it actually does?

---

### Post by Cl0ud9 on 2009-07-11
> **waznot said:**
> Along the same lines...

Is it possible to tinker this so an APTonCD ISO (aptoncd.iso) can be added to the repository for Synaptic Package Manager as if you were adding a CD?

Or perhaps, put in a different way, can you make the computer think it has more CD drives than it actually does?

You can certainly use this command with an aptoncd iso. I have never tried making Ubuntu think it has more cd drives than it actually does, but it may be as simple as making a new directory such as cdrom1 in /media. Try it and it may work.

---

