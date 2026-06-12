---
title: "Wine 0.9.6 crashes when winecfg -&gt; Audio tab"
date: 2006-01-25
forum: General Help
---

### Post by Eliseo on 2006-01-25
I installed wine 0.9.6 using Automatix and then I tried to run winecfg to adjust some settings, but when I clicked the Audio tab in winecfg the program crashed and wrote this to the console:

```
Creating link /root/.kde/socket-ubuntu.
can't create mcop directory
```

I'm not using Kubuntu, then why is KDE showing up there? And why is the program crashing?

---

### Post by Viro on 2006-01-25
Are you running winecfg as root?

---

### Post by Eliseo on 2006-01-25
[QUOTE=Viro]Are you running winecfg as root?[/QUOTE]
Yes, sorry I forgot to specify, I still get problems with that.
```
sudo winecfg
```

---

### Post by Viro on 2006-01-25
No, what I meant was that you shouldn't be running winecfg as root :). I thought you might have done, since you were trying to write to /root, but it looks like I'm wrong. No idea why it's crashing.

---

### Post by Eliseo on 2006-01-25
Both root and non-root user gives the same problem:

```
eliseo@ubuntu:~$ winecfg
Creating link /home/eliseo/.kde/socket-ubuntu.
can't create mcop directory

```

:( Anyone?

---

### Post by Eliseo on 2006-01-26
Found the solution here!:
[http://groups.google.nl/group/comp.emulators.ms-windows.wine/browse_thread/thread/4e0e59c7bb6c6410/2298146dcf72d61f](http://groups.google.nl/group/comp.emulators.ms-windows.wine/browse_thread/thread/4e0e59c7bb6c6410/2298146dcf72d61f)

I just had to do this:
```
mkdir -pv $HOME/.kde/socket-$HOSTNAME 
```

And voila! No more crashing!

---

### Post by Zeroangel on 2006-02-17
It works! :KS

Hooray for victory!

---

### Post by hectorC on 2006-05-03
some time later... another victory in Dapper. Thank you! This thread solved the same problem.

---

### Post by ubu-for on 2006-05-11
[QUOTE=Eliseo]Found the solution here!:
[http://groups.google.nl/group/comp.emulators.ms-windows.wine/browse_thread/thread/4e0e59c7bb6c6410/2298146dcf72d61f](http://groups.google.nl/group/comp.emulators.ms-windows.wine/browse_thread/thread/4e0e59c7bb6c6410/2298146dcf72d61f)

I just had to do this:
```
mkdir -pv $HOME/.kde/socket-$HOSTNAME 
```

And voila! No more crashing![/QUOTE]

Had the same problem because of choosing "Standard" instead of "Emulation" for DirectSound (winecfg).

I use DapperDrake and wine 0.9.12-dapper.

THX for your simple and great HOWTO!

---

### Post by menaar on 2006-06-22
Worked for me too, But I had to do winecfg without the sudo.

sudo still crashed me.

---

