---
title: "Replace Server"
date: 2011-08-05
forum: General Help
---

### Post by ambre on 2011-08-05
Hi,

I want to upgrade my Server (10.04LTS) to a newer, faster machine.  I have complete tar backups of my existing server on an external USB HD that I hope to use to make the upgrade.

I have a 10.04 Desktop LiveCD that I can use to boot up the new machine.
My procedure was going to be:
[LIST]
Boot new machine from LiveCD
[/LIST]
[LIST]
Format new hard disk
[/LIST]
[LIST]
Plug in USB external backup disk
[/LIST]
[LIST]
Untar backup onto new disk
[/LIST]

However, I can't seem to mount the USB disk on the new machine.

I would appreciate someone confirming that my procedure is feasible and if it is, give me a little help along the way.

If I am totally off beam then could you suggest the 'correct' way to upgrade my server.

Thanks,
Ambre

---

### Post by WorMzy on 2011-08-05
Yeah, that's a perfectly acceptable way of "installing" a Linux OS. Just make sure that you install grub to MBR of the new disk, update the grub.cfg (or whatever Grub 2 uses these days), and update /etc/fstab after "installing".

If you don't install grub, you won't be able to boot (duh!); and if you don't update grub.cfg, grub won't be able to find your root partition; same goes for fstab, you'll need to update the UUID for "/".

You can find out the UUID for your new partition by running
```
sudo blkid -c /dev/null
```

Regarding this:
> However, I can't seem to mount the USB disk on the new machine.

Do you get an error or anything? Can you mount it manually, via a terminal?

```
sudo mount /dev/sd## /mnt
```

---

### Post by ambre on 2011-08-11
Thanks for the info WorMzy, I'm sure it's good advice if I knew what to do with it!  (I'm not being sarcastic!)

You see, the more I think I know, the more I realise how little that is.

I'm still persevering with my upgrade.  Thank God it's not critical at the moment else I would be in serious trouble.  It's a case of one step forward, two steps back right now.

My initial procedure was a bit naive.  Yes, I have restored my backup onto the new machine but that is just the begining. As you pointed out, I can't boot the new machine and as yet have not found a way to install grub2 on it to give it a fighting chance.

My backup refers specifically to my old machine.  The new machine has different hardware so there are files in the tarball that need to be amended to reflect this.  I have no idea which/how many files I need to amend.

My old server has been running as I want it to for some time now, but getting there was a long road.  I did not document all of what I did to overcome the many problems I encountered along the way and the thought of having to start over is just too much.

I have backups!  But what use are they to me if I can't use them?  I have searched the 'net for a Howto but cannot find anything.

My plea to the community, on behalf of all novice users like myself, is for a detailed howto covering the migration of a working server to a new box using tar backups as the source.  Not only would that be useful to upgraders, like myself, but also to those whose machines die on them.

Regards,
Ambre

---

