---
title: "Searching everywhere for a file by name?"
date: 2009-08-10
forum: General Help
---

### Post by starbase1 on 2009-08-10
I'm getting myself seriously confused by searching for files... In some cases it's finishing so fast I'm not surprised it found nothing, even though I now there are some matching files, and it is really doing my head in!

So I'd appreciate some tips, more specifically:

How can I find matching files in all mounted drives and locations, including system folders etc? Example *.iso?

Graphic and command line would be cool...

I'm also thinking that I don't understand where applications would normally be expected to put their files, (I'm particularly thinking of VirtualBox in this case, I'm trying to find it's VM's and having no luck.)

Cheers,
Nick

---

### Post by nothingspecial on 2009-08-10
Try [[COLOR="Red"]catfish[/COLOR]]("https://help.ubuntu.com/community/Catfish")

---

### Post by joper90 on 2009-08-10
command line

find / -name <file>

so, find from root / (or another place) -name (search for a name) then the file *iso (you don't need the .iso like in dos)

However, if you do this you may get loads off odd cannot search type errors, especially if searching from root.. so run it as sudo.

Obviously -name can be other things too.. man find :)


if its a program, you can try which <program name> to get the location, for example you have 3 firefoxes installed on your system, which firefox will return the one that gets ran based on your path.

---

### Post by mcduck on 2009-08-10
Find will search for files:
```
find / -name *.iso
```

Alternatively, for a faster search, you can use locate, but locate is database-based and thus will not find any new files, only stuff it has already indexed in it's database. 
So if you try to find any recentlya dded files you need to update the database first.
```
locate *.iso
```
and to update the database:
```
sudo updatedb
```

What comes to application file locations, depnds on waht you mean. The applications themselves are installed alla rounf the file system, each files put to different places based on the purpose of that file. For example executable files for all user-level applications are in /usr/bin, documentation in /usr/share/doc and so on.

And all the files created when you actually use the programs, as in your settings an data, will go into your own home directory. Normal users don't have write permissions anywhere outside their home directory so that's pretty much the only possible place.. ;)

I don't use VirtualBox myself, but assuming you run it as a normal user (without "sudo", that is), you'll find your virtual machines in a hidden directory inside your home.

---

### Post by starbase1 on 2009-08-10
> **nothingspecial said:**
> Try [[COLOR="Red"]catfish[/COLOR]]("https://help.ubuntu.com/community/Catfish")

Ah, that sounds very handy, thanks!

Nick

---

### Post by starbase1 on 2009-08-10
> **joper90 said:**
> command line

find / -name <file>

so, find from root / (or another place) -name (search for a name) then the file *iso (you don't need the .iso like in dos)

However, if you do this you may get loads off odd cannot search type errors, especially if searching from root.. so run it as sudo.


Ah, this sounds handy too, the lack of sudo and / would have been where I was going wrong! Thing with this command is that unless I know the files are there, I have no idea if I typed it correctly - cheers!
:)

---

### Post by slakkie on 2009-08-10
> **joper90 said:**
> command line

find / -name <file>

so, find from root / (or another place) -name (search for a name) then the file *iso (you don't need the .iso like in dos)

However, if you do this you may get loads off odd cannot search type errors, especially if searching from root.. so run it as sudo.

Obviously -name can be other things too.. man find :)


if its a program, you can try which <program name> to get the location, for example you have 3 firefoxes installed on your system, which firefox will return the one that gets ran based on your path.

Or you redirect those errors to /dev/null:

```

find / -name \*.iso 2>/dev/null

```

---

### Post by mcduck on 2009-08-10
> **starbase1 said:**
> Ah, this sounds handy too, the lack of sudo and / would have been where I was going wrong! Thing with this command is that unless I know the files are there, I have no idea if I typed it correctly - cheers!
:)

Actually you don't need the sudo, and you can ignore the errors. They are simply a result from normal user's not having access to some system files and will not cause any problems unless you are specifically looking for those files.

---

### Post by starbase1 on 2009-08-10
> **mcduck said:**
> Find will search for files:
```
find / -name *.iso
```

What comes to application file locations, depnds on waht you mean. The applications themselves are installed alla rounf the file system, each files put to different places based on the purpose of that file. For example executable files for all user-level applications are in /usr/bin, documentation in /usr/share/doc and so on.

And all the files created when you actually use the programs, as in your settings an data, will go into your own home directory. Normal users don't have write permissions anywhere outside their home directory so that's pretty much the only possible place.. ;)

I don't use VirtualBox myself, but assuming you run it as a normal user (without "sudo", that is), you'll find your virtual machines in a hidden directory inside your home.

Thanks for the detailed explanation, it will be a big help in going from just copying commands to actually understanding! And I think it's the 'hidden' aspect that was tripping up my search.

Nick

---

### Post by starbase1 on 2009-08-10
And many thanks to all who responded so fast, and with such detail.

This community rocks!
:guitar:

---

### Post by rubblebuster on 2009-08-10
> **starbase1 said:**
> I'm also thinking that I don't understand where applications would normally be expected to put their files, (I'm particularly thinking of VirtualBox in this case, I'm trying to find it's VM's and having no luck.)

Cheers,
Nick

The VMs itself go to

```
/home/<your username>/.VirtualBox/Machines
```but here only configuration and logfiles are stored.

Additionally in the ".VirtualBox" directory you also find the VDIs for your virtual machines - these are the virtual disk images used by the corresponding VMs.

Note: since the ".VirtualBox" directory has a trailing "." it's not visible per se - so you have to enable the "View hidden files and directory" option in Gnome / KDE first.

When it comes to ISO images you might have added as additional drives or CD-ROMs for a Virtual Machine you can specify the location if you add them to VirtualBox - hence it's up to the user where these images are located. Perhaps a default directory is used / suggested by VirtualBox, but I have an extra folder where I locate my ISO-Images...

HTH & Cheers, Erik

---

### Post by starbase1 on 2009-08-10
Thanks Eric, I had already been building the disks elsewhere (on a big shared drive - a big part of the point of all this for me is the portability of VM's!)

It's because I wanted the cobnfig files near the drive images I was asking.

Many thanks,
Nick

---

### Post by lovinglinux on 2009-08-10
I like "Applications >> Places >> Search for Files..." since it allows you to search by file name, search for strings contained in the document and several other options.

---

