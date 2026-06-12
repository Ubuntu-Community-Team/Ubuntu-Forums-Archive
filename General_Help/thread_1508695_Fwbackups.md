---
title: "Fwbackups"
date: 2010-06-13
forum: General Help
---

### Post by hhoyt on 2010-06-13
Anyone successfully using FWBACKUPS ?

Since moving from windows, I have been really frustrated that there is no functional equivalent to True Image or Macrium Reflect type backup. I am relatively new to Linux but suspecting this is the downside to FOSS.

fwbackups seems to come closest re: function & ease of use.

So I backed up my six distros w/o a hitch and proceeded to test whether restore really worked.
Formatted my linux mint 9 partition and proceeded to restore it.

No Joy. Fwbackups complained the source destination was not r/w. But it was mounted r/w. Wrote that off to maybe not having been root when I did the fwbackups ?
Well, my fsarchiver backup did not restore. Again perhaps disk geometry ?
Clonezilla put me back in biz in less than 3 min but needed to reinstall fwbackups (1.43.3rc4 w/ stdoutfd patch)-- all local files, the b/u is to my big USB hard drive.

I then built a backup set on my mepis 8.5 partiton, which ran with no errors.
My next problem is that I cannot get the INCREMENTAL checkbox to take. I can select it ok ("backups are incremental"). Select "APPLY" say 'yes' to "OVERWRITE ?" and exit the panel.

Problem being that if I go right back into edit of the backup set and choose "options simple", the box is again un-checked. 
Is it just me ? 
If I select "help", darn if I can even find a write up on Incremental. Suspecting the help dialog might have been written earlier as the panels are not a good match to what 1.43.3rc4 presents.

Suppose I need to stick with Clonezilla but the idea was to exploit the incremental ability of fwbackups.

TIA, Howard

---

### Post by bobcollard on 2010-06-13
I use sbackup.  It's incremental and as long as you point to the original file after reinstalling both system and sbackup you can find anything you need.  I set it for daily backup with a full backup every seven days, to each his own.  Clonezilla takes up too much space for my needs.  I never tried fwbackups.

---

### Post by Zill on 2010-06-13
> **bobcollard said:**
> I use sbackup.  It's incremental and as long as you point to the original file after reinstalling both system and sbackup you can find anything you need...
+1 for [sbackup]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite"). 

Just note that the default backup destination of /var/backup may not help you much if your HDD crashes!  I suggest you ensure your backups are *always* saved somewhere else, such as a different HDD or optical media.

---

### Post by hhoyt on 2010-06-13
Ok, thanks for the replies.
I spent today fooling with Sbackup.

Works great except when I format the b/u partition, restore does not give me a bootable partion.

Gonna cut my losses and just use Clonezilla of everything for SYSTEM recovery and weekly sbackup for DATA recovery.

Thanks, Howard

---

### Post by hhoyt on 2010-06-14
A followup on this-

I suspect that fwbackups has disabled the incremental switch ?
(There is a note that it only works on *nix systems)
Having said that, Fwbackups RESETS the "# OF OLD BACKUPS TO KEEP" to zero. This effectively TURNS OFF incremental.
That is to say, checking incremental does the opposite of what you want.

When I set # of backups back to 4, incremental started working.

I'm going to stay with fwbackups. Have sbackup on my system but i prefer the granularity of fwbackups. More importantly--
Fwbackups KEEPS A LOG.

IMO, folks should consider a bare metal backup, such as clonezilla, to removable storage that can be kept against the possibility of catastrophic failure.
You can always follow the bare metal restore with your rsync variant data backup.

Howard

---

### Post by firewing1 on 2010-06-22
Hi Howard,

I'm sorry to hear that you're having trouble with fwbackups - I'm currently working on the code for 1.43.3rc5 (what I'm hoping will be the last release candidate before 1.43.3 final) so I'd be happy to wait a few more days and get this fix committed as well.

Regarding the permissions problem, fwbackups checks if the user running the backup has permissions to the destination so you'll either need to create a folder in your mounted filesystem that your user has permissions to, or run the backup as the root user (not recommended for user files).

In one-time backup mode, fwbackups does the backup only once so naturally the incremental option is disabled, but in set backup incremental mode should be available. Unfortunately because rsync updates the directory in-place, fwbackups must do the same (old backups = 0). If you need to keep snapshot archives of the older backups, then incremental mode will be disabled. This is something I'm working on for the next major release (1.44.0) where the rewrite into C++ and use of Box Backup as an engine should resolve this problem and enable encrypted backups as well!

---

### Post by alexeix on 2010-07-20
I thought that fwbackups could be used to backup an entire image of a PC, but I don't see that as an option.

The fwbackups web site states that it can..."backup the entire computer: Create archives images of so that the entire operating system, documents and applications are safe".

Can anyone advise how this can be done?

I'd like to use just one backup application, so it seems that fwbackups should meet my needs.

Note that I also checked the online user guide, but didn't find any relevant information.
Thanks.

---

### Post by alexeix on 2010-07-21
Any feedback on this?  It seems like not many people use Fwbackups.

---

### Post by Zill on 2010-07-22
alexeix:  Do you *really* want to backup the "entire computer"?  As it is so quick to reinstall a Linux OS and restore the latest data backups I see no need to combine the OS with the data in the backup set.

However, I would have thought that if you selected root (/) as the source directory then everything under that would be backed up.  ie. the "entire computer".  Not sure what you would get if you had a dual-boot system with Windows lurking there as well as Linux though - I haven't been near Windows in years. ;-)

---

### Post by alexeix on 2010-07-22
Well, that's a fair question, but I do have a reason for asking.

Some applications seem to need a fair amount of messing about to install and/or get them working, e.g. Docky, Skype, latest Firefox versions, Handbrake, Bluetooth, my Netgear WPN111 wifi adapter, ClamAV, etc., not to mention my amended desktop appearance.

I'm sure that not eveyone has experienced issues with all of the above, but I have from time to time.

I suppose I could get by without a total image of my installation, it's just that it would be nice and since it says Fwbackups can do it, I thought I'd ask.

I may well try your suggestion for backing up everything from root, to see if it works.

---

### Post by bobcollard on 2010-07-22
Sounds like you want something like Back In Time, but, be aware that unless you keep some sort of daily backup your current personal data will be lost.

---

### Post by alexeix on 2010-07-22
That looks like a good option; many thanks!

It never ceases to amaze me, when someone pops up with an application like this, which I haven't found during my searches. :D

---

### Post by bobcollard on 2010-07-22
> **alexeix said:**
> That looks like a good option; many thanks!

It never ceases to amaze me, when someone pops up with an application like this, which I haven't found during my searches. :D
Research is a matter of how much time you have.  I read seven different forums each day and keep track of many different new applications in links like  [http://distrowatch.com/](http://distrowatch.com/)  Of course, I spend all day in front of my computer, drives my wife nuts, but, it is what I like to do.  Hope this works out for you.

---

