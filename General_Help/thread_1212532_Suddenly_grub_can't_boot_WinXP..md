---
title: "Suddenly grub can't boot WinXP."
date: 2009-07-13
forum: General Help
---

### Post by dluzius on 2009-07-13
[SIZE="4"]**I installed Ubuntu and Grub about 4 or 5 weeks ago, and everything worked just fine. I had a working dual boot system, and no problems. But this morning when I turned on my PC, a 3 1/2 year old Gateway, I told grub to boot WXP, but it couldn't. Instead I got a message at the bottom of the screen, which said it was preparing system recovery options, the the screen went from black to blue and gave me an error # of 0xc000003a, and it shut down. I've tried several times since then, and although I can boot Ubuntu, it's still a no go with wxp. I've searched the Web, and tried hitting the F8 key , but it won't even go into safe mode. I really need help.    Dave**[/SIZE]

---

### Post by AdamShumpisxXx on 2009-07-13
It seems you've found the infamous BSOD that Windows is so famous for. You're particular error is a system restore filter error. Your F8 key won't be able to save you now. What I would suggest is using your original Windows XP disc to start up a recovery console and try to restore Windows. If not, you have a smoked Windows partition on your hands and you'll have to re-do it.

Also, please restore your font to the normal settings as it's annoying to read.

---

### Post by dluzius on 2009-07-13
Sorry about the font size, pls excuse my ignorance in this matter. I never received a WXP CD when I purchased the PC from Best Buy, Is there any other suggestion you can give me?    Dave

---

### Post by AdamShumpisxXx on 2009-07-13
Not a legal solution. If you don't have the tools you can't do the job...

If you end up figuring out how to get your legal copy of Windows XP from Best Buy come back. Either that or the recovery dics in which case the solution is specific to your situation and you're just going to have to follow the directions as they are provided with the discs.

Good luck!

---

### Post by lindsay7 on 2009-07-13
This may help you.


Friday, February 21, 2003 at 1:05 pm
Posted by Frank (1 messages posted)

I had the same problem, if your trying to dual boot with Linux it hides your NTFS partition with your Windows XP on it. As part of the boot process chkdsk calls for autochk.exe and because your partition is hidden it can't find it and gives you the error message. You can either use a Linux Boot Disk if you are comfortable with Linux or you can do what I did and use partition magic 8 and boot from the CD run partition magic and unhide you partition. You might have to run the Recovery Console in XP to recreate your MBR and boot sector etc

[Reply or follow-up to this message]
re: Can't get Windows XP to start
Friday, February 28, 2003 at 5:35 pm
Posted by sanlihe (1 messages posted)

The hidden Windows partition is easy to fix. Just run 'grub' from /boot, provided you have installed this partition. type: unhide (hd0,0) If you're not sure the device name required by 'unhide', check /boot/grub/grub.conf Restart and Windows will boot.


On Friday, February 21, 2003 at 1:05 pm, Frank wrote:
>I had the same problem, if your trying to dual boot with Linux it hides your NTFS
>partition with your Windows XP on it.
>As part of the boot process chkdsk calls for autochk.exe and because your partition
>is hidden it can't find it and gives you the error message.
>
>You can either use a Linux Boot Disk if you are comfortable with Linux or you can
>do what I did and use partition magic 8 and boot from the CD run partition magic
>and unhide you partition. You might have to run the Recovery Console in XP to recreate
>your MBR and boot sector etc

---

### Post by AdamShumpisxXx on 2009-07-13
> **lindsay7 said:**
> This may help you.


Friday, February 21, 2003 at 1:05 pm
Posted by Frank (1 messages posted)

I had the same problem, if your trying to dual boot with Linux it hides your NTFS partition with your Windows XP on it. As part of the boot process chkdsk calls for autochk.exe and because your partition is hidden it can't find it and gives you the error message. You can either use a Linux Boot Disk if you are comfortable with Linux or you can do what I did and use partition magic 8 and boot from the CD run partition magic and unhide you partition. You might have to run the Recovery Console in XP to recreate your MBR and boot sector etc

[Reply or follow-up to this message]
re: Can't get Windows XP to start
Friday, February 28, 2003 at 5:35 pm
Posted by sanlihe (1 messages posted)

The hidden Windows partition is easy to fix. Just run 'grub' from /boot, provided you have installed this partition. type: unhide (hd0,0) If you're not sure the device name required by 'unhide', check /boot/grub/grub.conf Restart and Windows will boot.


On Friday, February 21, 2003 at 1:05 pm, Frank wrote:
>I had the same problem, if your trying to dual boot with Linux it hides your NTFS
>partition with your Windows XP on it.
>As part of the boot process chkdsk calls for autochk.exe and because your partition
>is hidden it can't find it and gives you the error message.
>
>You can either use a Linux Boot Disk if you are comfortable with Linux or you can
>do what I did and use partition magic 8 and boot from the CD run partition magic
>and unhide you partition. You might have to run the Recovery Console in XP to recreate
>your MBR and boot sector etc

That doesn't pertain to this situation. The option IS NOT hidden. His Windows partition ITSELF is in a state of disrepair and is BSODing on startup. OP, do not concern yourself with this information.

---

