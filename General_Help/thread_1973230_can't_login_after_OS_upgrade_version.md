---
title: "can't login after OS upgrade version"
date: 2012-05-04
forum: General Help
---

### Post by YigalB on 2012-05-04
I tried updating the OS.
Now I get an "Ubunto 11.10" Login screen.
When I enter my password, something is happening, but it goes back to the Login screen.

If I place a wrong password, I get a "wrong passowrd" message, so at least I know my password, but I cant Login.

Any idea what can I do?
Can I recover to the previous stable OS version?

Thanks

---

### Post by electrojustin on 2012-05-04
Do you have a lightdm custom background? I'm in the same boat here-fixed by installing gdm or, alternatively, changing the lightdm background back to default.

---

### Post by YigalB on 2012-05-05
I think the issue was resolved. 
I succeeded to login after many trials (at least human will is stronger than computer's cpu power).
The look and feel was strange, as if the upgrade was not fully finished, and the OS was in between old and new version.

I was guided by the update manager to run```
sudo apt-get install -f
```, but when i tried to run it, i was guided to run ```
sudo dpkg --configure -a
```
This worked, and I could run the first line of code.
Now I have a working OS, but still facing update problems.
More updates to come.

---

### Post by YigalB on 2012-05-05
Once I got a readable screen, I lunched the update manager.
After long run and many updates I got my desktop displayed, but no menus at all: not the side menu, not the top.

So I could launch any program :(

Is there a way to launch programs manually?
How can I add the side menus, so I will have access to the programs?

---

### Post by roffisserver on 2012-05-05
Do you have the Unity or have you installed a custom GUI. Because it did the same thing to me when I had gnome.

---

### Post by YigalB on 2012-05-05
> **roffisserver said:**
> Do you have the Unity or have you installed a custom GUI. Because it did the same thing to me when I had gnome.
I don't know what Unity is. and I didn't install any custom. I always work out of the box.
Is there a way to operate the OS by keyboard? How can I run update manager and other software without GUI? or terminal window?

---

### Post by philinux on 2012-05-05
> **YigalB said:**
> I don't know what Unity is. and I didn't install any custom. I always work out of the box.
Is there a way to operate the OS by keyboard? How can I run update manager and other software without GUI? or terminal window?

ctrl+ alt+ t to get a terminal then run

```
unity --reset
```

---

### Post by YigalB on 2012-05-05
Thanks!
Now I know how to open terminal window.

I run the ```
unity --reset
```
but it ended with > trace/breakpoint trap (core dump)

I didn't see core dump for a long time...

What should I do now?
would re-install help?
Can I go back to the previous version? How?

---

### Post by YigalB on 2012-05-05
problem Solved:
The auto update failed, mainly because part of the new version was installed, but the update-manager was set to the old version.
So I burned the CD.
Once inserted, the new update-manager was launched and now I have a system working.
Lesson: better to update from installation CD.

---

