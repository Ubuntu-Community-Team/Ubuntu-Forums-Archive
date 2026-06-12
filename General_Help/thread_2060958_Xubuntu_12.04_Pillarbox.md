---
title: "Xubuntu 12.04 Pillarbox"
date: 2012-09-21
forum: General Help
---

### Post by Jpendragon on 2012-09-21
Hey, I'm running xubuntu 12.04, and while I like it's performance, it thinks my moniter is 4x3 apparently. But it is 16x9. When I go into display, these are my only options:
1024x768
840x600
848x480
640x480

I know that the third of those is ALMOST 16x9 (not quite). But if I click that I get a message saying: Not Supported. Which in my Windows Partition only happens if I set a game to a weird resolution. Anyway, Windows runs on 16x9, xubuntu does not.

Does anyone know how I could fix this?

---

### Post by irv on 2012-09-21
The problem is with the driver you are using for your video card.
To find out what VGA compatible controller you have do this in a terminal:
```
lspci -v
```
The look for the VGA compatible controller. Then run the "Additional Drivers" utility and see if there is a driver you can install for your VGA compatible controller.

---

### Post by Jpendragon on 2012-09-21
Okay...... so I don't know exactly what happened. I entered that code, and I was going to post it in a minute, after I followed the rest of his directions. I opened up Additional Drivers, and there were two graphics updates it was saying it could do (I hadn't entered any information, it was just automatically listing them). I clicked on one of them, it said that it failed to update for some reason. I checked, the one I clicked looked like it might want to be done second of the two. So I was going to do that. But (my memory gets a little foggy right here) I think my computer wanted to restart then. I tell it that it can, then I take a nap. When I wake up. The Screen just says "not supported." I restart it, same result.

---

### Post by irv on 2012-09-21
Can you run the lspci -v command and post what video you have. Maybe someone out here will have the same video card you have and they can tell you what driver there are using.

---

### Post by Jpendragon on 2012-09-21
No, because my monitor is saying that the signal it's getting is not supported. I can't see anything if I load xubuntu. If xubuntu was outputting a signal that my monitor could recognize, then I would tell you.

---

### Post by irv on 2012-09-21
> **Jpendragon said:**
> No, because my monitor is saying that the signal it's getting is not supported. I can't see anything if I load xubuntu. If xubuntu was outputting a signal that my monitor could recognize, then I would tell you.

If you can boot to the grub menu run in the recovery mode and then run a fix on your video so you can get back to your desktop.

---

### Post by Jpendragon on 2012-09-23
I tried running every scan I could find, it made no difference, do you know where a specific scan is?

---

### Post by irv on 2012-09-23
You are just spinning your tires here. Maybe you would be better off doing a reinstall. That would fix your problem.

---

### Post by Jpendragon on 2012-09-24
I would do a reinstall, but the problem is, I was storing some important files on this partition and I don't want to lose them. When I open up a trial version of xubuntu to see if I can access them, I can browse the folders that they were in, but the only ones I can see/copy/cut/move are the files that were created/downloaded on this partition. If it was moved to this computer via a flash drive or external harddrive, I don't have read/write permissions.

Is there a way to access them? (going to post this on another board as well)

---

### Post by irv on 2012-09-24
> **Jpendragon said:**
> I would do a reinstall, but the problem is, I was storing some important files on this partition and I don't want to lose them. When I open up a trial version of xubuntu to see if I can access them, I can browse the folders that they were in, but the only ones I can see/copy/cut/move are the files that were created/downloaded on this partition. If it was moved to this computer via a flash drive or external harddrive, I don't have read/write permissions.

Is there a way to access them? (going to post this on another board as well)

I am not sure what you are using for a file manager, but if you open up a terminal window and type
```
sudo [file manager name]
```
Enter your password you will be able to copy the files.

---

