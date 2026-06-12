---
title: "rsync Input/output error ... Source drive failure"
date: 2010-01-02
forum: General Help
---

### Post by gilch on 2010-01-02
I have a problem but I do not know with what. Should I get rid of my 2TB drive or my 1TB drive or both?

I used rsync to backup my 1TB drive to an external WD 2TB drive: it worked for many many hours, but got some Input/output error (5) on about a dozen or so directories. It says that it is a source drive failure.

I tried deleting an offending directory in the source drive, and it still didn't work. I have tried deleting the directory in the backup drive, but it says I cannot delete the directory because it is not empty (although I cannot see any file in it).

Do I send my 2TB drive (brand new) back to the supplier? Are the directories in the source drive really defective? Can they be repaired? Do I have to replace that drive?

I have no idea what to do here.

Gilles

---

### Post by geoff123 on 2010-01-02
have you tried checking the permissions and ownership of the files and directory?

This can be done using the file manager or in a terminal.  Try changing them as root using sudo if needed.  
See.. 
[http://linux.about.com/od/itl_guide/a/gdeitl31t00.htm](http://linux.about.com/od/itl_guide/a/gdeitl31t00.htm)
or many other guides by using google.

Also, what kind of file systems are you using?

---

### Post by gilch on 2010-01-02
Both drives are of type fuseblk (I understand that means NTFS). Which permissions should the files have?
Gilles

---

### Post by gilch on 2010-01-02
I found out (through ls -l) that the directories involved have the same permissions as the other ones around:
drwxrwxrwx 1 root root

On the specific file on which rsync got its first error, I could not get any answer: after the ls -l command it said: 
ls: cannot access /...(filename)

This is a series of files with extension .001 .002 .003 .004 .005 etc.
The ls command worked fine on files .001 to .004 but didn't work on .005 nor the files FOLLOWING that .005 file.

On files .001 .002 ... it gave permission as -rwxrwxrwx 1 root root

Very confusing for a 'pure user' (not a maker) like me.

Gilles

---

### Post by geoff123 on 2010-01-02
You should be able to do a "ls -l" within the directory and look at all the files including .001, .005 etc .  Do the permissions look any different?  

Can you access the file using "sudo ls -l FILENAME"?

I have seen issues with rsync in the past where it doesn't like certain files being transferred between different filesystems like ext3 to ntfs, etc.  But I think my most common problem was with really long paths-filenames.  

Also maybe if you told us rsync command that might help also?

---

### Post by gilch on 2010-01-03
Both drives are NTFS.
No, I cannot access the said file using sudo ls -l (file) - 'cannot access'
Here is the rsync command I was using:
rsync -av /home/gilles/files /media/"My Book" --delete

As I said it worked for most of the 1 TB drive(800+gb), except for those couple of dozens instances.

Thanks for looking into this.
Now I am questionning whether using rsync is the right solution, I see others are using dd.

Gilles

---

### Post by SecretCode on 2010-01-03
I've found the -a option can't be fully applied on ntfs. I just use -t (in fact I use -Pitr: -P for progress reporting, -i for itemising changes, -t preserves modification times and -r recurses into directories).

---

### Post by geoff123 on 2010-01-03
Not sure how much else I can help.  Drive is probably not the issue and my **guess** is that it is related to permissions.

A couple suggestions and thoughts:

-how about running the same rsync command again and then post some examples of the exact error message. 

-Maybe you could plug it into a windows machine to see if it gives you any clues as to what the problem it or use it to copy whatever the problem file is. 

-read up on linux permissions/ownership and look around as root and see if you can find the problem. some key commands to look at are chmod and chown.   For example you could "sudo chown gilles:gilles /home/gilles/files/PROBLEMDIRECTORY"  and "sudo chmod -R a+rwx /home/gilles/files/PROBLEMDIRECTORY"  and also on your My Book in the right location.  [I didn't test those commands so you may want to do "man chmod" before you try this].  Sorry to have to dig into the terminal stuff, but I find it easier to describe in situations like this. 

-Why are you using NTFS so much in Linux?  I know it works, but it can be hard to figure out weird stuff like this. Do you really need it to be NTFS?

---

### Post by geoff123 on 2010-01-03
A few more thoughts.

What happens if you unplug the new external drive and then plug it back in.  Then run the rsync again?  Is it repeatable on the same files/directories?  Maybe even after a reboot?

---

### Post by gilch on 2010-01-03
Could it help to check if there is any problem with the drive itself? Somewhere else I saw some suggestion to check drive with the following:
chkdsk drive /r
?

Gilles

---

### Post by geoff123 on 2010-01-03
Yes - Checking the disk from windows is probably a good idea also.

---

### Post by gilch on 2010-01-03
To Geoff123:
Re NTFS. Before I started this thread... I didn't know I was using NTFS. I thought they were all Linux type. I don't know if I want to change it, because I want to transfer my linux system from the small drive it is on to a 1TB drive so that I can install win7 as well on that drive.  Otherwise I have no preference for NTFS.

Re Disconnecting the drive. I tried that and it didnt help.

Gilles

---

### Post by geoff123 on 2010-01-04
gilch, I'm a little confused now.  You're going to have to share a lot more info about your setup and what you are trying to accomplish.  This started out as a rsync question that is morphing into something else now.    I use rsync quite a bit (on serveral OS's) and thought I could help out with that, but if you are now talking about installing another OS, etc. I'm not sure I'm the best for that.

---

### Post by gilch on 2010-01-04
Sorry about that. Let's stick with rsync. I need to solve this before doing anything else. I don't want to do anything else before I have a secure back up. Right now, i can't trust rsync. Please help me out.

To clarify my setup.
I have ubuntu 9.04 installed on a smallish drive. I have two other drive (NTFS) where my data resides.
I have an external WD 2TB drive (NTFS). This is where I want to back up my data. 
I used the form
sudo rsync -av /home/gilles/files /media/"My Book" --delete

(someone told me I should us t instead of a???)

There is a dozen or two directories (folders) that rsync cannot backup.(Output/input error (5)

rsync continues after each of these errors, and copies other files normally, until it get's to another Output/input error. 

I have no preference for whatever will do the backup. It could be another program than rsync.I'm even prepared to buy one if it will help me. 

I'm very grateful for your help.
Gilles

---

### Post by SecretCode on 2010-01-05
> **gilch said:**
> sudo rsync -av /home/gilles/files /media/"My Book" --delete

(someone told me I should us t instead of a???)
That was me, but it only relates to rsync being unable to set permissions on ntfs volumes. This does not sound like it's affecting you.

> **gilch said:**
> There is a dozen or two directories (folders) that rsync cannot backup.(Output/input error (5)

This does seem like there are some file system or IO channel errors. What is the actual output for these directories? Use the -vv option on rsync ... yes, two 'v's ... increased verbosity.

Is it always the same directories that result in the errors?

---

### Post by geoff123 on 2010-01-05
Maybe try this instead:

rsync -iurt --progress --modify-window=4 /home/gilles/files "/media/My Book" 

Note I added the modify-window command, which I've needed in the past with windows due to differences in the way the systems handle dates. May or may not be needed for you.  

I changed the quotes"" around to see if that makes a difference.  

This leaves out the "-p" which was implied with your "-a". 
You would be wise to read the "man rsync" to understand what all these do. 

you may need to prepend sudo also. 

You can always add the --delete command later if you need to, but put it at the beginning of the command instead, like this.  

rsync -iurt --progress --delete --modify-window=4 /home/gilles/files "/media/My Book"

---

### Post by gilch on 2010-01-06
Nothing has helped so far.
I have done some checking.

I deleted the whole directory with the 1st problem from the source drive. Then ran rsync again.

It turns out that the said directory is now completely empty on the output drive, but when I go in it refuses to delete that directory saying that it is not empty.

I am completely stunned.

There does not seem to be a way out.

Gilles

---

### Post by SecretCode on 2010-01-06
> **geoff123 said:**
> Yes - Checking the disk from windows is probably a good idea also.

Can you do this? Even from a virtualbox install if you don't have a windows installation any more.

---

### Post by SecretCode on 2010-01-06
> **SecretCode said:**
> This does seem like there are some file system or IO channel errors. What is the actual output for these directories? Use the -vv option on rsync ... yes, two 'v's ... increased verbosity.

Is it always the same directories that result in the errors?

Can you do this?

---

### Post by gilch on 2010-01-06
To your first reply. I do not have a windows installation.
TO your second. I tried but it runs so fast I can't identify the problem lines.

But why can I not delete that so-called not-empty empty directory, even using the command rm -D ?

Thanks for your patience... mine is getting thin.

Gilles

---

### Post by SecretCode on 2010-01-06
I suspect the answer to "why can't it be deleted" is the answer to all these troubles!

I'd recommend installing windows XP in a virtualbox virtual machine, in order to run chkdsk - or reformatting the entire drive to ext3/ext4. 

To capture the message output, try redirecting to a file - something like this:
```
rsync -iurt --progress --modify-window=4 /home/gilles/files "/media/My Book" -vv &> rsync-output.txt
``` 
but instead of all /files, just specify the directory giving problems.

---

### Post by gilch on 2010-01-06
You mean both drives are bad then?

I cannot delete the directory in the TARGET drive.

I cannot copy some files from the SOURCE drive.

I need to thrash nearly 1TB of music because of a dozen directories? There must be something to be done. 

I can't use Windows. I have Win7 but it is not installed. I was waiting to clear up these problems, bet a proper backup and then do that. 

I will try something else first and come back.
Gilles

---

### Post by SecretCode on 2010-01-06
You can use windows in virtualbox. Don't activate it. This will not mean deleting any data.

---

### Post by geoff123 on 2010-01-06
gilch, 

relax and take as step back.  if the goal is to only copy stuff from one directory to another, why not just use the file manager? or from command line.  

Start over and try this:

```
sudo cp -R /home/gilles/files "/media/My Book"
```

Or better yet, try this for only the problem directories.  Sorry if I'm repeating here, but I feel that maybe we're missing something simple.  

Also,
> But why can I not delete that so-called not-empty empty directory, even using the command rm -D

That is an invalid command.  Try the -IRf instead of -D.  That will remove the files and directories.  But be very careful with that.

One more thing that is a longshot.  Are you sure that your external hard drive is mounted at /mount/My Book ?  I mean if it weren't you would just be filling up the local drive. Can you see hard drive blinking hear it when copying?

---

### Post by gilch on 2010-01-07
Thanks for staying with me here. I know I'm probably frustrating you. Sorry

The idea is NOT to just copy all files to the external disk.
The idea is to make a BACKUP, and being able to add to the backup without having to redo the whole thing all over again. And it has to be reliable: not having a dozen directories not working every time is not acceptable. I am not interested in just copying. It takes almost two days to copy 1TB through USB.

If rsync is not suited for that job then I need something else. I am willing to buy commercial software if Linux doesn't have any. Is there something else than rsync I can use that will not redo the copying every time? I've already lost two weeks on this.

If a different software come up with the same problem on the same directories then I'll know it's the drive that is the problem.

Those files that won't copy play their music perfectly well. No difference from one file to the next.

Regarding whether My Book is mounted. I am quite sure it is: it put a My Book icon on my desktop, and yes the lights go when I access it.

Thanks again, Gilles.

---

### Post by gilch on 2010-01-07
I have been reading all kind of stuff on input/output errors in rsync.

I got the idea that I could copy my source 1TB drive onto another 1TB drive (2d drive), and then try to rsync the 2d drive to the External 2TB drive. If the problems were with the source drive, then everything should be OK.

You suggest using something like 

sudo cp -R /home/gilles/files "/media/My Book"

I read somewhere that when you do that there might be changes occuring in the permissions in the output? Is that true, or are the output file totally identical to the originals?

While I wait for your answer I will start that process and see what happens. If it's true that there are problems with permissions well, I guess I`ll have to start again.

---

### Post by geoff123 on 2010-01-07
> I read somewhere that when you do that there might be changes occuring in the permissions in the output? Is that true, or are the output file totally identical to the originals?

Not sure.. but don't worry about the permissions for now.  Assuming they are only normal user files such as documents and mp3s, etc.. then you can always go in and fix the permissions in the future.  The data in the files is separate from permissions.

I would not rely on saving all attributes like permissions when mixing a Linux with a Windows filesystem.  This is not good practice and they were never meant to be used like this.  However, I'd feel comfortable that the data in your files are okay. 

I would suggest that you stick with the default linux filesystem (ext3 or ext4) in the future and if you must, backup to NTFS using rsync.

---

### Post by gilch on 2010-01-08
Just for your information Geoff and SecretCode, I am now in deep doo doo and I have no idea what I have done. I can no longer get on. I posted a question on General Help entitled "Fail to boot".

Should I reinstall Ubuntu?
Gilles

---

### Post by SecretCode on 2010-01-09
[Link to the thread]("http://ubuntuforums.org/showthread.php?t=1375876")

---

