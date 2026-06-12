---
title: "Deaktop has wallpaper only"
date: 2010-08-02
forum: General Help
---

### Post by sandcrab on 2010-08-02
Hi

I recently came back from vacation to find my pc froze and had to reboot.
The following message screens came up. Any help in repairing is greatly appreciated.

Could not update ICEauthority file /home/curtis/.ICEauthority

There is a problem with your configuration server.
(/usr/lib/libconf2-4/gconf-sanity-check-2 exit with status 256)

Nautilus could not create the following required folders:
/home/curtis/Desktop, /home/curtis/.nautilus

The pc then comes to a Desktop with nothing but Ubuntu generic wallpaper, nothing else.

The hard drive has 320 gb with 75gb free.

Thanks for your time

---

### Post by WorMzy on 2010-08-02
Sounds like your permissions have gotten screwed up. Did you, by chance, run a graphical application with sudo at some point? You should use gksu or gksudo for graphical applications. Can you boot into recovery mode (Read point 11 on [this page]("http://ubuntuforums.org/showthread.php?t=1195275") if you're unsure how to do that), drop to a root shell, and run

```
chown curtis:curtis /home/curtis/.ICEauthority
chmod 644 /home/curtis/.ICEauthority
```

Then restart with

```
shutdown -r now
```

---

### Post by sandcrab on 2010-08-02
Chown: cannot access /home/curtis/.ICEauthority : No such file or directory

This is what came up

---

### Post by WorMzy on 2010-08-02
I see. Can you run
```
ls -l /home
```

and post the output here.

---

### Post by sandcrab on 2010-08-02
ls: cannot access /home:no such file or directory

---

### Post by TheNerdAL on 2010-08-02
I think this has happened to me too. It could be that your hard drive is having bad sectors.

---

### Post by WorMzy on 2010-08-02
Something has definitely gone horribly wrong somewhere. If your home folder's disappeared then you've likely lost all your work. If you had anything important on the partition, I'd recommend that you run something like testdisk to recover as much of the data as you can, then reformat the partition and reinstall Ubuntu.

You could try running fsck on the partition before you follow the above advice, to see if it could perhaps fix the problem, but fsck should run on the root partition every boot time to check for problems by default anyway, so I don't think a manual run will be of any use.

---

### Post by Irony on 2010-08-02
Delete your .ICEauthority file and .local file using a live cd. Then reboot.

---

