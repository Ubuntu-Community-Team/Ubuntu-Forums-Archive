---
title: "boot_info_script strange output"
date: 2011-08-06
forum: General Help
---

### Post by JASONFUSARO on 2011-08-06
I have no idea on how to track this problem down by googling it.

I ran boot_info_script and got some strange output that I need help with.

I thought the characters would show up with a paste but they did not so take a look at the screenshot.

I am hoping someone knows what it is and why this occured and can point me to a solution.

```

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab


```


Thank you

---

### Post by oldfred on 2011-08-07
If you run it from Arch what do you get?

Did you install with a different language or character set?

---

### Post by JASONFUSARO on 2011-08-07
I can login as root but not my user, it won't access /.

wait I will reboot and give the exact message, I have not tried for a couple of days.



**EDIT***

failed to execute login command

I checked the permissions and they are ok

I used english, root works fine.

although the user home is on another partition and I selected that option on the install, I checked fstab and such everything appears ok, I even messed around creating other users to see effect and the same thing happens?

I am at a loss for a solution?

**EDIT***

Thanks for responding

---

### Post by AlphaLexman on 2011-08-07
The 'domino' looking characters are 'escape codes' and the '001B' on the domino char is the escape code for the actual  'Esc' keystroke.

---

### Post by JASONFUSARO on 2011-08-07
> **AlphaLexman said:**
> The 'domino' looking characters are 'escape codes' and the '001B' on the domino char is the escape code for the actual  'Esc' keystroke.


The question may now be is boot_info_script.sh adding them ie. 'Esc' and if so is it because it is getting that information from somewhere which is the root cause of the login problem or is the login problem rooted in something else?

---

### Post by oldfred on 2011-08-07
The boot script is just trying to parse partitions to discover what operating system is there. I just must be picking up extra characters from where ever it is looking. I do not know script enough to tell exactly where it looks for that info.

---

### Post by AlphaLexman on 2011-08-07
Is the 'boot_info_script.sh' arch linux specific? Can you post it's contents?

**EDIT:** I think I found it, via this [thread]("http://archlinux.2023198.n4.nabble.com/Why-etc-issue-starts-with-invisible-chars-td2044979.html"). Post the output of...
```
cat /etc/issue
```

---

### Post by JASONFUSARO on 2011-08-07
> **AlphaLexman said:**
> Is the 'boot_info_script.sh' arch linux specific? Can you post it's contents?

**EDIT:** I think I found it, via this [thread]("http://archlinux.2023198.n4.nabble.com/Why-etc-issue-starts-with-invisible-chars-td2044979.html"). Post the output of...
```
cat /etc/issue
```



I am using the boot_info_script.sh that I use in Ubuntu


I localized the script that is doing the output, but I am not currently proficient at analyzing script, have not delved into that yet.

this is what is outputting the appropriate lines

```

echo "    Operating System:  "${OS} | fold -s -w 55 | sed -e '2~1s/.*/                       &/' >> "${Log}"

*** This is from me not in the actual script  **********************

fold command --> -s means break at spaces  -w means width = 55 as opposed to 80

sed (tream editor)   -e (-e script, --expression=script add the script to the commands to be executed)

which is --->    '2~1s/.*/                       &/' >> "${Log}"

********************************************************


```




**EDIT #2***


It's also found in this area



```



	if [[ x"${BFI}" != x'' ]] ; then
	   printf "    Boot file info:     " >> "${Log}";
	   printf "${BFI}\n" | fold -s -w 55 | sed -e '/^-------------------------$/ d' -e '2~1s/.*/                       &/' >> "${Log}";
	fi

	[COLOR="Red"]echo "    Operating System:  "${OS} | fold -s -w 55 | sed -e '2~1s/.*/                       &/' >> "${Log}"[/COLOR]
	printf "    Boot files:        " >> "${Log}";
	echo ${BootFiles} | fold -s -w 55 | sed -e '2~1s/.*/                       &/' >> "${Log}";



[COLOR="#ff0000"]	# If partition was mounted by the script.[/COLOR]
	if [ x"${CheckMount}" = x'' ] ; then
	   umount "${mountname}" || umount -l "${mountname}";          
	fi

     # If partition failed to mount.
     else
	printf "    Mounting failed:   " >> "${Log}";  
	cat ${Mount_Error} >> "${Log}"; 
     fi		# End of Mounting "if then else".
  fi	  	# End of Partition Type "if then else".

  echo >> "${Log}";



```


Which might mean it was added by the scipt, that section is not the whole thing just trying to figure out if the script generates non found info?

---

### Post by AlphaLexman on 2011-08-07
Try this, change...
> **JASONFUSARO said:**
> ```
echo [COLOR="Red"]"[/COLOR]    Operating System:  [COLOR="red"]"[/COLOR]${OS} | fold -s -w 55 | sed -e '2~1s/.*/ &/' >> "${Log}"
```
to...
```
echo [COLOR="Red"]-e "[/COLOR]    Operating System:  [COLOR="red"]${OS}"[/COLOR] | fold -s -w 55 | sed -e '2~1s/.*/ &/' >> "${Log}"
```
**NOTE:** The location of the double quotes and the addition of the '-e'
Save the script and run it again, and post any errors or if you see any escape code dominos.

---

### Post by JASONFUSARO on 2011-08-07
> **AlphaLexman said:**
> Try this, change...

to...
```
echo [COLOR="Red"]-e "[/COLOR]    Operating System:  [COLOR="red"]${OS}"[/COLOR] | fold -s -w 55 | sed -e '2~1s/.*/ &/' >> "${Log}"
```
**NOTE:** The location of the double quotes and the addition of the '-e'
Save the script and run it again, and post any errors or if you see any escape code dominos.



I am running Mint right now


I should have incuded the other lines initially here they are:

```


                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /menu.lst /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 274213392 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 11 Katya 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 359492032 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 11.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /core.img 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J
 Arch Linux  () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J
 Arch Linux  () ()
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda9 and looks at sector 460557664 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 9 for (,msdos9)/boot/grub.
    Operating System:  Ubuntu 10.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
 This is .() 
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/grub/grub.conf /etc/fstab

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda11 and looks at sector 586193008 of the same 
                       hard drive for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #13 for /boot/grub/menu.lst.
    Operating System:  Lucid Puppy Linux
 Linux 2.6.33.2 [i686 arch]
    Boot files:        /etc/fstab

sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda14: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Slackware 13.37.0
    Boot files:        /etc/fstab /etc/lilo.conf

sda15: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda15 and looks at sector 754347968 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 15 for /boot/grub2.
    Operating System:  Fusion Linux release 14 
 (Thorium)
 Kernel on an ()
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img 
                       /boot/grub2/core.img

sda16: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

```




This is the run with the replacement:

```


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot files:        /menu.lst /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 274213392 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Boot files:        /boot/grub/grub.cfg /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda6 
                       and looks at sector 359492032 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Boot files:        /boot/grub/grub.cfg /etc/fstab /core.img 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda8: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda9 and looks at sector 460557664 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 9 for (,msdos9)/boot/grub.
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/grub/grub.conf /etc/fstab

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda11 and looks at sector 586193008 of the same 
                       hard drive for the stage2 file.  A stage2 file is at 
                       this location on /dev/sda.  Stage2 looks on partition 
                       #13 for /boot/grub/menu.lst.
    Boot files:        /etc/fstab

sda12: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot files:        

sda14: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Boot files:        /etc/fstab /etc/lilo.conf

sda15: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sda15 and looks at sector 754347968 of the same hard 
                       drive for core.img. core.img is at this location and 
                       looks in partition 15 for /boot/grub2.
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img 
                       /boot/grub2/core.img

sda16: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Boot files:        

============================ Drive/Partition Info: =============================


```


there is no ouput?


let me double check if the search and replace worked correctly


this is what is there now

```
	echo -e "    Operating System:  ${OS}" | fold -s -w 55 | sed -e '2~1s/.*/ &/' >> "${Log}" '2~1s/.*/                       &/' >> "${Log}"
```

argh!!  mistake let me rerun it



EDIT**************

It now contains the corrected run ie.   the above code section has the correction in it

---

### Post by AlphaLexman on 2011-08-07
WOW! That's a lot of partitions and distros!

If you read the thread link in Post #7 you should have noticed that the escape characters are not necessarily a bug, but a design flaw, and that a better script will test for the existence of '/etc/arch-release'. However, this test method is not distro-independent, and really is only required on Arch Linux, so it is not really compliant with other distros.

In conclusion, I would suggest that you just live with the strange, funny, escape codes, or remove Arch Linux from your many installed distros (although extreme for a text error)!!!!!

---

### Post by JASONFUSARO on 2011-08-07
> **AlphaLexman said:**
> , I would suggest that you just live with the strange, funny, escape codes, or remove Arch Linux from your many installed distros (although extreme for a text error)!!!!!


Do you mean extreme with regards to the post for a text error?

If so, the post is trying to determine if that is the reason for not being able to login?

That they were somehow the reason behind the login problem, but since I now know that they are not responsible I have to look elsewhere.

Thanks

---

### Post by AlphaLexman on 2011-08-07
> **JASONFUSARO said:**
> Do you mean extreme with regards to the post for a text error?

If so, the post is trying to determine if that is the reason for not being able to login?

That they were somehow the reason behind the login problem, but since I now know that they are not responsible I have to look elsewhere.

Thanks
Sorry, I actually forgot you couldn't login, I got confused with the ubuntu script, and being on mint, as well as the other distros...

I would still suggest some of the suggestions in the thread in Post #7, such as deleting '/etc/issue' and rebooting.

---

### Post by JASONFUSARO on 2011-08-07
> **AlphaLexman said:**
> Sorry, I actually forgot you couldn't login, I got confused with the ubuntu script, and being on mint, as well as the other distros...

I would still suggest some of the suggestions in the thread in Post #7, such as deleting '/etc/issue' and rebooting.


this is from post #7   /etc/issue

Arch Linux \r (\n) (\l)

and here in 

Linux Mint 11 Katya \n \l


I had to logout and boot up ArchBang and enter as root

but there is also a networking problem there   Error 105 (net::ERR_NAME_NOT_RESOLVED): The server could not be found.

can't run my browser???

but that is another issue


What actualy is /etc/issue for? I read the link but may have missed something in it, thought it was just the position for naming the distro so it could be recognized.

I will try it, delete /etc/issue in ArchBang and reboot thanks for your time.


As for all the distros it allows a greater number of ways to get back in and try and fix problems, the downside is there ends up being a greater number of problems! But I enjoy the adventure of learning.

---

### Post by JASONFUSARO on 2011-08-07
That changed nothing.


I will call this thread solved, since those characters are not the cause of the login issue, just have not seen them in any other runs. Thanks for the link in #7 which explains why they are there.

Thank you for your time, I hope I didn,t waste it


EDIT****


And you are correct I should have added that in the first post which I was in error of doing, I appologize.

---

