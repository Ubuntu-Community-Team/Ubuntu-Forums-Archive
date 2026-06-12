---
title: "A few questions/problems..."
date: 2006-06-05
forum: General Help
---

### Post by dignick on 2006-06-05
Ok, a few questions/problems, each unrelated to each other.  I should have probably done seperate threads but I'd probably have forgotten what I was going to ask and filled half a page in threads.

I'm using dapper under VMWare.  All hardware is set up great.
1. Whenever I try to install a set of packages, the last one always fails.  It only fails on the very last package though.  If I press no, and try it again, it downloads the last package and works.

2. Sometimes when I click the menus in the panel, it acts like they have no space to open fully even though they do, ie I get an arrow to scroll down the menu.  If I reopen the menu, it's fine.

3. What is the linux equivalent of the windows Shared documents?

4. How can I duplicate a user?

5. Is there anyway I can copy all my user preferences to all users, or create a default user with my profile?  (in windows I can do this by copying my user profile into the default user profile, so when a new user logs in it copys that profile as thier own)

6. Logon sounds skip.  Is there anyway to fix this?

7. I'm using a M$ multimedia keyboard 1.0A.  Most keys and special keys work fine (very well done as there was no extra work required), however it appears print screen does not (I'm expecting a save image dialog).  Any ideas?

8. I have to click drop down menus in firefox 3 times before they work.  This could be because I have installed prettywidgets, but if not, is there a fix?

9. Is there a way I can make a file rename when I click on the filename like in windows?

I think thats it.

Now I've got the problems out the way, I would like to commend everyone who develops Ubuntu and linux in general.  I've been playing with Vista recently too, and I can honestly say IMHO it beats the s**t out of it.  If only vmware supported 3d graphics, then I could have some more fun with xgl :D 
Please keep it up everyone!

---

### Post by cleentrax on 2006-06-05
Replies to the ones on which I have opinions:

#6: Does your sound card skip on other sounds, or just the opening sound? What sound card are you using?

#9: I don't know of a key combo for this, though you could probably create one. I just use the "Rename" option in the R-Click menu. Alternatively, use the "menu" key on the keyboard, and then click "R."

---

### Post by dignick on 2006-06-06
6. No, other sounds don't skip.  I thought it might skip because it can't read the sound file fast enough or something, and I might be able to give it higher priority (because it gets a bit annoying).  I'm using the VMWare default soundcard, In device manager under audioPCI it says the oem product is a 'creative sound blaster AudioPCI64v,' Vendor is 'Esoniq' and Product is ES1371.

I may have fixed that problem though now by changing the VMWare settings from 'use default sound adapter' to specifying my actual sound adapter.  Logon sound has not skipped yet.

9. I was wondering if there was actually something that would enable clicking on the filename to rename, but it doesn't matter, its just an extra click away.

Thanks for helping.  Anyone else?

---

### Post by ifokkema on 2006-06-06
Hi,

[QUOTE=dignick]1. Whenever I try to install a set of packages, the last one always fails.  It only fails on the very last package though.  If I press no, and try it again, it downloads the last package and works.[/QUOTE]
Could you elaborate on 'fails': the download or the install? What's the error message?

[QUOTE=dignick]3. What is the linux equivalent of the windows Shared documents?[/QUOTE]
You don't share documents over the network by default. You can use Samba to share your linux files with the Windows host.

[QUOTE=dignick]4. How can I duplicate a user?[/QUOTE]
To my knowledge, there is no automated way. Copying the home directory and creating a new user should do the same, though.

```
sudo cp -pr /home/original_user /home/new_user_name
sudo adduser new_user_name
<follow the instructions on the screen>
sudo chown -R new_user_name:new_user_name /home/new_user_name
```

[QUOTE=dignick]5. Is there anyway I can copy all my user preferences to all users, or create a default user with my profile?  (in windows I can do this by copying my user profile into the default user profile, so when a new user logs in it copys that profile as thier own)[/QUOTE]
To my knowledge, default settings reside in /etc/skel

[QUOTE=dignick]7. I'm using a M$ multimedia keyboard 1.0A.  Most keys and special keys work fine (very well done as there was no extra work required), however it appears print screen does not (I'm expecting a save image dialog).  Any ideas?[/QUOTE]
Sounds to me you still need to configure the key bindings to the screenshot utility. There is a key bidings program in your menu, but I'm currently behind Breezy. There, it's at System => Preferences => Keyboard shotcuts. There's a "Take a screenshot" option.

[QUOTE=dignick]9. Is there a way I can make a file rename when I click on the filename like in windows?[/QUOTE]
Use the F2 key.

Happy Ubuntu-ing!

Ivo

---

### Post by dignick on 2006-06-08
Ok, errors as follows (this was on todays software update **while downloading**)

> 
Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?

[no]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.7.4-1ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.7.4-1ubuntu3.1_i386.deb)
  Error reading from server. Remote end closed connection 

That was the last package, the first downloaded fine.  If it helps in any way, I'm using NAT through VMWare.


I didn't mean sharing a folder over the network, I meant sharing a folder between users where every user has full permissions for the folder.  If one does not exist as default, how can I create one and where should it be?

Keyboard shortcuts is still in the same place.  However, even though I have now assigned print screen, it still doesn't work!  Everything else I assigned does.

Thanks a lot for the advice, everything else (excluding the user bits which I havn't tried yet) worked!

---

### Post by ifokkema on 2006-06-08
> **dignick]Ok, errors as follows (this was on todays software update **while downloading**)

That was the last package, the first downloaded fine.  If it helps in any way, I'm using NAT through VMWare.[/QUOTE]
Ok... I haven't had any updates on Dapper yet, and I haven't installed packages on it using the GUI (I always use the console). I am wondering if this also happens when upgrading through the console.

Next time it offers an upgrade, or next time you want to install stuff, try using the command line and see if that does work:
```
sudo apt-get update said:**
> I didn't mean sharing a folder over the network, I meant sharing a folder between users where every user has full permissions for the folder.  If one does not exist as default, how can I create one and where should it be?
Ah, sorry for the misunderstanding.

The easiest way to do this, is by creating a new folder in / and making it world writable. Every user can then add files to this folder, and edit other people's files.
```
sudo mkdir /share
sudo chmod 777 /share
```

[QUOTE=dignick]Keyboard shortcuts is still in the same place.  However, even though I have now assigned print screen, it still doesn't work!  Everything else I assigned does.[/QUOTE]
Hm.... I wonder if Windows catches that key before passing it on to VMware. On the other hand, if you can set the key, you must be able to use it, too. What happens if you assign something different to it, such as <Ctrl><Print> or <Ctrl>~ or something?

[QUOTE=dignick]Thanks a lot for the advice, everything else (excluding the user bits which I havn't tried yet) worked![/QUOTE]
Glad to be of help :)

---

### Post by dignick on 2006-06-10
The first two update packages worked, and then...
> Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main binutils-static 2.16.1cvs20060117-1ubuntu2.1 [536kB]
Errhttp://security.ubuntu.com dapper-security/main binutils-static 2.16.1cvs20060117-1ubuntu2.1
  Error reading from server. Remote end closed connection
Get: 4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main firefox-gnome-support 1.5.dfsg+1.5.0.4-0ubuntu6.06 [74.3kB]
Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libnspr4 2:1.firefox1.5.dfsg+1.5.0.4-0ubuntu6.06 [146kB]
Errhttp://security.ubuntu.com dapper-security/main libnspr4 2:1.firefox1.5.dfsg+1.5.0.4-0ubuntu6.06
  Error reading from server. Remote end closed connection
Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libnss3 2:1.firefox1.5.dfsg+1.5.0.4-0ubuntu6.06 [669kB]
Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main firefox 1.5.dfsg+1.5.0.4-0ubuntu6.06 [7911kB]
Errhttp://security.ubuntu.com dapper-security/main firefox 1.5.dfsg+1.5.0.4-0ubuntu6.06
  Error reading from server. Remote end closed connection
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main gdm 2.14.6-0ubuntu2.1 [1714kB]
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main libpq4 8.1.4-0ubuntu1 [199kB]
Errhttp://security.ubuntu.com dapper-security/main libpq4 8.1.4-0ubuntu1
  Error reading from server. Remote end closed connection
Fetched 13.1MB in 2m2s (107kB/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-static_2.16.1cvs20060117-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-static_2.16.1cvs20060117-1ubuntu2.1_i386.deb)  Error reading from server. Remote end closed connection
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.4-0ubuntu6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.5.dfsg+1.5.0.4-0ubuntu6.06_i386.deb)  Error reading from server. Remote end closed connection
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.4-0ubuntu6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.5.dfsg+1.5.0.4-0ubuntu6.06_i386.deb)  Error reading from server. Remote end closed connection
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq4_8.1.4-0ubuntu1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/postgresql-8.1/libpq4_8.1.4-0ubuntu1_i386.deb)  Error reading from server. Remote end closed connection
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
After running it a couple more times, it got all the packages.

Print screen works with a different key, so I'm guessing you were right about windows somehow catching it or something...it did cross my mind but I wasnt inventive enough to try another key :D   I'll just leave it like that, and try the real button next time i use a live cd.

Sounds still skip btw.  Not when playing music, well not often, but on logon and also the hardware test in device manager.

Putting files in /etc/skel for the default user works great!  Shared folder works too.

Any idea about the menu problem I have where it puts arrows top and bottom?

Thanks.

---

### Post by ifokkema on 2006-06-10
[QUOTE=dignick]The first two update packages worked, and then...

After running it a couple more times, it got all the packages.[/QUOTE]
Where the first two packages taken from a different server, or also from security.ubuntu.com?

[QUOTE=dignick]Sounds still skip btw.  Not when playing music, well not often, but on logon and also the hardware test in device manager.[/QUOTE]
How's your CPU when this happens? You can install a system monitor on your panel, so you can monitor your CPU usage, Disk I/O, Load etc. Maybe it's because your PC is too busy doing things when your sound skips?

[QUOTE=dignick]Putting files in /etc/skel for the default user works great!  Shared folder works too.[/QUOTE]
Good to know you got it to work :)

[QUOTE=dignick]Any idea about the menu problem I have where it puts arrows top and bottom?[/QUOTE]
For that, I'm afraid I can't help you. It might be VMware related. I've never seen it or heard of other users having this problem. I could imagine it has something to do with Ubuntu not getting the screen resolution right or something.

---

### Post by dignick on 2006-06-14
A few packages have failed from archive.ubuntu.com (85.133.25.7 80), I havn't installed enough things to see if it just fails from ubuntu servers or not.

My pc probably is too busy but I was wondering if I could run the sounds at a higher priority or something - windows sounds don't skip when I log in, even though it is busy.  It doesn't really annoy me at the moment, but I can imagine it would after a while as the skipping can be quite severe.  I could just turn the sounds off...but I'm a bit of a perfectionist :p 

Almost all problems sorted! :D

---

