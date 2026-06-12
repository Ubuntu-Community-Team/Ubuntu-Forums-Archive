---
title: "Disabling UUID in GRUB2 and fstab and resume and ?"
date: 2010-11-25
forum: General Help
---

### Post by carlturney on 2010-11-25
[FONT=Courier 10 Pitch][SIZE=3]For reasons long and unique, I want to disable UUID in my recent Ubuntu 10.4 install, and use the old fashioned /dev/sda1 /dev/sdb3 etc. method[/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=3]I had this &#8220;all fixed&#8221; under GRUB (pre-2) on Ubuntu 8.04 and it has served well and bug free for years. (Warning: I use old stable hardware - others may have disasters.)[/SIZE][/FONT]

[FONT=Courier 10 Pitch][SIZE=3]But with GRUB2, the task seems more complicated. I've spent hours reading up web forums on the subject, but want your second opinions before making changes.  (This helps me make the backups I haven't done since the fresh install 2 weeks ago.)
[/SIZE][/FONT]
[FONT=Courier 10 Pitch][SIZE=3]Is the following process complete, necessary, and accurate...
[/SIZE][/FONT] 
 [FONT=Courier 10 Pitch][SIZE=3]Edit the file  /etc/default/grub  to remove the # in the line...  [/SIZE][/FONT] 
 [FONT=Courier 10 Pitch][SIZE=3]#GRUB_DISABLE_LINUX_UUID=&#8221;true&#8221;[/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=3]... making sure to add the two &#8220; if missing.[/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=3]Copy nearly the entire  /boot/grub/grub.cfg  file[/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=3]into  /etc/grub.d/40_custom  and then...[/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=3]Comment out every line that says...[/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=3]search --no-floppy --fs-uuid --set (etc.) [/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=3]Change every line that says...[/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=3]linux  /boot/vmlinuz-2.x.yy-zz-generic root=UUID=(etc.)[/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=3]into...[/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=3]linux  /boot/vmlinuz-2.x.yy-zz-generic root=/dev/sda1[/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=3]Edit  /etc/fstab  and change every instance of UUID=(etc.)[/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=3]to the appropriate drive and partition e.g. /dev/sda1[/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=3]edit  /etc/initramfs-tools/conf.d/resume  and change RESUME=UUID=(etc.)[/SIZE][/FONT]
 [FONT=Courier 10 Pitch][SIZE=3]into RESUME=/dev/sda1[/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=3]Run update-grub[/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=3]Do all the above, every time I do a kernel upgrade.  [/SIZE][/FONT] 
 
[FONT=Courier 10 Pitch][SIZE=3](Is it important to do all the above before or after rebooting for an upgrade?)[/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=3]Am I correct, succinct, and complete in the above process?  Any mistakes?  Any omissions?  Any misunderstandings?[/SIZE][/FONT]
 
 [FONT=Courier 10 Pitch][SIZE=3]Thanks very much.  Carl Turney  New Zealand[/SIZE][/FONT]

---

### Post by wilee-nilee on 2010-11-25
This mod has a plethora of tutorials, they are in their signature, I think what you looking for will be there, actually I know so, click on about me on their home page.
[http://ubuntuforums.org/member.php?u=223945](http://ubuntuforums.org/member.php?u=223945)

I can't answer your questions, the only modifications I make are removing the mem check, in the grub menu, so hopefully this person will see you or you will get some answers.;)

---

### Post by carlturney on 2010-11-25
Hi wilee-nilee,

Thanks for that lead.  Unfortunately, I've read through all his tutorials there and none of them quite answer my initial questions on this thread.

(In fact, some of the steps that I proposed I learned from his tutes, before even starting this thread.)

Hope someone with lots of experience with & understanding of GRUB2 and fstab and resume and "whatever else may need to be altered" posts to this thread with their insights.  I don't like going all these days, and putting in all these changes, without getting on with my backup system.

Cheers, Carl, New Zealand

---

### Post by drs305 on 2010-11-25
**/etc/default/grub**
Uncomment:
***[COLOR="DarkRed"]#[/COLOR]**GRUB_DISABLE_LINUX_UUID=true*, as you have proposed.

**/usr/lib/grub/grub-mkconfig_lib**
If you would prefer to use a 'live' grub.cfg rather than a 40_custom copy, instead of removing the 'search' lines from 40_custom, you could also  remove the 'search' lines automatically by removing them from /usr/lib/grub/grub-mkconfig_lib. This would eliminate having to manually edit 40_custom when there is a kernel update. 

Comment this section to remove the 'search' lines from appearing in grub.cfg
> 
**[COLOR="DarkRed"]#[/COLOR]** if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
**[COLOR="DarkRed"]#[/COLOR]**    echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
**[COLOR="DarkRed"]#[/COLOR]**  fi


With the two changes above, I don't think you will have an UUIDs in the grub menu files. Disclaimer: I don't have a Windows or Mac OS on my machine to see the results for those parts of 30_os-prober so I don't know how they are presented. You can always disable 30_os-prober and place them in 40_custom if the OS's wouldn't be updated often. Use "GRUB_DISABLE_OS_PROBER=true" in /etc/default/grub rather than make the file unexecutable.

Change /etc/fstab, as you noted.

**/etc/initramfs-tools/conf.d/resume**
As you said.

If your system supports them, have you considered using LABELS instead of UUIDs? Grub2 can use partition labels, and I find them much easier to recognize than eitehr device names or UUIDs.

---

