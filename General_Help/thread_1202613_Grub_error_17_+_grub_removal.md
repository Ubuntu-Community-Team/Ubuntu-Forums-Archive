---
title: "Grub error 17 + grub removal?"
date: 2009-07-02
forum: General Help
---

### Post by lernatix on 2009-07-02
continued from this thread : [http://ubuntuforums.org/showthread.php?t=1190417&page=3]("http://ubuntuforums.org/showthread.php?t=1190417&page=3")

*Backstory...

OK so I have an XP machine which I dual boot to Ubuntu.
Ubuntu was installed on the second hard drive. (D: )

I decided to remove Ubuntu from the PC as I run linux on my PS3.

I formatted my second drive (D: ) to NTFS and the next time 
I switched my PC on I got the "Grub error 17" message.

I managed to sort of fix this by using a windows XP CD's 
repair option.  Specifically the commands "fixboot" and 
"fixmbr". Windows would then load normally.

Now when I switch the PC on, I still get a grub menu asking
if I want to boot Windows or Ubuntu, which seemed odd as I 
had formatted the D: drive. 

*OK back to the present.

> ronaldprettyman writes...

Once your in XP, super+r>>cmd>>"BOOTCFG /rebuild">>reboot see if that fixed then once your back in xp, right click my computer and select manage. Go down to disk/partitions and check to see that you only have one, or that all of them are mounted in windows(have a letter association).

I don't know how you formated the ubuntu installation, but I'm fairly certain that Grub looks for the menu.lst on the /boot partition every time it boots.

OK Ron, I sort of skipped to the check partitions part of your 
instructions on a whim.  There is an unknown but healthy  extended 
partition of <>900mb on disk1 (D: ) so I assume 
that the drive was formatted AROUND Ubuntu...?

Just to clarify your first instruction.
> Once your in XP, super+r>>cmd>>"BOOTCFG /rebuild">>reboot
Are we talking about using the XP CD again here?

---

