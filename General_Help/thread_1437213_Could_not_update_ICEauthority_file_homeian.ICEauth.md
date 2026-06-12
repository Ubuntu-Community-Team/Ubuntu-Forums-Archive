---
title: "Could not update ICEauthority file /home/ian/.ICEauthority"
date: 2010-03-23
forum: General Help
---

### Post by IanVaughan on 2010-03-23
1) I get this error message when I boot up :-
[IMG]http://farm5.static.flickr.com/4063/4454948761_665957abb8.jpg[/IMG]

2) Then followed by : "There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status-256)"

[img]http://farm3.static.flickr.com/2758/4454948965_4a375165f2.jpg[/img]

3) Then followed by : "Nautilus could not create the following required folders: /home/ian/Desktop, /home/ian/.nautilus. Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them"

[img]http://farm3.static.flickr.com/2802/4454949409_53948c5d7e.jpg[/img]


1. I have tried changing the permissions of the /home/ian/.ICEautority folder  ([as here]("http://ubuntuforums.org/showthread.php?t=949750")) :-
```
sudo chown ian:ian /home/ian/.ICEauthority 
sudo chmod 644 /home/ian/.ICEauthority
```

No luck. (Even tho[ this thread]("http://ubuntuforums.org/showthread.php?t=1081730") states it worked!)


2. As per [this thread]("http://ubuntuforums.org/showthread.php?t=1061084")
None of these worked :-
```
sudo chmod 1777 /tmp
```
```
sudo chmod 755 /etc/gconf/gconf.xml.*
``` ([here]("http://ubuntuforums.org/showthread.php?t=917306"))


I am now really hacked of with Linux!

---

### Post by IanVaughan on 2010-03-27
Well, Ubuntu failed me again!
I know the community would of helped if it could, but it couldnt!

I had to copy my docs out into a new user, and delete my old one! Crap!

---

### Post by dominicsparks on 2010-03-30
I Had this problem too. I followed a lot of suggestions from the forums, none of which worked.
In the end I figured out it's to do with having an encrypted home directory.

When I installed Ubuntu (9.10) I selected the option to encrypt my home directory.  Everything worked fine until I enabled the auto-login. Disabling auto-login (by removing /etc/gdm/custom.conf) got my desktop back.

I read the instructions here: [https://help.ubuntu.com/community/EncryptedPrivateDirectory#How](https://help.ubuntu.com/community/EncryptedPrivateDirectory#How) to Remove an Encrypted Private Directory Setup
to remove the encryption. However, NOTE those instructions imply that the encryption is applied to  ~/Private, but in fact it seems the whole of my home directory is encrypted ( there is no  ~/Private folder, actually).
It also states that the encrypted folder is not mounted when using auto-login, which might explain all the errors and why changing ownership and permissions doesn't seem to work.

I roughly followed the instructions there about removing the encryption, and now I can login, either using auto-login, or one of the 'without password' solutions mentioned elsewhere on the forums. Not sure I did everything 100% correctly, as I got some errors in step 5, and I also failed to copy all the hidden files from my home folder for step 1... but at least it seems to be working again now :)

I think perhaps there is a problem with using the Encrypt option during installation - next time I install ubuntu I won't use that option....

---

### Post by IanVaughan on 2010-03-30
Wow, I too had that setup (encryption) so wish I had found that link!

Should file a bug report somewhere suppose!

---

### Post by ario on 2010-03-31
> **IanVaughan said:**
> Wow, I too had that setup (encryption) so wish I had found that link!

Should file a bug report somewhere suppose!

I told that how I solved mine here:
[http://ubuntuforums.org/showthread.php?t=1021106&page=2](http://ubuntuforums.org/showthread.php?t=1021106&page=2)

---

### Post by Steve Francis on 2010-04-02
My problem is identical with the first post in this thread. I am using 9.04.

(Nautilus stopped working after an update a few weeks ago. In trying to solve that problem, I have now got on to this one.)

I can boot up in recovery mode to a command line but can't find a command which gets me to the desktop. Everyting I type results in the dreaded ICEauthority message.

I can't remember if I chose the encryption option as described by dominicsparks.

How can I retrieve my data!??

---

### Post by Steve Francis on 2010-04-02
I booted up in recovery mode, selected root and typed

```
ls -l /
```and got the screen shown below.

---

### Post by Steve Francis on 2010-04-02
SOLVED! For me anyway, at LinuxQuestions.org

[http://www.linuxquestions.org/questions/linux-newbie-8/locked-out-ubuntu-desktop-permissions-error-799626/](http://www.linuxquestions.org/questions/linux-newbie-8/locked-out-ubuntu-desktop-permissions-error-799626/)

---

### Post by Flos Headford on 2010-04-08
I have tried most of the recommendations above.
Sadly, I was one of the few whom these kind contributions did not help.
In the end, I used a Ubuntu distro disc to get to a command-line interface.
I then removed the .ICEauthority entry from my $HOME directory, and a copy of the same from /var/lib/gdm, ensured that permissions in my $HOME directory were appropriate (usually 755), then used
```
dpkg
sudo apt-get remove nautilus
```
After that, I rebooted by the distro disc method back into a CLI and did
```
sudo apt-get install nautilus
```
On removal of the disc and rebooting by
```
sudo shutdown -r now
```
I now enter a usual boot and login.
It takes a little time, but not as long as a reinstall.
Thanks again to all who have put their efforts into this enquiry,
Phil

---

### Post by outleradam on 2010-12-04
I'm having this same problem.  It should not require reinstallation to enable auto-login.  This is a critical issue.  Is there a bug report?

---

### Post by touf on 2010-12-06
Hi,
I also had this message when loggin.
Furthermore the sound mixer was not working...
(I also installed veetle before).
I noticed that I was not anymore the owner of my own home folder
So in a terminal:
sudo chown -R "me" /home/"me"
and it worked back well

Cheers
Touf

---

### Post by Steve Francis on 2011-04-13
Got the same error again.

The command
sudo chmod 755 /home/user
fixed the boot up problem (type 755 not 700).

After that, applying the commands described in the 'how to' here:
[http://ubuntuforums.org/showthread.php?p=6208727](http://ubuntuforums.org/showthread.php?p=6208727)
fixed the ICEauthority problem

---

