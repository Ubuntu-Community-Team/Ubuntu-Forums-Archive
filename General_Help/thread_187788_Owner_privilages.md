---
title: "Owner privilages"
date: 2006-06-03
forum: General Help
---

### Post by livingword26 on 2006-06-03
I am running a dual boot with windows xp. From the linix side, I can access "My Documents" on the windows side and copy items to Linux from Windows, but when I attempt to put something into the "Documents" folder from Linux I get an error message that says since I am not the owner I cannot write this folder. I know I have sharing set up in the windows program because I can access it from one of my other computers, but not from the Linux. How can I gain the "owner" status in Linux?

---

### Post by Rackerz on 2006-06-03
Open up a terminal and type, 'gksudo nautilus' then try and transfer what you were trying to transfer, see if it works ;).

---

### Post by taurus on 2006-06-03
You can't write to your Windows partition because root probably owns it!!!  And by the way, I assume that partition is an NTFS which means you're better be careful when you write to NTFS because funny thing can and would happen to your Windows partition...

---

### Post by livingword26 on 2006-06-03
[QUOTE=Rackerz]Open up a terminal and type, 'gksudo nautilus' then try and transfer what you were trying to transfer, see if it works ;).[/QUOTE]

**Reply from terminal:**  

(Nautilus:5123):GnomeUI-WARNING**:While connecting to session manager:Authentification rejected, reason:none of the authentification protocals specified are suppported and host-based authentification failed

---

### Post by livingword26 on 2006-06-03
[QUOTE=taurus]You can't write to your Windows partition because root probably owns it.[/QUOTE]

I know very little about linux. Why does root ownership mean I cannot write to it.

---

### Post by Monster_user on 2006-06-03
Linux has stricter permissions than Windows does. The "Root" is similar to the "Administrator", or "Owner" account in Windows.

Only the root can change files that are "owned" by the root. Windows drives in Ubuntu are automatically setup to be owned by the root. This is done during the boot process, since Ubuntu cannot set the ownership of the files themselves. Due to the differences between Windows, and Linux.

Any other accounts in Linux are setup to be "user" accounts, and do not have permission to modify any files in any folder other than their "home" folder.

gksu, gksudo, and sudo are programs that can be used to allow you to temporarily run programs as the root. This is more secure than logging in as the root. Gksu is a Gtk (Gnome/XFCE) password prompt. IT will ask you for your password everytime you type it in, and then run any program that is typed just after it (gksu gedit). Gksudo is similar, but only requires you to use your password once, for a short time period. Su, and sudo are the console versions, and MUST be entered in a console.

Before you run 'gksudo nautilus', you have to type 'xhost +', to enable the launch of "GUI" programs, or any program that opens in a new window.

xhost +
gksudo nautilus

Nautilus is the Ubuntu/Gnome file manager. Make sure you 'right-click' any files you copy over, and adjust their permissions. set them to your account, or enable full read, and write access.

---

