---
title: "Retrospect client install with alien"
date: 2009-08-22
forum: General Help
---

### Post by AlexBooton on 2009-08-22
Hi,

I can't find a .deb package to install the EMC Retrospect client for linux (a file backup system).

So I thought I'd follow some steps I found by googling that uses alien to convert an .rpm to a .deb.

The steps are posted here: [http://forums.dantz.com/showtopic.php?tid/31192/](http://forums.dantz.com/showtopic.php?tid/31192/)  

And this is what it says:
****** start quote ********
Yes, it is enough to install lib32stdc++6

This is the way how I did it:
- aptitude install alien
- aptitude install libstdc++6
- Donwloaded Linux_Client-XXX.rpm from here (XXX is your version)
- alien Linux_Client-XXX.rpm
- vim retroclient-XXX/debian/control
- Set the Architecture to amd64 or append amd64 to it (devided by a space)
- retroclient-XXX/debian/rules binary
- dpkg -i retroclient_XXX_amd64.deb
- update-rc.d rcl defaults 99
****** end quote **********

Everything seems to go OK until I get to "retroclient-XXX/debian/rules binary".  At that point I get 

"dh_testdir: cannot read debian/control: No such file or 
directory"

I don't know why, This file does exist and I'm running under sudo.

Any ideas?

Thanks

P.S. If anyone has this .deb package, especially for amd64, I'd greatly appreciate a copy.

Thanks


But I can't get it to work.  I get

---

### Post by mrpeachum on 2009-10-22
I don't remember how I did it, but I have a working .deb package that works with Retrospect 7 for Windows on 8.04 server amd64 version. I can email it to you if you PM me! 

/Erik

---

### Post by Marty Connor on 2009-12-25
I needed to install Retrospect Client on a Ubuntu 9.10 (Karmic)  machine so it could be a client to my Retrospect server, which backs up Linux, Windows, and Macintosh machines in our facility.  The machine is a running 64-bit, which complicates things a little bit.

I basically followed the previous instructions, but had some issues.  I was able to get things to mostly work, and I have successfully done a backup.

I think there are some minor issues with filesystem layout and assumptions about what shell is being used.  This led to some minor error messages, but nothing fatal.

Hopefully this will help someone else, and maybe someone can take it further, and get rid of more warnings and errors during build and installation.

My Recipe:

# Install required packages
$ sudo aptitude install alien
$ sudo aptitude install libstdc++6
$ sudo apt-get install libc6-i386

# Download Retrospect Client .rpm
$ wget [http://download.dantz.com/archives/Linux_Client-7_6_100.rpm](http://download.dantz.com/archives/Linux_Client-7_6_100.rpm)

# Do initial conversion
$ sudo alien --scripts Linux_Client-7_6_100.rpm

"--scripts" seems to be needed to have the install script run to set a password for connecting the first time.

# Fix up architecture if required (64 bit systems, particularly) by editing the debian/control file with a text editor
# I happen to have used emacs, but vi, gedit, nano, or others should work fine
# Set the Architecture to amd64 or append amd64 to it (devided by a space)

$ cd retroclient-7.6.100
$ sudo emacs debian/control

# Find the line that says:
#      Architecture: i386

# and change it to say:
#     Architecture: amd64

# Then save your changes (however you do in your editor)

# Build binaries
$ sudo debian/rules binary

# Install .deb package
$ cd ..
$ sudo dpkg -i retroclient_7.6.100-2_amd64.deb

I got prompted for an initial password here.

Now we just need to set up /etc/init.d/rcl to run at the appropriate times.

# Update rc.d startup scripts
$ sudo update-rc.d rcl defaults 99

# Inspect/Modify startup scripts
$ sudo sysv-rc-conf

Now I have a retroclient_7.6.100-2_amd64.deb that I can use to install on other Ubuntu 64 bit machines.

---

### Post by sk1nnycowboy on 2010-03-24
I had to do some fiddling to get my deb to build. I already had installed the 32 bit libraries, but that didn't seem to help me at all.  

When I tried to run 

```
root@local:~# alien --scripts -v Linux_Client-7_6_100.rpm 
```

I kept getting:

> dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)

... which appeared to be caused by a line in the file **./retroclient-7.6.100/debian/control** part way during the generation of the .deb package. 

The file that was being created was not putting **amd64** in the "Architecture" line. Since this file was being created by alien, I could not go in to the file after the fact, and manually adjust that line. 

The way I finally worked around the problem was to go in and edit the file **/usr/share/perl5/Alien/Package/Deb.pm** and changed 

```
print OUT "Architecture: ".$this->arch."\n";
```

at line 357 to 

```
print OUT "Architecture: ".$this->arch." amd64\n";
```

I realize that this probably is not the best solution, but it did allow me to build the .deb package, and now I do have a functioning retrospect client.

If anyone wants, they can download my binary. 
[http://0z.ca/files/NetworkClients/retroclient_7.6.100-2_amd64.deb.zip]("http://0z.ca/files/NetworkClients/retroclient_7.6.100-2_amd64.deb.zip")

---

### Post by JGrubbs on 2010-05-01
I got a StorCenter ix2-200 today, I have the Iomega Storage Manager installed, and I downloaded and ran your retroclient_7.6.100-2_amd64.deb.zip but when I go to the "Retrospect Clients" section of the Iomega Storage Manager I get this message:

[I]There are currently no backup clients defined!

Run Iomega StorCenter Manager to activate backup on your computers.[/I]

How do I use the Retrospcet Client to start backup up my data?

---

### Post by skforu007 on 2010-06-22
> **sk1nnycowboy said:**
> I had to do some fiddling to get my deb to build. I already had installed the 32 bit libraries, but that didn't seem to help me at all. 
 
When I tried to run 
 
```
root@local:~# alien --scripts -v Linux_Client-7_6_100.rpm 
```
 
I kept getting:
 
 
 
... which appeared to be caused by a line in the file **./retroclient-7.6.100/debian/control** part way during the generation of the .deb package. 
 
The file that was being created was not putting **amd64** in the "Architecture" line. Since this file was being created by alien, I could not go in to the file after the fact, and manually adjust that line. 
 
The way I finally worked around the problem was to go in and edit the file **/usr/share/perl5/Alien/Package/Deb.pm** and changed 
 
```
print OUT "Architecture: ".$this->arch."\n";
```
 
at line 357 to 
 
```
print OUT "Architecture: ".$this->arch." amd64\n";
```
 
I realize that this probably is not the best solution, but it did allow me to build the .deb package, and now I do have a functioning retrospect client.
 
If anyone wants, they can download my binary. 
[http://0z.ca/files/NetworkClients/retroclient_7.6.100-2_amd64.deb.zip](http://0z.ca/files/NetworkClients/retroclient_7.6.100-2_amd64.deb.zip)
 
 
I have installed the Retrospect client but enable to start the services.
 
Do any budy know how to start the services.....

---

### Post by gypsumwolf on 2011-10-11
> **skforu007 said:**
> I have installed the Retrospect client but enable to start the services.
 
Do any budy know how to start the services.....

I got it installed but can't get it to run as a service either.
How could I get it to run?

Also, Is there any other programs like this or Net Backup that work in Ubuntu?

---

