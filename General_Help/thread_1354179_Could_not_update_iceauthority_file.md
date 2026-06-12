---
title: "Could not update iceauthority file"
date: 2009-12-13
forum: General Help
---

### Post by boomslang20117 on 2009-12-13
hi I'm running on ubuntu 9.10. After a restart I got the error Could not update iceauthority file /home/dntel/.iceauthority

followed by there is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256

and then nautilus could not create the following required folders: /home/dntel/desktop, /home/dntel/.nautilus. Before running nautilus, please create these folders, or set permissions such that nautilus can create them.

---

### Post by boomslang20117 on 2009-12-13
Btw chown doesn't work as the message was no such file or directory

---

### Post by Craig Bakkala on 2009-12-13
I too have just run into the exact same problem and cannot get ubuntu to boot!
 
I have already tried the following:
sudo chown craig:craig /home/craig/.ICEauthority
sudo chmod 600 /home/craig/.ICEauthority
 
and get the following error:
cannot access '/home/craig/.ICEauthority' :no such file or directory

---

### Post by kamikaze.tnt on 2009-12-13
As I've figured out, the problem here is the automatic login, so you just have to disable it.

Try this:
from root directory: sudo vi /etc/gmd/custom.conf
there you should see
```
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=mazlik
AutomaticLogin=mazlik
TimedLoginDelay=30
```
and just change the "true" in the second row to "false"

this has just done the trick for me.. been struggling with this for about 2,5 hours..

---

### Post by Craig Bakkala on 2009-12-13
> **kamikaze.tnt said:**
> As I've figured out, the problem here is the automatic login, so you just have to disable it.
 
Try this:
from root directory: sudo vi /etc/gmd/custom.conf
there you should see
```
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=mazlik
AutomaticLogin=mazlik
TimedLoginDelay=30
```
and just change the "true" in the second row to "false"
 
this has just done the trick for me.. been struggling with this for about 2,5 hours..
 
OK, I have tried this however after entering sudo vi /ect/gmd/custom.conf  I get a screen with blue tildes all down the left side of the screen and "/ect/gdm/custom.conf" [New DIRECTORY] at the bottom.  

notice that I changed the gdm. I believe that gmd may have been a typo.  Please correct me if I'm wrong as I am a newbe and only using Ubuntu for a few days now.

I tend to agree that this has to do with the automatic login because I had just activated it prior to restarting.

---

### Post by boomslang20117 on 2009-12-14
Yes that's what I got too

~
~
~
"/etc/gmc/custom.conf [new directory]

---

### Post by Craig Bakkala on 2009-12-14
Boomslang...   I don't have enough time to post it right now but I did find a way to fix it just this morning.  I promise to post what I did as soon as I get home from work this afternoon.

---

### Post by boomslang20117 on 2009-12-14
Thanks :) that would be of great help

---

### Post by Craig Bakkala on 2009-12-14
Ok.. here is what I did.

boot into recovery mode

drop to root shell prompt

type:
  login

you will get this prompt:
  <name>-desktop login:     enter you user account name
  password:    enter your password  (NOTE: you will not see the characters that you type here)

at the next prompt type:
  startx

This will log you into your normal user account.  The Login Screen menu item will be accessable at this point but, it will not work.

in a terminal window enter this command:
  sudo gedit

enter your password when prompted.  This will open gedit with root permissions.

in gedit click open then under file system browse to /ect/gdm/custom.conf

you should see a file that looks like this:  

[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=craig
AutomaticLogin=craig
TimedLoginDelay=30

simply change AutomaticLoginEnable=true to =false

shutdown as normal.  this will drop you back into the recovery mode.  Close out from that and restart.  From there everything should be good.

Please let me know if this works for you too.

---

### Post by boomslang20117 on 2009-12-14
I manage to edit it but sadly it didn't work for me. I still get the same error even though I'm manually logging in now

---

### Post by boomslang20117 on 2009-12-14
Does anyone knows what's causing the problem? If not I guess I'll just have to do a fresh install. Anyway I'd I were to do that is there any precaution I should take to prevent such a problem again?

---

### Post by Craig Bakkala on 2009-12-14
ok.. 2 questions then..

did the gedit window header say "read only"?  It shold not.

you did save the file after editing right??  sorry, have to ask.

---

### Post by boomslang20117 on 2009-12-14
No its not read only and yes I did save it. Anyway I manage it to edit by running ubuntu from the USB drive which I use to install my ubuntu from because I can't seem to get into recovery mode after holding shift. It did get into the menu where I have to choose drop to root shell prompt and when I wanted to press the down arrow to select the option the weiss starts to jumble up and pixelled up.

---

### Post by Craig Bakkala on 2009-12-14
ok.  booting it from the usb drive is probably going to be the problem there.  by booting it from other than the harddrive, you cant gain ownership of the file to save an edit.


try following the directions on this page to see if you cant get into recovery mode

[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

---

### Post by boomslang20117 on 2009-12-15
But it did manage to work anyway cu the end result is the same no? As in the end I didanafe roanually log in but I sill got the same problem

---

### Post by boomslang20117 on 2009-12-15
Anyway what I did was Boot into the USB drive and typed sudo gedit. Then I went to file browser and navigate to /etc/gdm and drag custom.conf into gedit. From there I edited the file and did manage to save it.

---

### Post by KarmaJones on 2009-12-17
I have the same issues, but I can't drop to root shell prompt. I can't access the GRUB menu on start-up even when I press escape.

---

### Post by TheLunticIsInMyHead on 2009-12-24
I have the same problem but my automatic login is already set to false, any ideas what could be causing this then?

Note: If I just close the dialog box the system works as normal, and I have been using 9.10 for about a week before this problem started!

---

### Post by TheLunticIsInMyHead on 2009-12-28
Okay - I also had a problem with Amarok not opening correctly - there was an error that it could not read the DCOPserver_username_0 file.

I searched the forum for this, and it says that to fix it just delete the /home/user/.DCOP_user_0 file, you may also need to delete /home/user/.ICE_authority

It said it was safe to do this as KDE makes them on login, rm'd them and now both problems are fixed.
Mike

---

### Post by jigsaw. on 2009-12-28
Hi, new to all this, learning quick but still new, so bear with me! I've got two accounts - root and my user account - I'm having trouble even working out which accounts have which privileges. Anywho I changed some passwords around last night and all was working great, both accounts would log in. Then I switched off; when I rebooted about an hour later root would log in fine, my user account displays the error messages detailed in the first post of the thread. Given I've spent a huge amount of time in the past few weeks pimping my user account to be awesome, and my root account is still in default settings as far as I'm aware, I'd really like to be able to get back into my user account.

I tried sudo vi, got the same problem everyone else has. So I tried thing with custom.conf. Everyone else seems to have at least found the custom.conf file, I did not. My recovery mode + root shell thingy booted me automatically into the root account, which I can already access fine. I went to the directory suggested and there was no custom.conf file. I think my user account has permissions that my root account does not - maybe I can only access custom.conf in my user account - how do I get onto the user account? I have been able to get onto tty1-6, but not tty7. Maybe there is no custom.conf file and I'm truly buggered! I do not know. Can anyone help?

Many thanks in advance.

EDIT: Tried again logging into user account in recovery mode. Held down shift, when I would have clicked on the root shell option I clicked on continue as normal and entered my user account details. I could still access tty1-6 but not tty7. I'm not sure if this was truly recovery mode or if it was the normal boot - there seemed no difference. In either case, I navigated to the gdm folder as per norm and it displayed the same contents - no custom.conf anywhere to be seen. I just get:

failsafeBlacklist
failsafeDexconf
Xinit
XServer
gdm.schemas
Init
PostLogin
PostSession
PreSession
XSession

And when I do ls -a (which I seem to vaguely remember is meant to show hidden files?) I also get . and .. and nothing else.

---

### Post by jeepGuy on 2010-01-02
These messages can by caused by improper file ownership and permission settings. You need to get to a shell with root privileges to make changes, so you may have to boot from a live disk. 

1 - Check that the /home directory has the right ownership (root) and permissions (755). Mine looks like this:

jeepguy@laptop:~$  ls -l /
[snip]
drwxr-xr-x   4 root root  4096 2008-08-03 16:40 home
[snip]

2 - Check that your home directory has the right ownership (you!) and permissions (755). Again, mine looks like this:

jeepguy@laptop:~$  ls -l /home
drwxr-xr-x 132 jeepguy jeepguy 12288 2010-01-02 12:20 jeepguy

3 - Then check that the .ICEauthority file (and the other files in your home directory) are owned by you. My .ICEauthority file has permissions set to 600.

Good luck!

---

### Post by suresh babu t on 2010-01-26
DEAR SIR,
              thank you very much for your kind guidence. it worked with me very fine & i was able to re boot my laptop back to normal. thank you very much once again.

---

### Post by jlb.think on 2010-01-27
> **jigsaw. said:**
> Hi, new to all this, learning quick but still new, so bear with me! I've got two accounts - root and my user account - I'm having trouble even working out which accounts have which privileges. Anywho I changed some passwords around last night and all was working great, both accounts would log in. Then I switched off; when I rebooted about an hour later root would log in fine, my user account displays the error messages detailed in the first post of the thread. Given I've spent a huge amount of time in the past few weeks pimping my user account to be awesome, and my root account is still in default settings as far as I'm aware, I'd really like to be able to get back into my user account.

I tried sudo vi, got the same problem everyone else has. So I tried thing with custom.conf. Everyone else seems to have at least found the custom.conf file, I did not. My recovery mode + root shell thingy booted me automatically into the root account, which I can already access fine. I went to the directory suggested and there was no custom.conf file. I think my user account has permissions that my root account does not - maybe I can only access custom.conf in my user account - how do I get onto the user account? I have been able to get onto tty1-6, but not tty7. Maybe there is no custom.conf file and I'm truly buggered! I do not know. Can anyone help?

Many thanks in advance.

EDIT: Tried again logging into user account in recovery mode. Held down shift, when I would have clicked on the root shell option I clicked on continue as normal and entered my user account details. I could still access tty1-6 but not tty7. I'm not sure if this was truly recovery mode or if it was the normal boot - there seemed no difference. In either case, I navigated to the gdm folder as per norm and it displayed the same contents - no custom.conf anywhere to be seen. I just get:

failsafeBlacklist
failsafeDexconf
Xinit
XServer
gdm.schemas
Init
PostLogin
PostSession
PreSession
XSession

And when I do ls -a (which I seem to vaguely remember is meant to show hidden files?) I also get . and .. and nothing else.


I had the same problem and I figured out the fix.  Start Ubuntu as normal and when you are prompted to login to the desktop do it.  Wait until you see your error message, and then hit CTRL-ALT-F1

Login to the text shell by typing your username and password, if your new password doesn't work use your old.

Type "ls"

You should see two files, README.txt and ecrypt-fs-mount or similar.  Run the ecrypt-fs file.  It will prompt you for a password, try the new password you set and the old password, if you have a separate root password try that too until one works.

Now run the "passwd" command, it will prompt you for your old password which is the same one you used to login to the text prompt, and it wants a new password.  Your new password should be whatever password worked to get ecrypt-fs* to work.

After this reboot your system and everything should be normal.  The problem lies in how Ubuntu handles the root password by not really having one, but using your user password.  When you changed your password it fscked up how the whole root passowrd as your password relationship works.

When I figure out more I will file a bug-report if one has not already been filed.

---

### Post by Flos Headford on 2010-04-08
This worked for me:
Use a Ubuntu Live CD to boot up, and choose a command-line (shell) option.
With this, set your $HOME directory (/home/username) permissions to something appropriate (see post #21; I used 755) and make sure all directories can be listed with the "ls" command. Then remove nautilus with ```
sudo apt-get remove nautilus
``` and delete the .ICEauthority entry in $HOME, and possibly in /var/lib/gdm. Then reboot with ```
sudo shutdown -r now
``` When you choose the same option on boot-up, from the command line you can use ```
sudo apt-get install nautilus
sudo shutdown -r now
``` and retrieve the CD a bit smartish. I do hope you get a clean straight boot and login, as I did!
With thanks to all who helped me,
Phil

---

### Post by wasabishot on 2010-04-18
Hey guys,
this morning i tried to install WINE, and since then having the error messege mentioned above. furthermore, my audio settings are impossible to access, means i cannot even listen to music, surprisingly, the audio in skype works just fine.
tried some things, including deleting the .ICEathority files. nothing helps.

I'm doing the recomended in post #21 and the result:
```

bishgatzu@bishgatzu-laptop:~$ ls
Desktop    Downloads         Music     Templates
dic.txt    examples.desktop  Pictures  veetle-0.9.17-linux-install.sh
Documents  libflashsupport   Public    Videos
bishgatzu@bishgatzu-laptop:~$ ls -l /
total 92
drwxr-xr-x   2 root root  4096 2010-02-22 20:27 bin
drwxr-xr-x   3 root root  4096 2010-03-17 11:49 boot
lrwxrwxrwx   1 root root    11 2010-02-22 17:32 cdrom -> media/cdrom
drwxr-xr-x  16 root root  3800 2010-04-18 19:22 dev
drwxr-xr-x 137 root root 12288 2010-04-18 19:24 etc
drwxr-xr-x   3 root root  4096 2010-02-22 17:43 home
lrwxrwxrwx   1 root root    33 2010-03-05 09:09 initrd.img -> boot/initrd.img-2.6.31-20-generic
lrwxrwxrwx   1 root root    33 2010-02-22 20:28 initrd.img.old -> boot/initrd.img-2.6.31-19-generic
drwxr-xr-x  18 root root 12288 2010-04-18 11:25 lib
drwx------   2 root root 16384 2010-02-22 17:31 lost+found
drwxr-xr-x   6 root root  4096 2010-04-18 19:23 media
drwxr-xr-x   2 root root  4096 2009-10-20 02:04 mnt
drwxr-xr-x   3 root root  4096 2010-04-11 17:24 opt
dr-xr-xr-x 164 root root     0 2010-04-18 19:22 proc
drwx------  19 root root  4096 2010-04-18 12:23 root
drwxr-xr-x   2 root root  4096 2010-04-16 09:38 sbin
drwxr-xr-x   2 root root  4096 2009-10-20 01:05 selinux
drwxr-xr-x   2 root root  4096 2009-10-28 21:55 srv
drwxr-xr-x  12 root root     0 2010-04-18 19:22 sys
drwxrwxrwt  10 root root  4096 2010-04-18 19:32 tmp
drwxr-xr-x  12 root root  4096 2010-02-22 20:46 usr
drwxr-xr-x  15 root root  4096 2009-10-28 22:02 var
lrwxrwxrwx   1 root root    30 2010-03-05 09:09 vmlinuz -> boot/vmlinuz-2.6.31-20-generic
lrwxrwxrwx   1 root root    30 2010-02-22 20:28 vmlinuz.old -> boot/vmlinuz-2.6.31-19-generic
bishgatzu@bishgatzu-laptop:~$ ls -l /home
total 4
drwxr-xr-x 43 1016 1016 4096 2010-04-18 19:21 bishgatzu
```

how do i go on?
 please help...

---

### Post by wasabishot on 2010-04-19
Hello guys

i published this messege in the other thread, but i´ve been working on this for many hours and getting desperate.

so its like that
i had this error messege mentioned on top, then got to have the other error messeges related to nautilus and all that.
then i tried to do what said above: entered the live cd. tried to figure out how to open terminal from there, couldn't, so booted from recovery, did all the chown and chmod, deleted bot .ICEauthority files, removed nautilus , restarted, installed nautilus, restarted.

ANNND now it's WORSEEEE
i get the login screen, try to log in, it seems woking, but then going back to the login screen... and so on................

now im working thanks to the ubuntu tryout of the live cd....
without any ability to access my desktop

please help!!!!!!!!!

---

### Post by mjcritchie on 2010-04-20
I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:

> sudo chown -R user:user /home/user/.*

Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org

---

### Post by chiwi on 2010-06-06
Hey, I accidentaly removed the ICEauthority file. Do you know how can i regenerate it ? 

THanks!

Chiwi

---

### Post by Jimmy the Geek on 2010-06-10
Thanks for the tip, mjcritchie! This worked perfectly for me on UUE 2.5.

---

### Post by Susslarn on 2010-12-18
Hi Guys!
 
I had the same problem and stumbled on a solution. I don't know if it's going to help you but it worked for me.
 
My nautilus didn't want to load because I checked the box "Dont ask for password on login" (or something like that).
 
• When the loginscreen shows, press CTRL+ALT+F3.
 
• Login with your username and password.
 
• Press CTRL+ALT+F7. You should now come back to the login screen and it should say that you are logged in.
Now, simply click your name and voila!
 
• Now nautilus loaded for me, and I could manage users and uncheck the "don't ask for password"-thingy.
 
Hope it helps.

---

### Post by Hoopz on 2010-12-18
Here's my experience with these errors.  I created a user using the command useradd [http://ubuntuforums.org/showthread.php?t=1587015](http://ubuntuforums.org/showthread.php?t=1587015)

---

