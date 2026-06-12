---
title: "Backuppc not backing up my linux client"
date: 2010-10-28
forum: General Help
---

### Post by p2ranger on 2010-10-28
I have been struggling to get backuppc running and finally today figured out what I was doing wrong. Backuppc is running on my Ubuntu 10.04 server. I have it backing up my mac, but I can 't get it work on my Ubuntu 10.04 desktop. I followed the same steps I used in getting it to work in my mac, so I can't really see why there is a discrepancy. This is the error log I'm getting now:

```
full backup started for directory /
Running: /usr/bin/ssh -q -x -l root 192.168.1.120 /usr/bin/rsync --server --sender --numeric-ids --perms --owner --group -D --links --hard-links --times --block-size=2048 --recursive --ignore-times . /
Xfer PIDs are now 14404
Read EOF: Connection reset by peer
Tried again: got 0 bytes
Done: 0 files, 0 bytes
Got fatal error during xfer (Unable to read 4 bytes)
Backup aborted (Unable to read 4 bytes)
Not saving this as a partial backup since it has fewer files than the prior one (got 0 and 0 files versus 0)
```

The dreaded 4 bytes error. I was getting that problem before on my mac, but from what I've managed to find, this error usually shows up when you don't have ssh keys set up properly. Once I got that figured out, it started working on my mac. I can confirm that that part is set up because when I execute the following as the backuppc user on the server:

```
ssh -l root mycomputername whoami
```

The response I get is **root**, which means its working. And I'm not prompted with anything when I enter that line.

That tells me the SSH part of the process is set up correctly. What could I be missing?

Thanks for any help

Jason

---

### Post by click4851 on 2010-12-22
so I don't know if sharing my linux (linux mint 9 by the way) setup will help, but here is my:

 RsyncClientCmd: $sshPath -l root $host nice -n 19 sudo $rsyncPath

also I notice you are trying to backup directory /, I haven't tried that. I first started with /home, and then others. I did have to exclude 

./backuppc/.gvfs ......as it would hang on this.

I also read somewhere in the docs that you can run backuppc manually and verbose to get much more feedback about what is causing trouble. I will review my notes and post it if I find it, goodluck.

---

### Post by click4851 on 2010-12-22
Here it is:

[I]On 07/04/2010 04:03 PM, Matthias Meyer wrote:
> Bob Wooden wrote:
>
>    
>> On the server, I would run the troubleshoot command:
>>
>> 'sudo -u backuppc /usr/share/backuppc/bin/BackupPC_dump -v -f
>> [backupclient]'
>>
>>
>>      
> Hello Bob,
>
> I have some Linux as well as some Windows client with public/private key
> over ssh and I didn't have had this problem with any of my clients.
> Do you have established the host key on the client?
> What is the error message of "'Start Full Backup' would fail"?
>
> The BackupPC_dump isn't a "troubleshoot command" but the normal backup
> command. Normaly called from the backuppc daemon.
>    
For this communication, I choose to call this command a "troubleshoot 
command" because it is the first suggestion to try from the backuppc 
wiki page. The "-v" of the 'BackupPC_dump" portion gives verbose output, 
so users can see what is happen and diagnose failure issues.

When I ran this command, the only thing I remember having to do, in each 
case was, agree that the host was to be added to the 'known_host' file. 
If I understand ssh correctly, that would be the client being added to 
the server (backuppc server) 'known_host' file.

[/I]

Hopefully that can give you more hints as to what is going on....

---

### Post by p2ranger on 2010-12-22
I got it to work, I never changed the status of this post, but thanks for your help anyway :)

Jason

---

