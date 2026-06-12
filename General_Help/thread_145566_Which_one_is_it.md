---
title: "Which one is it?"
date: 2006-03-16
forum: General Help
---

### Post by robertall on 2006-03-16
[http://ubuntuforums.org/showthread.php?p=112157](http://ubuntuforums.org/showthread.php?p=112157)

Need some help. I am quite new to linux (had experience with 98, xp, Mac Os 9.2 and fedora core), and i want to get away from windows, and i cannot seem to get my ubuntu to work.

The main problem is that ubuntu is setting a too big resolution. my monitor cannot handle 1600x1200.

The thread above is the problem or the confusion.

I know what to do sortof, i have figured out how to use the boot manager.

I just need to know if i use vga=791 or vga=792.

Can you please help me by telling me which is the correct one to use?

Robert.

---

### Post by tronica on 2006-03-16
i'm not sure if i follow, is the desktop res to large? if so you would edit the xorg.conf and set you default res there.

---

### Post by robertall on 2006-03-16
I cannot access unbuntu at all mate, i tryed to access it after editing, and the same problem keeps happening. The problem is that i am unsure what to do, and i could be wrong.

Robert.

---

### Post by tronica on 2006-03-16
so i take it your at the command prompt and you need to do:

sudo nano /etc/X11/xorg.conf
(password)
then find this section
> Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"CM2019"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

then change the res under your defualt depth which is probally 24, under that just change the res to your liking, to on the safe side just change the first res in each section to the one you want. Then hit Ctrl+o, then hit enter. the Ctrl+x to exit.

---

### Post by robertall on 2006-03-16
[QUOTE=tronica]so i take it your at the command prompt and you need to do:

sudo nano /etc/X11/xorg.conf
(password)
then find this section


then change the res under your defualt depth which is probally 24, under that just change the res to your liking, to on the safe side just change the first res in each section to the one you want. Then hit Ctrl+o, then hit enter. the Ctrl+x to exit.[/QUOTE]
tronica: I cannot even boot unbuntu with getting 'Out of Scan Range' on my screen. Is there a way to edit it in grub?

---

### Post by tronica on 2006-03-16
i not sure about that, maybe someone here can answer that one. when you installed ubuntu did it ask you for resolution?

---

### Post by robertall on 2006-03-16
Nope, it did not ask for resolution.

Thanks for the help btw.

Edit: I saw it in a post, but does ctrl+alt+- change the resolution?

---

### Post by rejser on 2006-03-16
i think you can edit grub parameters by pressing "e"
vga 791 I think you should run. Forget xorg.conf, doesn't matter until the computer start the xorg. server

---

### Post by robertall on 2006-03-16
As a conclude to my edit in my past post, i have managed to get the login screen working and logged in works anyway. Yippe, ubuntu rocks!

How exactly do you use that function?

Is it vga=791 or vga 791?

Edit: When i login to my account with the username robert, it does not give me root permissions. Why?

And what is the password to the account 'root' after installing using the username robert?

I am asking because i have got to install PengAOL using terminal, and it does not want to work using my current account.

Any help please?

ps: My version is the one with the 'password bug in a .dat file'. I looked there and only found the password for my own account, robert.

Robert.

---

### Post by taurus on 2006-03-16
It should be "vga=791" NOT "vga 791"...  Also, you don't need to be root to edit anything.  Just use "sudo" instead!!!
```

sudo gedit /boot/grub/menu.lst

```

---

### Post by nanotube on 2006-03-17
and when sudo asks you for password, enter your user password, btw. :)

---

