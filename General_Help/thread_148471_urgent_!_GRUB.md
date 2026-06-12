---
title: "urgent ! GRUB"
date: 2006-03-22
forum: General Help
---

### Post by 008325 on 2006-03-22
i have 2 harddisk ..

1. Ubuntu
2. Windows XP

now i want to take out ubuntu harddisk to other computer 

but i can not boot the Windows XP ....

and i got the error message

GRUB HARDDISK ERROR

---

### Post by markr on 2006-03-22
You need to fix the MBR.  Insert the WindowXP disk that came with your computer and go ot the recovery options.  You should be able to overwrite GRUB with teh default windows stuff and so get back into Windows.

Mark.

---

### Post by kenweill on 2006-03-22
It will probably happen too on your Ubuntu when you transfer your harddisk with Ubuntu.

I have no experience with two hard disk but only with 2 OS in the same hard disk.

This is about my experience. Don't know if other guys have the same experience.

If your Windows XP is in the second hard disk, you gonna need to have the Windows XP installer CD and Windows 98 installer CD.

Using only the hard disk that contains your Windows, boot from the Win98 CD and do "fdisk /mbr".

Boot from the Win XP CD and install..
JUST DON'T FORMAT YOUR PARTITION.
When it comes to formatting partition, restart your machine.

It should add another option in your boot prompt.
Winxp
and Winxp install(something like this).

You can now delete the other option in Windows.

---

### Post by Ramses de Norre on 2006-03-22
In rescue mode you'll get a terminal. Do fixmbr and then exit, if it still doesn't work you can go back into rescue mode and try fixboot instead of fixmbr.

---

### Post by goatflyer on 2006-03-22
Reinstall the ubuntu drive onto the same cable/slot as it was before.
Boot into windows.
Run FIXMBR  (this will overwrite grub and set windows as primary boot)
NOW pull your ubuntu drive.

---

### Post by localzuk on 2006-03-22
Do not do this. I am afraid the parent has it wrong - there will be issues with your Ubuntu disk - as it appears you have it on the secondary disk with the bootloader installed into the mbr of the windows (1st) disk.

All you need do is put the windows xp disk in and enter rescue mode. Type fixboot and fixmbr and reboot. That should fix the issue.

If you follow the parents instructions you will have to re-install all your applications - which is unnecessary.

EDIT: Wrong post

---

### Post by Ramses de Norre on 2006-03-22
What I think of now: did you check the master/slave jumpers?

---

### Post by NewWithoutClue on 2006-03-22
It's my suggestion that if people know something is wrong/missing from another persons reply to someones question.. you should A) Post why one option was wrong or what was missing, or B) Wait for the person who asked the question to reply. I only say this because i can see how people may get mixed up/confused.

p01n7

---

### Post by kenweill on 2006-03-22
[QUOTE=NewWithoutClue]It's my suggestion that if people know something is wrong/missing from another persons reply to someones question.. you should A) Post why one option was wrong or what was missing, or B) Wait for the person who asked the question to reply. I only say this because i can see how people may get mixed up/confused.

p01n7[/QUOTE]

Right.
Its better to find alternatives before actually doing it.
Different person has different solutions and views of a particular problem.
Don't do it right away. Read more.

---

### Post by localzuk on 2006-03-22
The problem is that a lot of people will be posting at the same time - so you might have 5 people posting the same thing or slightly different without each of them knowing that.

---

### Post by NewWithoutClue on 2006-03-22
[QUOTE=localzuk]The problem is that a lot of people will be posting at the same time - so you might have 5 people posting the same thing or slightly different without each of them knowing that.[/QUOTE]

Agreed, but i also get the feeling people just want to toss in their two cents without thinking about the person who is going to heed it.

p01n7

---

