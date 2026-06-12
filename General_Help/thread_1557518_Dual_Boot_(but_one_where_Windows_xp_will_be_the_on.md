---
title: "Dual Boot (but one where Windows xp will be the one that will automatically boot)"
date: 2010-08-20
forum: General Help
---

### Post by Korea91 on 2010-08-20
I want to install ubuntu for my parent's for security purposes/ banking and what not. 

Anyway I know from experience that grub (dual boot) will always have the ubuntu boot on the top of the list therefore ubuntu will always automatically log in unless I were to choose windows 7 before the time ran out. 

So therefore, I hope you understood what I've asked and can help me. I want it so it will automatically boot with xp, but whenever they need to use the bank or something they can do so by simplly turning on the computer and arrow key down at the grub dual boot list.

Thank you in advance ):P

---

### Post by drs305 on 2010-08-20
After you have Ubuntu installed and Grub2 recognizing Windows, install StartUp-Manager. It's a simple GUI app that will let you easily designate the menu timeout and default OS.

You can read more about StartUp-Manager by clicking on the "SUM" link in my signature line.

If you would rather edit the Grub2 files manually, look at the "G2 - Tasks" link.

---

### Post by Korea91 on 2010-08-20
thank you

---

### Post by Korea91 on 2010-08-22
great thanks it worked... now im going to sound paranoid but, for myself I like  ubuntu as well but i can't seem to get it to make a dual boot when installing, it keeps saying that it needs to erase the existing os. 

Therefore I was wondering, do you think it would be safe for me to just use the ubuntu as a live cd (run it like that) and do my banking and when I'm done take out the cd and use windows 7 again?

---

### Post by dougalkerr on 2010-08-22
Dump Windows 7. Do you need it?
Be free and install software for almost anything you want for nothing.

Yes there may be software available for Windows only for some time to come but, what can a Windows machine do that a Linux machine (properly configured) can't?

As long as Linux has the software programs you need to get the job done there will be no need for Windows.

Think about it...

I have been using both Operating Systems for years now and have to say that Linux and especially Ubuntu or Ultimate Edition that I use, is now very mature and problem free.

If you have been using Linux for some time and it does everything that you need...

I use mine for Internet browsing, email, Office programs and working with my photos and recently for compiling a video of an anniversary do for watching on TV.

---

### Post by oldfred on 2010-08-22
You can use the liveCD. When you close it since it is read only it does not save anything.

Some windows installs use all 4 primary partitions. You can only have 4 primary partitions but normally make the last an extended partition with many logical partitions. Win7 uses 2 primary and then many vendors add a recovery and another utility partition. Then there is no place for the extended and you cannot install. Many decide to make the recovery backups and delete it or depending on what is in the utility they may back it up and delete it. You can create it again inside the extended and copy it back. But some portables may have system keys hard wired to use that partition, so they may or may not work.

---

### Post by Monotoko on 2010-08-22
Why will the CD not allow you to install with dual-boot? You should just be able to select "Install Ubuntu and Windows Side-By-Side" or something similar.

It will then partition the drive and you should be able to continue with installation into one partition, not affecting the Windows partition.

The LiveCD will be a slow and painful process, I would either advise you to install to a hard disk using the method above, or use a distro that boots straight into RAM. (You will need a smaller distro for that, DSL or similar)

---

### Post by drs305 on 2010-08-22
I'd recommend installing Ubuntu, but as a second choice, if you are at least still using the Grub2 menu, I'd place the LiveCD iso on your hard drive and add a menuentry for the ISO.

The advantage is that you won't have to keep inserting the LiveCD and it will boot faster to the LiveCD desktop. 

This link will help you with the menuentry if you are interested:
[ISO Booting with Grub 2]("http://ubuntuforums.org/showthread.php?t=1549847")

---

### Post by Korea91 on 2010-08-22
Thank you all for your responses..
I'm not sure why there is no side by side install. I had just installed it for my parents with that option and had done so on my previous laptop, but apparently for some reason i can't on this one.

Also I would dump windows 7 but there are certain programs that I need for school that only work on a windows os ( i know terrible) haha but I guess I'll just have to bear through it.

Once again thank you all and, I think I will take your advice and use the live cd via iso.

---

