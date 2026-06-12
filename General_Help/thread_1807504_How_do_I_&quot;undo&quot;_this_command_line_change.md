---
title: "How do I &quot;undo&quot; this command line change to my system?"
date: 2011-07-19
forum: General Help
---

### Post by stevennlv on 2011-07-19
From the Ubuntu documentation (For Stricter Defaults):

 _**"su" program available to non-admin users**_

 This is not  necessarily a problem alone, but if there are accounts with weak  passwords on the system a malicious non-admin user (or malicious  software they are using) might use su to gain access to such accounts. To deny non-admin users access to su, type this in a terminal: 

sudo dpkg-statoverride --update --add root admin 4750 /bin/su

OK, I did it. Now I'm thinking I shouldn't have. I'm having some issues and I 
think this may be causing them. 

I can't get several different pieces of software to install properly now. I've "undone" all the other changes listed on the above quoted page.  But, I've searched all over the place and can't figure out how to "undo" this last one?

---

### Post by matt_symes on 2011-07-19
Hi

Try

```
sudo dpkg-statoverride --remove /bin/su
```Be careful of typing commands from the Internet if you do not know what they do.

Kind regards

---

### Post by mikejonesey on 2011-07-19
the default is;
-rwsr-xr-x 1 root root 34024 Feb 15 20:54 /bin/su

(sticky bit by user (4 - SUID))
user = 7
group = 5
other = 5

if you want switch it back to 4755
```
sudo chmod 4755 /bin/su
```

---

### Post by stevennlv on 2011-07-19
> **matt_symes said:**
> Hi

Try

```
sudo dpkg-statoverride --remove /bin/su
```Be careful of typing commands from the Internet if you do not know what they do.

Kind regards

Thankx for the help.

I'm poking and playing on a VM. If I blow it up I'll just have to make another one. Which would be a complete and total pain the butt. So I think I'm going to make another one to poke at so I don't blow this one up! ;)

I found another way to do it though (I thought it would take a long time to get an answer):

I searched for "statoverride" then opened it with gksudo gedit and removed the added line. Fortunately the command backed up the old file and changed the extension to .old. So I just made sure the new one matched the old one!

---

### Post by stevennlv on 2011-07-19
> **matt_symes said:**
> Hi

Try

```
sudo dpkg-statoverride --remove /bin/su
```Be careful of typing commands from the Internet if you do not know what they do.

Kind regards

Ok, my solution did not work.

So I tried yours. I got an error message saying that there was an empty line in the file. Since I had removed one that made sense. So I used gksudo gedit to open the file statoverride.old and rename it as statoverride and then replaced the other new (mutilated by me) file with that same name (statoverride).

So I'm thinking I should have the original file restored now and be back to a pretty much default system install. I've added some stuff, but not much.

I've got the google earth package from medibuntu, I've added flash, java and some plug ins to stream the types of files that media player would normally handle. That's pretty much it.

But now it's doing goofy stuff.

I tried to install avast, but thet never sent me one of their keys. So I uninstalled it using

sudo apt-get remove avast

Which really did not work all that well. I still have avast listed in my accessories menu. But the icon is gone. And as far as I can tell so is the rest of the program?

I tried to install clamav and got several error messages. So I used the same command to uninstall it. Now terminal is saying this:

XXXX@ubuntu:~$ sudo apt-get remove clamav
[sudo] password for XXX: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package clamav is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-28-generic linux-headers-2.6.32-28 clamav-freshclam
  clamav-base libclamav6 libtommath0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So, I entered 

apt-get autoremove

And got this back

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
XXXX@ubuntu:~$ 

I'm also having trouble with truecrypt. When I install it it runs just fine until I reboot. Then it's gone when I boot back in. I was going to try the old windows trick of un/re-install. But when I try to uninstall truecrypt I get an error message saying package is not installed, so not removed. 

I'm stuck.  

Help would be greatly appreciated. 

I really hope I haven't borked this thing too badly. I really don't want to start over from scratch.

---

### Post by stevennlv on 2011-07-19
Update:

I was able to get all the rest of clamav out using the software manager.

But, now when I use 

apt-get install clamav

I get

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I'm sure that whatever this is it's something I messed up.

Any idea how I fix it?

---

### Post by stevennlv on 2011-07-19
Learning a new OS is as much fun as banging your head against a brick wall, just without all the fun.

I got clam av straightened out. 

It helps if you run commands in sudo, eh?

But, I'm still stuck on truecypt.

When I run **sudo** apt-get remove truecypt I get an error message say there is no such package.

But I just watched clam av scan it with my own eyes (I put KlamAV on the front end).

So clam can see the folder but apt-get cannot.

The installer for truecrypt tells me to run " truecypt-uninstall.sh"

But I can't figure that one out yet.

Any suggestions?

---

### Post by matt_symes on 2011-07-19
Hi

Sorry for the delay. 

It sounds like you are making progress though. There is always a learning curve associated with learning a new operating system but perseverance is the key.

As for TrueCrypt, it's not a piece of software i use. However, TrueCrypt is asking you to run the file truecypt-uninstall.sh.

Find it either in the terminal or in nautilus file browser then run the file. In Nautilus right click on the file and select open and then run in terminal.

In a terminal, navigate to the directory containing the file and type 

```
./truecypt-uninstall.sh
```

This will run the file if it is an executable script. If not you need to change the permissions of the file.

Kind regards

---

### Post by stevennlv on 2011-07-19
> **matt_symes said:**
> Hi

Sorry for the delay. 



No worries at all. I greatly appreciate the help.

I've got everything fixed, almost.

And to be perfectly honest I'm not sure exactly how I did it! :shock:

I've been researching, poking, testing and seeking advice for about 6 - 7 hours now. (Marathon session.)

The only thing that I haven't got straightened out yet is how to update the clam av engine from
version 0.96.5 to version: 0.97.1

Any suggestions?

Time for bed here.

But I'll check back after work.

Once again, thanks for the help.

---

