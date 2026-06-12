---
title: "Permission problems with netatalk 2.2~beta4-0~ppa1 and Apple Lion OS 10.7"
date: 2011-08-13
forum: General Help
---

### Post by jo_mama on 2011-08-13
With Apple OS 10.6.* I was using samba for a network time machine with my natty box (mythbuntu) when 10.7 came out I had to change over to AFP.  I am able to get the machine to do back ups, however when I try to enter the Star Wars screen, the network drive mounts, and nothing happens.  I don't get any errors.  I can go into my Time Machine folder, and I can see Backups.backupdb, I go in there and I see <mymachinesnetworkname>, but when I try to go into that folder I get permission errors.

In terminal on the mac as sudo su - I see...

drwx------  6 root    wheel   264 Aug 13 14:29 Time Machine
drwxr-xr-x  9 root    wheel   374 Aug  2 07:22 Time Machine 1

Inside of Time Machine I see...

drwxr-xr-x@ 2 root  wheel  264 Jul 31 09:23 Network Trash Folder
drwxr-xr-x@ 2 root  wheel  264 Jul 31 09:23 Temporary Items
drwx------@ 8 root  wheel  264 Aug 13 14:31 mymachinesnetworkname.sparsebundle
drwx------  2 root  wheel  264 May 29 14:21 lost+found

...and inside mymachinesnetworkname I see...

-rwx------      1 root  wheel      499 May 19 12:46 Info.bckup
-rwx------      1 root  wheel      499 May 19 12:46 Info.plist
drwx------  30297 root  wheel  1030054 Aug 13 14:03 bands
-rwx------      1 root  wheel      445 Aug 13 14:15 com.apple.TimeMachine.MachineID.bckup
-rwx------      1 root  wheel      445 Aug 13 14:15 com.apple.TimeMachine.MachineID.plist
-rwx------      1 root  wheel        0 May 19 12:46 token

Inside of Time Machine 1 I see...

-rw-r--r--@   1 root  wheel  6148 Aug  2 07:41 .DS_Store
drwx------    5 root  wheel   170 Jul 31 09:46 .Spotlight-V100
d-wx-wx-wt@   2 root  wheel    68 Jul 31 09:45 .Trashes
drwx------  263 root  wheel  8942 Aug 13 14:04 .fseventsd
drwxr-xr-x+   5 root  wheel   170 Jul 31 09:57 Backups.backupdb

...and Inside of Backups.backupdb I see...

drwx------   2 root  wheel       68 Aug  7 13:31 .spotlight_repair
drwx------   2 root  wheel       68 Aug 13 13:01 .spotlight_temp
drwx--x--x@ 39 root  _unknown  1326 Aug 13 13:58 mymachinesnetworkname

...and inside of mymachinesnetworkname I see...

drwxr-xr-x@ 6 root  _unknown  204 Aug  1 19:24 2011-08-01-192413
<same file different time stamp about 20 times>
drwxr-xr-x@ 4 root  _unknown  136 Aug 13 13:58 2011-08-13-135846.inProgress
lrwx--x--x  1 root  _unknown   17 Aug 13 13:01 Latest -> 2011-08-13-130144

Note, I didn't use -a but it showed me the hidden files/directories anyways.

For netatalk  AppleVolumes.default looks like this...

: DEFAULT: options:upriv,usedots,tm dperm:0775 fperm:0660
/path/TimeMachine        "Time Machine"  allow:myusername    options:usedots,upriv,tm

...afpd.conf looks like this...

- -udp -noddp -uamlist uams_randnum.so,uams_dhx.so,uams_dhx2.so -nosavepassword

Anyone idea what I am doing wrong?  Thanks.

---

### Post by dmovad on 2011-08-14
I'd wait for additional answers from more expert forum members but for what it's worth I have a Time Capsule and using the Terminal from my Mac my permissions show:

My Mac OS X user name is the owner and the group is "staff".

Permissions for the sparse bundle backup file are:

drwxrwxrwx

I'd also like to add that since upgrading to Lion and with having an Ubuntu 10.04 Server that I updated to netatalk 2.2-beta-4-0 as well I still couldn't connect to do Time Machine backups.  Prior to upgrading to Lion the Ubuntu box proved to be more reliable than my Time Capsule so I had been using it for about 1 year.  Since Lion I copied my backup from the Ubuntu server to the Time Capsule.  I used it for about a week on the Time Capsule then got an error message that I had to recreate the Time Machine backup.  The bottom line is that I lost that version of my backup and now have a one week old file on the Time Capsule.  I'd like to get back to using the Ubuntu server because ultimately I have more trust in it than the Time Capsule but I'll wait until the dust settles with netatalk.

There also seems to be a "pissing contest" going on between the developers of netatalk and the NAS box makers.  It seems that the final version of netatalk 2.2 is ready but because only one NAS vendor chooses to financially support the netatalk project (I think it may be Dlink but not sure) the developers are holding back.  We who test and often make financial contributions to GPL licensed projects suffer until releases are made.  Few open source projects are skilled at monitizing their businesses except perhaps Red Hat.  So we wait...

Good luck...

---

### Post by jo_mama on 2011-08-14
In Finder I have just 1 item showing Time Machine.  But in terminal (actually iTerm) in /Volumes I have Time Machine, and Time Machine 1.  What do you have in /Volumes?

Everything is root:wheel, or unknown:unknown,admin,wheel, or a mix.  What do you have that is <yourusername>:staff?

What version of netatalk are you running?

What does your afpd.conf and AppleVolumes.default look like? (if you answer only thing, answer this please)

I'm pretty sure the problem is I don't have netatalk set up correctly.  I've erased my sparsebundle and, rsync -aE it twice.  I'm using the same sparsebundle file that I created under 10.6, I haven't remade that under 10.7 and to be honest, backing up 250 gigs over a wireless connection takes WAY to long.  It's a last resort thing.

One thing I forgot to mention, when 10.7 first came up and I got afp working I could get to StarWars, but I didn't trust that back up, so I wiped/redid the sparsebundle.  Since then, I have not been able to get back to the StarWars screen.  Thanks for your help.

---

