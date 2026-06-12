---
title: "PC will not boot up properly"
date: 2009-11-28
forum: General Help
---

### Post by andypearce on 2009-11-28
Hi, spent yesterday and this morning on this... I am running Ubuntu 9.10.
My PC starts to boot up gets to the white ubuntu symbol and starts to run the disk check... it gets to 70% then stops. I have got a screen up now that says the following (I copied it)

986b173a
filesystem checks are in progress (ESC to cancel):
/dev/sda1 : Duplicate or bad block in use! #----------)
/dev/sda1 : multiply-claimed block(s) in inode  3867042:1048576 1048576 1048576
/dev/sda1 : (There are 1 inodes containing multiply-cla1med blocks.)

/dev/sda1 :file/home/hazel/.mozilla/firefox/rqyhard2c.default/cache/3B877BEBdo1
(inode #3867042 mod time Thu Nov 26 16:55:22 2009)has 3 multiply-claimed block(s) shared with 1 file(s) 

/dev/sda1 :<filesystem metadata>
/dev/sda1 :
/dev/sda1 :UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (i.e.without -a or -p options)
mountall :fsck/[790] terminated with status 4
mountall: filesystem has errors:/

init : mountall main process (789) terminated with status 3
mount of filesystem failed.
A maintenance shell will now be started CONTROL-D will terminate this shell and re-try
root@hazel-desktop:~#_
root@hazel-desktop:~#_
root@hazel-desktop:~#_

That is what it says... I have crashed the pc several times by holding the on button on and it starts up again and freezes up. Prior to this I had a little problem of the PC sometimes freezing... the mouse arrow stopped moving... after about 5 mins and I had to crash it (nothing else worked)

Does anyone recognise the above and have a suggestion of how to fix it? I was so smug when 9.10 ran perfectly on my PC... 
Thanks 
Andy

---

### Post by QLee on 2009-11-28
[QUOTE=andypearce]
/dev/sda1 :UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (i.e.without -a or -p options)[/QUOTE]

The system told you what to try next, as above.

Since you don't want to do it on a mounted file system, do it from the maintenance shell as instructed, ...or you could try from a live CD.

Edit: There is a fairly good chance you introduced the problem with all those "pull the plug" unorderly shutdowns.

---

### Post by andypearce on 2009-11-28
Hi, thanks for your reply, I am (relatively) new in my understanding of this and don't know what it means....or how to do it. 
Andy

---

### Post by hirnwurscht on 2009-11-28
Hello andypearce,

when it drops you to
```
root@hazel-desktop:~#_ 
```
type 
```
e2fsck -v /dev/sda1
```
(-v for more log-output)
and post the output.

---

### Post by andypearce on 2009-11-28
Thanks Hirnwurscht I have done that it gives a load of things in brackets that appear a bit lower in a menu that is titled 'emergency help' the first being -p automatic repair (no questions)[/B]. Do you need more detail than that as I am on another computer downstairs from the problematic one and need to copy the info manually which will take a little time...

---

### Post by andypearce on 2009-11-28
hi... this is it
root @ hazel-desktop:~#e2fsck-v/dev/sda1
e2fsck: invalid option _ _ '/'
usage e2fsck [-panyrcdfvtDFV] [-b superblock] [-B blocksize] [-I inode-buffer-blocks] [-P process-inode-size][-1|-L bad blocks file] [-cfd] [-j external-jornal] [-E extended options] device

Emergency help
-p automatic repair (no questions)
-n make no changes to the file system
-y assume "yes" to all questions
-c check for bad blocks and add them to bad blocks list
-f force checking even if filesystem is marked clean
-v be verbose
-b superblock force locksize when looking for superblock
-J external-journal set location of the external journal
-I bad blocks file  add to the bad blocks list
-L bad blocks file set bad blocks list
root @ hazel-desktop :~#  

took a while....

---

### Post by hirnwurscht on 2009-11-28
I forgot to ask: You did backup your important data already, didn't you?

Read this:
[http://en.opensuse.org/SDB:Fsck:_Unexpected_Inconsistency]("http://en.opensuse.org/SDB:Fsck:_Unexpected_Inconsistency")

It suggests running e2fsck -f -c -y /dev/sda1 in your case.
It also points out that it may be a hardware error.

Maybe deleting /home/hazel/.mozilla/firefox/rqyhard2c.default/cache/3B877BEBdo1 (before e2fsck -f -c -y /dev/sda1 ?) will help, although i have little experience with really borked ext*fs partitions. 

Be sure to backup.

If it's running again, run palimpsest and check the status of the hardrive.

---

### Post by QLee on 2009-11-28
[QUOTE=andypearce]hi... this is it
root @ hazel-desktop:~#e2fsck-v/dev/sda1
e2fsck: invalid option _ _ '/'[/QUOTE]

You need some spaces in the command string so the system can understand what you want to do.

e2fsck -v /dev/sda1

not:e2fsck-v/dev/sda1

---

### Post by andypearce on 2009-11-28
Thanks again,
I will give it a go. I assume I just type it in and press return. I might lose a bit of stuff but that is just hard luck. I don't have a lot of choice.
Here goes.......
Andy

It is doing a bad block test... taking a while..

---

### Post by QLee on 2009-11-28
[QUOTE=andypearce]I might lose a bit of stuff but that is just hard luck. I don't have a lot of choice.[/QUOTE]

Well, the advice to backup first before you try something like that is always good advice, in addition you should backup you important data on a somewhat regular basis so the most you can lose is what was done since the previous backup. However, most of the time the fsck doesn't foul things up, I'll cross my fingers for luck for you.

[QUOTE=andypearce]It is doing a bad block test... taking a while..[/QUOTE]

Yes, expect it to take a while if there are problems to correct.

There are other ways to try and recover from a "freeze", if after your system is back up and working, and you get the freeze again, come back and post about that problem before you remove power by holding the power button, your drive may still be writing.

Edit: On the other hand, if you have lots of bad blocks your drive may be failing, especially if it is an old system. All the more reason to keep frequent backups.

---

### Post by andypearce on 2009-11-28
SOLVED(I think) I'm back on..... wow thought I'd lost it there. Great job... thanks very much. All I need to know now is how to crash the computer safely if it freezes again.Do you think I should remove mozilla and re install it?

Thanks again 

Best wishes

Andy

---

### Post by hirnwurscht on 2009-11-28
Good that it worked. Please mark the Thread as solved and if possible write which of the steps you did (i.e. did you delete the firefox cache file?)

Since we don't know what process or piece of hardware causes the crash, it's not easy to tell how to safely shutdown.

It's way better to actually fix the problem completely instead of just killing the machine.


there is a solution which is called magic sysrequest, a key-combination that will reboot your machine safely in case of a crash. this also mostly works when your machine is pretty stuck.

---

### Post by andypearce on 2009-11-28
Thanks Hirnwurscht.

This is what I did.From when the disk scan found the error I had the above screens, so following the advice I did the following

root@hazel-desktop:~# 

I typed in the code recommended on the attachment supplied.... 

root@hazel-desktop:~# e2fsck -f -c -y /dev/sda1 (remembering to leave the correct spaces... I didn't first time and it didn't recognise it as a command)

The computer then looks for bad blocks running through as a percentage eventually it tells you what it has done and suggests you reboot and leaves you with the command line (?) 

root@hazel-desktop:~# 

I didn't know how to do this but I took a guess and typed reboot

root@hazel-desktop:~# reboot

and it all worked perfectly, with no loss of files.

I have not deleted the mozilla firefox cache as I do not know what this is yet but am working on it. Now to work out how to write solved on the thread!
Thanks Andy

Just worked out how to write solved!!! Thread tools...I am getting the hang of this!

---

