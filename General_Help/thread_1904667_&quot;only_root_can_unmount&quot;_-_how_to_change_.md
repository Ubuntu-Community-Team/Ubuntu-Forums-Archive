---
title: "&quot;only root can unmount&quot; - how to change permission(?)"
date: 2012-01-05
forum: General Help
---

### Post by kurja on 2012-01-05
I recently replaced a failing media hdd with a new one, and had some permission(?) issues with it - I only had access to the new drive as root, untill I ran ```
sudo chown -R <username>:<username> <drive name>
```

Current issue with that drive is that I can not unmount it! I get an error message saying that only root can unmount dev/sdb1 from...

This is pretty much a single user home computer, with a single user account on it, and I'd very much like to get rid of any restrictions when it comes to accessing files, especially on that media hdd. What command do I need to run to make it so?

Running ubuntu lucid.

---

### Post by mcduck on 2012-01-05
How are you mounting the drive in the first place? If youa re doing it through fstab (like you should for any drive you want mounted on every boot), add "user" into the mount options to allow users to mount and unmount the drive.

What comes to the "single user" thing, if the machine is connected to the Internet you pretty much can forget about single-user machines. At the best it's a machine where you are trying to keep yourself as the only user. And all the user/group systems, permissions, password requests and such are the very means of doing that. The generic rule is that any computer connected to Internet (or any other non-private network) should be handled as a multi-user system.

---

### Post by kurja on 2012-01-05
> **mcduck said:**
> How are you mounting the drive in the first place? If youa re doing it through fstab (like you should for any drive you want mounted on every boot), add "user" into the mount options to allow users to mount and unmount the drive.

What comes to the "single user" thing, if the machine is connected to the Internet you pretty much can forget about single-user machines. At the best it's a machine where you are trying to keep yourself as the only user. And all the user/group systems, permissions, password requests and such are the very means of doing that. The generic rule is that any computer connected to Internet (or any other non-private network) should be handled as a multi-user system.

Yes, it's getting mounted in fstab. I'll try adding the user option, thanks.

As for the single user thing, yes, you are of course right but I don't think having the ability to unmount a drive would compromise my security ,) And usually people do have more or less unrestricted access to their locally saved files, anything else would be seen by the end user as needlessly complicated.

---

### Post by Morbius1 on 2012-01-05
It's probably just me but I don't understand the nature of the problem.

If you have it mount automatically by placing mount instructions in fstab then why do you want or need to unmount it?

If you want the freedom to mount it at will or unmount it at will and you are the only user then don't put anything in fstab and mount it by accessing it through Nautilus.

Am I missing something?

---

### Post by mcduck on 2012-01-05
> **Morbius1 said:**
> It's probably just me but I don't understand the nature of the problem.

If you have it mount automatically by placing mount instructions in fstab then why do you want or need to unmount it?

If you want the freedom to mount it at will or unmount it at will and you are the only user then don't put anything in fstab and mount it by accessing it through Nautilus.

Am I missing something?

Using fstab instead of Gnome's automatic mounting allows more detailed configuration of mount options, location, owner, permissions and so on.

---

### Post by kurja on 2012-01-05
> **Morbius1 said:**
> It's probably just me but I don't understand the nature of the problem.

If you have it mount automatically by placing mount instructions in fstab then why do you want or need to unmount it?

If you want the freedom to mount it at will or unmount it at will and you are the only user then don't put anything in fstab and mount it by accessing it through Nautilus.

Am I missing something?

I do like to have it mounted at startup, mostly because of Picasa - if I launch that while the picture files can't be accessed, it will re-start building it's database which takes like 20 hours to complete.

But, I cannot spin down the drive while it is mounted - unless I've mistaken? And this storage space disk often has little use for long periods of time.

---

### Post by Morbius1 on 2012-01-05
Well, you got me on spin down. I can honestly say I've never given that any thought.

As far as mount location, options, ownership, and permissions it's true you can spicify mount location and a few options but you can't assign ownership and permissions in fstab for a Linux filesystem only a Windows filesystem. For a Linux filesystem it's done after the mount.

---

### Post by mcduck on 2012-01-05
> **kurja said:**
> I do like to have it mounted at startup, mostly because of Picasa - if I launch that while the picture files can't be accessed, it will re-start building it's database which takes like 20 hours to complete.

But, I cannot spin down the drive while it is mounted - unless I've mistaken? And this storage space disk often has little use for long periods of time.

Actually you should be able to spin down a hard drive with mounted partitions, as long as nothing is accessing it for a long enough period of time. At least my laptop's drive sure does spin down if I let it idle for a while.

---

### Post by kurja on 2012-02-24
Resurrecting a thread here, as I came across this same issue when booting from a live cd - again, I don't have permission to access anything on that disk.

Is there a way to make it available to all users?

---

### Post by kurja on 2012-03-15
bump.

---

