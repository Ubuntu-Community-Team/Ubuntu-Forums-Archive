---
title: "asking root password during startup ??"
date: 2009-10-10
forum: General Help
---

### Post by chinmaya_n on 2009-10-10
Hi

I'm stuck with a big problem.....
Some how my system has got unclean shutdown and everytime i start the system it is undergoing disk-checking and in at 14% asking for the root password, which i've not changed i.e default (no root password).
I only have a single user! so i typed that users password, but it showed incorrect password and prompted for password again... I'm stuck here...

I tried in another way :
pressed "alt+ctrl+F5" and logged in as a general user under tty5.
Then tried to change the root password using *"$sudo passwd root"* but it showed an error stating [B] Authentication token Manipulation Error ... password unchanged 
[/B]

Plz help me... Its urgent!!
(Now i'm using livecd)

---

### Post by lloyd_b on 2009-10-10
Have you tried booting in recovery mode?  This is automatically a "root" session, so it shouldn't require any passwords.

Lloyd B.

---

### Post by khelben1979 on 2009-10-10
> **chinmaya_n said:**
> I'm stuck with a big problem.....
Some how my system has got unclean shutdown and everytime i start the system it is undergoing disk-checking and in at 14% asking for the root password, which i've not changed i.e default (no root password).

Maybe the system is incorrectly partitioned? What partition does it get stuck on? And how long have you had the system up and running before you got problems? If the system contains no important files, I would suggest you do a complete reinstall of the whole system.

If your harddrive have taken damage in some way and this is the cause of your troubles, then running Windows and using [spinrite]("http://en.wikipedia.org/wiki/Spinrite") is a way of trying to get it working again.

---

### Post by chinmaya_n on 2009-10-11
> **lloyd_b said:**
> Have you tried booting in recovery mode?  This is automatically a "root" session, so it shouldn't require any passwords.

Lloyd B.

Yes, tried using recovery mode.... but droped at the same point !!
NO use :(:confused:

---

### Post by sooper on 2009-10-11
I have a similar problem.  The last upgrade hosed my system, so I booted recovery, and it brought me to the menu.  When I selected either the root with net connection or just the root prompt, it gave me the option to enter a "maintenance" root password or hit control D to return to the menu. Sounds like a beta issue to me.  I think I'll wait a while and see if they fix it on the next upgrade

---

### Post by RuleMaker on 2009-10-11
> ...so i typed that users password...

try using an empty password, I think it's empty unless you change it.

Also check your /etc/passwd file, maybe it got corrupted on unclean shutdown.

---

### Post by chinmaya_n on 2009-10-13
> **RuleMaker said:**
> try using an empty password, I think it's empty unless you change it.

Also check your /etc/passwd file, maybe it got corrupted on unclean shutdown.

I tried the empty password, but vain!!
I'll check /etc/passwd file .... what i should i do if it has corrupted ?? Will it work if i copy the same file from my friends system ?? 
Will it permit me to do it via livecd ??

---

### Post by coffeecat on 2009-10-13
If you are trying to do a fsck, then yes you can do that from a live CD, and you won't need a password. Simply open a terminal and "sudo fsck...." whichever partition(s) need checking.

**Don't** copy /etc/passwd from another system. You'll just make matters worse.

I don't know why the system is prompting you for the root password, but it used to be that there was a (hidden) root password. In earlier versions of Ubuntu, a random root password was generated at installation - not a blank password. There was a way of changing that, but I won't go into that because it's against forum policy. If Jaunty works the same way, then there is a root password, but unknown and unrecoverable, which is probably why the blank password didn't work. The idea that there is no root password in Ubuntu is a common misperception because of the use of the sudo model. It's just that it isn't needed in ordinary use.

Anyway, the live CD seems to be the way to go. Good luck!

---

### Post by az on 2009-10-13
> **chinmaya_n said:**
> Hi

I'm stuck with a big problem.....
Some how my system has got unclean shutdown and everytime i start the system it is undergoing disk-checking and in at 14% asking for the root password, whi...

Okay, this is not normal.  There is something very wrong with this.  The root password is not the problem here.  The fact that you are being dropped into a shell which is asking you for this is.

First off, are you able to boot a previous kernel in your grub list?  That will boot you with another initrd that is unlikely to be broken.

If the problem still persists, then you should consider hardware problems (disk, ram or overheating).

---

### Post by chinmaya_n on 2009-10-13
> First off, are you able to boot a previous kernel in your grub list? That will boot you with another initrd that is unlikely to be broken.
Actually i removed the previous kernal listings in the grub.....!!! 
-----
Thanks to **coffeecat** i executed ```
sudo fsck /dev/sdaX
```(/dev/sdaX is the problamatic disk and that is the root paritition).
I executed this from the shell it provided when it pressed _alt+cntl+F5_(Not from the livecd, i dont know if it works with the livecd) It corrected some errors and asked for reboot. When rebooted the system, everything was fine! Voila!!
Now i could use the system as before :popcorn:

I'm Really very happy :)
And Thanks to Everyone!!

---

