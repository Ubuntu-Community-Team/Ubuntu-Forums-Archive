---
title: "Directory turned into File"
date: 2012-02-01
forum: General Help
---

### Post by jr226 on 2012-02-01
I am running Ubuntu 11.10, as well as Windows 7 on another partition.  I have used primarily Ubuntu for the past several months, and booted up to Windows this past weekend for a project requiring Visual Studio.  I also recently started using dropbox.

Today I went to access a directory in MATLAB which contained work for my thesis, only to find the directory had been turned into an extensionless file.  Is there anyway to convert this back to a directory? Some permission or settings I can change?  I can see the "file/directory" in the command line, but not in the GUI windows explorer.

Thanks for any help, this directory contains several weeks of work, so any help is really appreciated...

JR

PS, I will be backing up from now on :), should I just use the built in utility, or anyone have other suggestions?

Also, the corrupt directory is located on a partition for my data, shared by both Windows and Ubuntu.

---

### Post by sanderd17 on 2012-02-01
Can you show me the permissions of the directory and the files in the directory?

You can do it with 

```

ls -l /path/to/file/or/directory

```

You will see something like

```

-rw-r--r-- user group filename

```

I need to get that info for the directory and for the files in it.

---

### Post by jr226 on 2012-02-01
The corrupted directory returns:

[INDENT]$ ls -l /media/mpoint/Documents/College/Masters/Research/MATLAB/McyMdlStudy/TorqueReqd
ls: cannot access /media/mpoint/Documents/College/Masters/Research/MATLAB/McyMdlStudy/TorqueReqd: Input/output error[/INDENT]

and the parent directory to the corrupted on returns:

[INDENT]total 161
drwxrwxrwx 1 root root     0 2012-01-29 14:46 dFZ.m
-rwxrwxrwx 1 root root  2704 2012-01-19 19:33 EA1_Project1.m
-rwxrwxrwx 1 root root  1141 2012-01-06 11:08 EOM_pointDualMassAeroLoadTrans.m
-rwxrwxrwx 1 root root   741 2012-01-23 13:54 EOM_pointDualMassAero.m
-rwxrwxrwx 1 root root   565 2011-11-09 11:46 EOM_pointMassAero.m
-rwxrwxrwx 1 root root   465 2011-11-08 20:03 EOM_pointMass.m
-rwxrwxrwx 1 root root  2122 2011-11-09 11:47 EOM_suspDualMassAero.m
-rwxrwxrwx 1 root root 69317 2007-10-02 14:13 expand_mrandim.p
-rwxrwxrwx 1 root root  6024 2005-08-25 09:56 Goodyear 20x7-13.mat
-rwxrwxrwx 1 root root  4568 2010-05-07 11:10 Goodyear_D2696_20.0x7.0-13_8in. rim_12psi.mat
-rwxrwxrwx 1 root root  5859 2011-11-09 22:57 matlab.mat
-rwxrwxrwx 1 root root   814 2005-09-01 20:45 muexpansion.p
-rwxrwxrwx 1 root root  5098 2011-11-10 21:33 ODEhelper.m
-rwxrwxrwx 1 root root  3432 2012-01-04 16:48 odePitch.m
-rwxrwxrwx 1 root root  6941 2011-11-10 21:18 PhaseHelperPwrLim.m
-rwxrwxrwx 1 root root  5025 2012-01-06 08:54 PhaseHelperUnlimited.m
-rwxrwxrwx 1 root root 10411 2011-11-10 17:36 PhasePwrLim.mat
-rwxrwxrwx 1 root root   295 2011-11-04 14:47 PowerReq.m
-rwxrwxrwx 1 root root   187 2011-11-08 20:11 saveFigures.m
[B]d????????? ? ?    ?        ?                ? TorqueReqd
[/B]-rwxrwxrwx 1 root root  1440 2011-11-09 10:57 TyreModelHelper.m
-rwxrwxrwx 1 root root   632 2012-01-20 14:18 xddlock.m
-rwxrwxrwx 1 root root   569 2012-01-19 19:50 xddloss.m
[/INDENT]

Thanks!

---

### Post by ajgreeny on 2012-02-01
Are you sure you shutdown Win7 completely, and did not just hibernate or suspend it, as is the deafult, I think, just like it was for Vista?

---

### Post by sanderd17 on 2012-02-01
+1 to the thing mentioned above.

I'm not sure, but maybe you can reset the permessions.

```

sudo chmod 755 TorqueReqd
sudo chown username:username TorqueReqd

```

I can't guarantee that this will work, and maybe it will damage your data even more. So it would be best to wait for a second opinion.

---

### Post by m_duck on 2012-02-01
> **sanderd17 said:**
> I'm not sure, but maybe you can reset the permessions.
```

sudo chmod 755 TorqueReqd
sudo chown username:username TorqueReqd

```I can't guarantee that this will work, and maybe it will damage your data even more. So it would be best to wait for a second opinion.
If it's a shared partition, it is likely NTFS of FAT (so Windows can read it), neither of which can manage permissions so I suspect the above commands will not work.

---

### Post by sanderd17 on 2012-02-01
> **m_duck said:**
> If it's a shared partition, it is likely NTFS of FAT (so Windows can read it), neither of which can manage permissions so I suspect the above commands will not work.

Yes, you're right.

So all files on that partition should be mounted with the same rights and owners.

Does anyone has an idea what's different for that one directory?

---

### Post by WorMzy on 2012-02-01
It's corrupted. Run chkdsk from Windows, and hope.

---

### Post by jr226 on 2012-02-01
I restarted the Windows side to make sure it was shut down completely, when I did it tried to run the disk checker (I cancelled it).  I'm saving my important files to an external, and then I was going to reboot and see if the disk checker would help.  

The shared data drive is formatted NTFS.

---

### Post by jr226 on 2012-02-01
> **WorMzy said:**
> It's corrupted. Run chkdsk from Windows, and hope.

Just from the windows command line : chkdsk ?

Thanks.

---

### Post by jr226 on 2012-02-02
Thanks for all the help, the files are completely gone now.  I talked to a friend, and he stated he had a similar situation.  He was dual booting Windows/ Some Linux variant.  Switched to running primary Linux and then booted windows and had files corrput, he thinks because of the disk checker.  I realize this is most likely Windows fault, but is there anything which could be done on Ubunut side?  

My solution will be to start an offsite server and some form of version control for my future code.

---

### Post by WorMzy on 2012-02-03
Have you checked under "C:\FOUND.000"? That's where chkdsk puts files that have been recovered. If not, then try [photorec]("http://www.cgsecurity.org/wiki/PhotoRec"). You can run it from Ubuntu, and it can recover documents (often as archives if they're richly formatted) and images.

---

### Post by varunendra on 2012-02-03
> **WorMzy said:**
> Have you checked under "C:\FOUND.000"? That's where chkdsk puts files that have been recovered. If not, then try [photorec]("http://www.cgsecurity.org/wiki/PhotoRec"). You can run it from Ubuntu, and it can recover documents (often as archives if they're richly formatted) and images.
+1 to photorec.

Step-by-step guide: [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

It has both windows and linux versions (as well as mac, although irrelevant here).

Installation in Ubuntu:
```
sudo apt-get install testdisk
```
(yes it is part of testdisk installation)
running photorec:
```
sudo photorec
```

---

