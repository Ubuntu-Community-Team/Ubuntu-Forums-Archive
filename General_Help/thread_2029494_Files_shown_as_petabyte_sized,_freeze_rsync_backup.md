---
title: "Files shown as petabyte sized, freeze rsync backup"
date: 2012-07-19
forum: General Help
---

### Post by cephalopods on 2012-07-19
The backstory: I recently setup an old desktop as an ssh server with the intent of primarily using it for remote backup. Setup was fine, and I have ssh and vnc running reliably. When I run rsync from my laptop, it starts out fine as well - I get "sending incremental file list," then it starts listing of directories and file names. Satisfied that it was running well, I left it overnight. In the morning, I found it stuck on an xml file (in the virtualbox folder, I think). Curious as to why this would happen, I looked at the properties for that file, and it was listed at 52.6 PB. I moved this file individually to another drive, and tried to backup again. I tried this several times, and every time it hangs on a file that shows up as being in the multi-petabyte range. I don't remember which files this happened with exactly, but I could not discern a pattern. The ones I do remember were the xml file in the virtualbox folder, and random 6 character alphanumeric in the home directory, and most recently a file under play-on-linux. 

The laptop running the backup is a lenovo y560 running 11.04 (can't upgrade, need it for work). Specifically, the command I'm using is : rsync -avz -e "ssh -p xxxx" /home/xxxxx [email]xxxx@xxxxxxx.org[/email]:~/Backup/Lapt\
op-backup/

I'm perplexed, and would really like to be able to get this backup process going. Any help is greatly appreciated!

---

### Post by papibe on 2012-07-20
Hi cephalopods. Welcome to the forums ):P

rsyncing virtual disks has been known to have its issues.

I would start by excluding the virtualbox directory in your regular rsync backup script by adding an exclude rule:
```
--exclude .Virtualbox
```
Then it would be necessary to design another rsync command with special options to take care of the virtual disks.

Are your disks fixed-size, or dynamically allocated?

Let us know how it goes.
Regards.

---

### Post by Sandro Hawke on 2012-07-21
FWIW, I've been struggling with the same problem, and it's all over my filesystem, so I can't just exclude it.      It's usually machine-generated filenames, like on just now:

```

.local/share/recently-used.xbel.IAWEYV
 15132852224   0%   24.11MB/s 357334:23:02 

```

I manage by checking on my rsync after a while, seeing it's hung up, and deleting the given file.  it's never a file that matters.

I'm using   --max-size=10G  but that's not helping.    The petabyte files are not found by 'find . -size +1G -ls'.

I'm also using 11.04 and not upgrading because of unity.   Once I get a proper backup done, I'm planning to try another distro.

fsck doesn't find any problems.

---

### Post by kpi on 2012-07-22
I have had the same problem for some while now when doing backups to USB external drives. Most of the time I manage to get along with excludes. My current exclude list looks like this "--exclude '.config' --exclude '.cache' --exclude '.thumbnails' --exclude 'sessionstore*.js'".

I also did some research a while ago and it seems that in my case it could be related to ecryptfs corrupting files with size 0. I found out that the affected files all actually have a filesize of 0. At least that's what ls -l says _before_ the rsync command is issued and rsync actually causes the file to afterwards show up with ls -l in the petabyte range (which is more than the actual filesystem total). Find -size does not find these files. I can get around deleting the files and doing rsync again.

I am using Ubuntu 10.04 LTS with ecryptfs.

I would also appreciate a way of getting rid of this behavior in a more efficient way. Question to the others affected: Do you see Input/Output errors from rsync? Are you using disk encryption? What does your dmesg say?

Probably related bugs [https://bugs.launchpad.net/ecryptfs/+bug/911507](https://bugs.launchpad.net/ecryptfs/+bug/911507) and [https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/957843](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/957843)

---

### Post by cephalopods on 2012-07-23
I had initially tried excluding the virtualbox directory, but when I did so it just caused another file to display the same properties. (For reference, I have dynamically allocated virtual drives, but it doesn't seem like that's the root of the problem). 

kpi, it's looking like my problem has the same cause as yours. When I take a look at dmesg, I am getting I/O errors, and I do have encryption. It does look like the 0 size files are the problem. I added --min-size=1 to the rsync command, and it's been happily running for about 4 hours, far past the point it was getting stuck before. I have my fingers crossed that it continues to work properly, but it looks like that is a decent workaround. 

I've attached a section of my dmesg output from before I excluded the 0 size files, in the hopes that it might help someone get a better idea of the underlying problem.

---

