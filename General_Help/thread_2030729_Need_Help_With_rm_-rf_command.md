---
title: "Need Help With rm -rf command"
date: 2012-07-21
forum: General Help
---

### Post by UltimateCat on 2012-07-21
I am trying to un-install the hplip-3.12.6 for my printer.

The HP help page advises to do this (uninstall) if the terminal read out says
```
pp-build=no

```

It should says 
```
pp-build=yes

```

I opened the terminal and tried to execute the command that HP recommends but nothing happened-  Please advise 

```
rm -rf /usr/share/hplip-3.12.6

```

Here's what I have tried
cat@ztcat:~$ rm -rf /usr/share/hplip-3.12.6
cat@ztcat:~$

---

### Post by zombifier25 on 2012-07-21
Nothing means the process executed successfully. You can add the -v (verbose) so that you can see the process.

Is the folder still there after deleting?

---

### Post by Elfy on 2012-07-21
If the command failed you would get an output.

If there is nothing there then it should have worked.

Update the dbase and see if you can find it 

```
sudo updatedb

locate /usr/share/hplip-3.12.6
```

Not sure why the page would have said that - you've uninstalled nothing - just removed a file/folder.

---

### Post by UltimateCat on 2012-07-21
> **zombifier25 said:**
> Nothing means the process executed successfully. You can add the -v (verbose) so that you can see the process.

Is the folder still there after deleting?

Yes, the file/folder named hplip-3.12.6 is one my Desktop.

I'll try going into the printer Manager and see if I can remove any hplip driver that way-  I'll use ( -v ) like use advised-

If that fails then I'm clueless

---

### Post by Quackers on 2012-07-21
It won't delete the one on your desktop. The command is to delete the file of that name from /usr/share directory.

---

### Post by UltimateCat on 2012-07-21
> **Elfy said:**
> If the command failed you would get an output.

If there is nothing there then it should have worked.

Update the dbase and see if you can find it 

```
sudo updatedb

locate /usr/share/hplip-3.12.6
```Not sure why the page would have said that - you've uninstalled nothing - just removed a file/folder.

It was in my Home folder...I drug and dropped it to my Desktop and its there for now-  I don't understand why un-installing is so difficult. You have more experience than I what is the problem you think?

Should I re-execute:
```
rm -rf /usr/share/hplip

```
Or just delete the file on my Desktop?

---

### Post by UltimateCat on 2012-07-21
> **Quackers said:**
> It won't delete the one on your desktop. The command is to delete the file of that name from /usr/share directory.
Didn't know that-
Thank You:)

---

### Post by Quackers on 2012-07-21
If you look in your file system in the usr directory there will be a folder there called share. Open that and see if the hplip-3.12.6 file/folder is gone.
If it's gone the command worked. The copy on your desktop is irrelevant, I would say.

---

### Post by Quackers on 2012-07-21
> **UltimateCat said:**
> Didn't know that-
Thank You:)
You're welcome. We're all still learning :-)

By the way, the rm -rf command is a very powerful command and should be used sparingly - and never when you don't know what it's going to do. Better to ask first to save you deleting something your system may need.

---

### Post by kyphi on 2012-07-21
You have to use "sudo" otherwise the commands you put in will do nothing at all.

To totally remove hplip:

sudo rm -rf /usr/share/hplip
sudo rm -rf /etc/hp
sudo rm -rf ~/.hplip
sudo rm -rf /var/lib/hp

If you have placed hplip files in other places such as your Desktop, just delete them.
Please note that the version number of hplip is not part of the commands.

---

### Post by UltimateCat on 2012-07-21
> **Quackers said:**
> If you look in your file system in the usr directory there will be a folder there called share. Open that and see if the hplip-3.12.6 file/folder is gone.
If it's gone the command worked. The copy on your desktop is irrelevant, I would say.
I went under user found the share folder hplip is still there.

---

### Post by UltimateCat on 2012-07-21
I opened the terminal and executed like you advised. Hitting enter after @ command.
```
sudo rm -rf /usr/share/hplip
sudo rm -rf /etc/hp
sudo rm -rf ~/.hplip
sudo rm -rf /var/lib/hp

```

```
cat@ztcat:~$ sudo rm -rf /user/share/hplip
[sudo] password for cat: 
cat@ztcat:~$ sudo rm -rf /etc/hp
cat@ztcat:~$ sudo rm -rf ~/.hplip
cat@ztcat:~$ sudo rm -rf /var/lib/hp
cat@ztcat:~$ 

```

I went to /user/share and checked -
It's still there-
Is there another way?

---

### Post by kyphi on 2012-07-21
Sometimes you have to reboot to effect changes.

---

### Post by UltimateCat on 2012-07-21
> **kyphi said:**
> Sometimes you have to reboot to effect changes.
I started to ask myself; In order for a command to be effective would I have to reboot?

I'll try that and see what comes of it-
I just want this to be over because I'm trying to un_install so that I can re-install:(

---

### Post by UltimateCat on 2012-07-21
Folder in /user/share/hplip is gone after a reboot.

Thank You for the help.:popcorn:

---

