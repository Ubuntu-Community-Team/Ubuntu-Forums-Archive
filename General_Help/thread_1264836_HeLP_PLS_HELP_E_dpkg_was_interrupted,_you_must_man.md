---
title: "HeLP PLS HELP E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -"
date: 2009-09-12
forum: General Help
---

### Post by EvilCastillo on 2009-09-12
hey guys i have been getting the problem now for almost a week, everytime i tryed to install something or remove something today i saw that i needed alot of uopdates so i tryed and i am getting this message E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

and when i put it on google it gives me steps that dont work i tryed everything to make this work my last step is to unstall the whole os and start over again but before i do that i would like to know what should i do thanks

---

### Post by NoaHall on 2009-09-12
ctrl + alt + F1 

then run "sudo dpkg --configure -a"

---

### Post by P4man on 2009-09-12
well. dpkg was interrupted, so you must manually run ```
sudo dpkg --configure -a
```

Im honestly not sure how they could have made that error any clearer :confused:

In case you're wondering what happened: dpkg got interrupted. Not to be a jerk, but really. Maybe you rebooted before it finished, laptop battery drained or something.

If you don't know how to run that command, just open a terminal (applications > accessories > terminal) and type or copy paste it there. If ubuntu is not booting in to a graphical environemnt, then just type it at the terminal you should have in front of you.

---

### Post by EvilCastillo on 2009-09-12
alright i tryed that but still the same thing when i go back to the os anything else i should do

---

### Post by P4man on 2009-09-12
can you copy paste the output of that command here?

---

### Post by EvilCastillo on 2009-09-12
ok ok so now it asked me for a passowrd and i entered it 

dpkg: need an action option 

what can i do ??

---

### Post by P4man on 2009-09-12
you have to enter the *entire* command as typed above. one line. Copy paste it to avoid typing errors (to paste, use shift+control+V).

---

### Post by EvilCastillo on 2009-09-12
ohued@ohued-laptop:~$ sudo dpkg --configure -a
[sudo] password for ohued: 
dpkg: parse error, in file `/var/lib/dpkg/updates/0005' near line 11 package `abrowser':
 file details field `Filename' not allowed in status file
ohued@ohued-laptop:~$ 
...............................................................................................................................

thats what it says on the OS, should i screen shot this for ya ? i am new to the game thanks

---

### Post by P4man on 2009-09-12
Looks like something got corrupted there. You can probably fix it with this:

```
sudo dpkg --clear-avail && sudo apt-get update
```

But id worry about your harddisk..

---

### Post by EvilCastillo on 2009-09-12
that's what my computer says any new idea's let me know thanks

---

### Post by EvilCastillo on 2009-09-12
hey i put that in and look what happen:


ohued@ohued-laptop:~$ sudo dpkg --clear-avail
[sudo] password for ohued: 
ohued@ohued-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty Release.gpg
Ign cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty/main Translation-en_US            
Ign cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty/multiverse Translation-en_US      
Ign cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty/restricted Translation-en_US      
Ign cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty Release                           
Ign cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty/main Packages                     
Ign cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty/multiverse Packages               
Ign cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty/restricted Packages               
Ign cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty/main Packages                     
Ign cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty/multiverse Packages               
Ign cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty/restricted Packages               
Err cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty/main Packages                     
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty/multiverse Packages               
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421) jaunty/restricted Packages               
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                                                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources
W: Failed to fetch cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)/dists/jaunty/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

what should i do should i reinstall the whole OS again ??

---

### Post by P4man on 2009-09-12
not just yet. Now that you cleared the cache, you can try again:

```
sudo dpkg --configure -a
```

---

### Post by EvilCastillo on 2009-09-12
ohued@ohued-laptop:~$ sudo dpkg --clear-avail
ohued@ohued-laptop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0005' near line 11 package `abrowser':
 file details field `Filename' not allowed 

thats what happen again

---

### Post by EvilCastillo on 2009-09-12
Again I am going to reinstall the OS again on my net book but thanks alot for the info I hope this does not happpen again =\ thanks tho if anynew info hit me up

---

### Post by MaxIBoy on 2009-09-13
I was going to suggest moving that /var/lib/updates0005 file somewhere else (not deleting it!) so that dpkg can't find it. If that doesn't work, I would suggest editing the file, going to line 11, and removing the 'Filename' field (KEEPING A COPY OF THE ORIGINAL!!!)

I often find that in errors with dpkg, you can remove the file or line of a file which is tripping it up and nothing bad will happen.

---

### Post by EvilCastillo on 2009-09-13
Well when I try to edit the file it tells me that I don't have permission to do so is there a way I could edit the file or move it I am new to this so all helps are welcome thanks again

---

### Post by P4man on 2009-09-13
> **EvilCastillo said:**
> Well when I try to edit the file it tells me that I don't have permission to do so is there a way I could edit the file or move it I am new to this so all helps are welcome thanks again

If you want to do so with the filemanager (nautilus) you can do one of two things:

Either install a little script so you get a right click, open ad admin option:

sudo apt-.. ahm, never mind, you can"t install stuff lol.

Ok, open a terminal and type

```
gksudo nautilus
```

That opens a file browser with root (admin) rights, and should let you move or edit those files.

---

