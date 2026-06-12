---
title: "mounting just a folder"
date: 2010-12-27
forum: General Help
---

### Post by Jguy on 2010-12-27
I am dual booting an installation of Windows 7 with ubuntu 10.10, both 64bit.

I have a minecraft installation in both that I want to play both saves folders on both, so I don't have to copy files over from Windows to Ubuntu, or switch the OS to play. I want it to be 'transparent' if possible. If you play minecraft, you know that windows and Linux installations do not save their worlds to the same folder.

In Windows, the saves of Minecraft reside in C:\Users\username\AppData\Roaming\.minecraft\saves

in Ubuntu, the saves of Minecraft reside in ~/.minecraft/saves

like mentioned above, I want to make it so that my saves of Minecraft are available to Windows and vise-versa, so I don't 1) have to switch operating systems to play the world on windows and the world on Ubuntu or 2) don't have to copy the save files back and forth.

Is there anyway I could mount just that folder that houses the Minecraft save files in windows to a mountpoint, say /mnt/minecraft/saves? Even better, can I mount that folder to ~/.minecraft/saves?

If I remember right, my /~ drive resides on /dev/sdc1 and my Windows installation is /dev/sda5. I would think the command would be something like...

$ sudo mount /dev/sda5/Users/App Data/Roaming/.minecraft/saves -t ntfs ~/.minecraft/saves

would that be correct? I also don't mind mounting just that saves folder to something like /mnt/minecraft/saves and creating a link from my home directory to that folder.

thanks for any insight you can provide.

---

### Post by dcstar on 2010-12-27
Mount the C: drive permanently using the **pysdm** package.

Then just make a shortcut from the Windows location to replace the Linux one (rename the shortcut and move it to the proper location). Make sure the shortcut permissions are the same as the original you are replacing.

---

### Post by gsgleason on 2010-12-27
> **Jguy said:**
> I am dual booting an installation of Windows 7 with ubuntu 10.10, both 64bit.

I have a minecraft installation in both that I want to play both saves folders on both, so I don't have to copy files over from Windows to Ubuntu, or switch the OS to play. I want it to be 'transparent' if possible. If you play minecraft, you know that windows and Linux installations do not save their worlds to the same folder.

In Windows, the saves of Minecraft reside in C:\Users\username\AppData\Roaming\.minecraft\saves

in Ubuntu, the saves of Minecraft reside in ~/.minecraft/saves

like mentioned above, I want to make it so that my saves of Minecraft are available to Windows and vise-versa, so I don't 1) have to switch operating systems to play the world on windows and the world on Ubuntu or 2) don't have to copy the save files back and forth.

Is there anyway I could mount just that folder that houses the Minecraft save files in windows to a mountpoint, say /mnt/minecraft/saves? Even better, can I mount that folder to ~/.minecraft/saves?

If I remember right, my /~ drive resides on /dev/sdc1 and my Windows installation is /dev/sda5. I would think the command would be something like...

$ sudo mount /dev/sda5/Users/App Data/Roaming/.minecraft/saves -t ntfs ~/.minecraft/saves

would that be correct? I also don't mind mounting just that saves folder to something like /mnt/minecraft/saves and creating a link from my home directory to that folder.

thanks for any insight you can provide.

Not correct.  Try this:
```
sudo mkdir /mnt/windows
mkdir -p ~/.minecraft/saves
sudo mount /dev/sda5 /mnt/windows
sudo mount -o bind /mnt/windows/Users/username/AppData/Roaming/.minecraft/saves /home/username/.minecraft/saves
```

you can then put entries in your /etc/fstab to make it to this upon boot.

---

### Post by djeikyb on 2010-12-27
I would have fstab mount the windows partition on boot automagically. Then I would make a symlink in your home folder pointing the windows save directory (eg: ln -s ~/minecraft/saves /mnt/windows/path/to/appdata)

---

### Post by Jguy on 2010-12-27
Well, I would rather not have to mount the entire drive if I just have to use one folder.

gsgleason: Thanks for the step by step.

How would I set the bind in fstab? Don't think I've ever done that...

---

### Post by djeikyb on 2011-01-17
You must mount the entire drive. It's the nature of the thing. Mounting the drive exposes it to linux. Only then can linux see the file system. The file system provides a map of the files and folders. No map, no files.

---

### Post by geirha on 2011-01-17
```
/some/dir /mount/point none bind 0 0
```

---

