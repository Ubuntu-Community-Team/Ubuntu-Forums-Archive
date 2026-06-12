---
title: "Won't recognise root password"
date: 2006-05-21
forum: General Help
---

### Post by rustleg on 2006-05-21
I have just installed Ubuntu. I tells me I have 147 updates available and I want to get the updates. When I click on update manager it asks for the root password but when I type it in it rejects it and says it is the wrong password.

However if I open a terminal and type su it asks me for a root password and accepts it giving me the # prompt. Why will it accept it here but not in the update manager?

I installed Ubuntu in expert mode and so it gave me a root account separate from the user account. 

The root password is of the form  "word99" i.e. lowercase characters followed by 2 numbers - nothing weird. I can only guess it is not accepting the keyboard input in the same way but experiments with some other combination (like uppercase letters or the symbol above the number on the number key) were unsuccessful ](*,) 

This newbie would be grateful for any ideas.

(Could it be anything to do with UTF-8 whatever that is?)

---

### Post by Sef on 2006-05-21
Did you do a regular install or an expert install?  If you did a regular install, root is turned off by default.  Read about why here:

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by kaydub on 2006-05-21
For just about any linux system, if your boot loader allows the addition of more parameters (after the bios boot, before linux boot, hit ESC or F2 or whatever)

    * add init=/bin/bash to the list of your kernel-parameters

This puts you into a limited console during boot, then at the prompt type

    * mount -o remount,rw /

This remounts your harddrive read/write instead of read-only because you are going to need to edit a file

    * then use passwd or edit /etc/shadow 

passwd might work editing the /etc/passwd and /etc/shadow files will.  Look for the line like "root*..stuff...*...stuff..*..."

edit out all of the stuff except the word root and the asterixs.

save the files, reboot

linux will ask you for a new root password

BTW use a editor like "vi" in the console, google it for instructions...

good luck

---

### Post by rustleg on 2006-05-22
Hi Kaydub. The system boots ok and I am in Gnome. My root password works fine in a terminal and I can change it there. Is that not good enough? (I don't want to mess with the root password in the boot sequence if I can avoid it - besides I have never used vi and I read it is a bit of a beast:twisted: )

---

### Post by cskeide on 2006-05-22
Maybe you've tried this. Assuming you're in the sudoers file, if gnome/kde asks for administrative privileges you must enter your USER password, not the root password.

---

### Post by AndyCooll on 2006-05-22
Just a thought.

I have similar issues whenever I install Debian. The problem I find is keyboard settings related. So my locale is ok, but the settings for X aren't. For me it is the fact that I use a UK keyboard and my password contains a symbol that is in a different place on the US default one. And for some reason the X settings don't update. 

I edit xorg.conf and everything works ok after that. Might be worth checking the keyboard settings in that.

```
sudo vi /etc/X11/xorg.conf
```

:cool:

---

### Post by rustleg on 2006-05-30
Well I fixed it myself after some cogitation.

It turns out that I wasn't in the sudoers file, so I presume the applications were expecting my password not the root password but if I entered this, it would fail because I wasn't authorised to sudo anything.

This appears it may be a fault in the Ubuntu setup. I used "expert" mode in installation (although I'm certainly not an expert) because otherwise the installation wouldn't allow me to specify where to load grub. The first time I installed Ubuntu with the default method it placed grub in the MBR without asking. As I was trying to set up Ubuntu in a multiboot configuration this screwed up my boot manager.

So I had to reinstall and I then set it up in expert mode which then did give me the option of installing grub to the root partition instead of the MBR. It then also automatically asked me to set up a root account which I did, then a normal user account. I presume it forgot to add the first user account to the sudoers file.

Should I report this as a bug somewhere? (As a newbie this seems a bit presumptious!)

---

