---
title: "Ubuntu 9.10 help"
date: 2009-12-11
forum: General Help
---

### Post by cdawley4 on 2009-12-11
Hi,

I just installed 9.10 on my desktop.  I had 9.04 running on a laptop that died a sudden death (LCD got stepped on) about 2 months ago.  I noticed in 9.04, that I was able to choose a login theme.  In 9.10, I set it up so that everyone in the family has an account and it just lists their user names.  Is there a good site for me to go to download a new theme?  I saw a site with a nice 9.10 screen that had colorful icons next to the usernames.  If I can modify my existing login screen to my liking, that would be great too.

Another thing is that my screen that displays the Ubuntu logo that is all white.  I don't know what that screen is called and would like to change it to a different screen as well.

The other thing my computer does is with the grub2 menu.  I installed 9.10 onto a 160Gb Hard drive.  I have an 80G drive with Windows XP on it.  Upon installation, it was configured for dual boot and I am able to read the contents of my XP drive.  That is all great, but is there a way to modify the boot menu to have Windows XP listed 2nd in the list instead of last, under all of the recovery and extra Ubuntu 9.10 entries?

I know this is a lot of information at one time, but since 9.10 came out, it's like a totally different platform than 9.04.

Thanks,

Chris

---

### Post by utnubuuser on 2009-12-11
gnome-look.org

---

### Post by Leppie on 2009-12-11
To add colorful icons next to the usernames, just place the desired avatar in the user's home directory and rename the file to .face
If you have the gnome-control-center installed, you can use gnome-aoubt-me to set avatars for users.

If you only have xp as alternative system, you could add a file like 11_winxp to the /etc/grub.d folder:
```
#!/bin/sh
exec tail -n +3 $0
echo "Windows XP" >&2
cat << EOF
menuentry "Windows XP" {
	insmod ntfs
	set root=(hdx,y)
	search --no-floppy --fs-uuid --set 1e5a005c5a003357
	chainloader +1
}

```
You will have to change (hdx,y) to your xp partition settings (check your /boot/grub/grub.cfg for the correct values). Then make the script executable:
```
$sudo chmod +x /etc/grub.d/11_winxp
```
and make the script /etc/grub.d/30_os-prober inactive (unless you have other systems installed besides your ubuntu and xp installations):
```
$sudo chmod -x /etc/grub.d/30_os-prober
```

---

### Post by BobSongs on 2009-12-11
[FONT="Verdana"]Each user can also choose from a set of face icons in this manner:

**System** > **Preferences** > **About Me**

In the dialog boxe that appears, click the square box to the left of the user's name (first tab). It should open a dialog box to[INDENT]**[FONT=Courier New]/usr/share/pixmaps/faces[/FONT]**
[/INDENT]You'll know you've got the right folder if the top three listed are: **astronaut.jpg**, **baseball.jpg** and **butterfly.jpg**.[/FONT]

---

