---
title: "reset user to admin and removed password to login now i got no desktop"
date: 2011-02-24
forum: General Help
---

### Post by jdchurchill on 2011-02-24
hello forum-
i thought it would be easier if i removed the password to login, but now i basicly have a computer that i can't use.  yesterday i changed the main user to admin and ticked the box so login does not require password.  (i have msi board athalon quadcore chip 1tb hdd) now i get error messages on login that nautilus cannot generate the desktop.  i am freaking out what should i do?

---

### Post by dino99 on 2011-02-24
you are ready for a new installation :(

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by jdchurchill on 2011-02-24
really?  the link you give is for a duel boot 

there is no way to restore to previous?  or just use terminal cuz i get a message about something generating a password and the terminal opens for this action so i can maybe do something there?

also if i go through with the directions in your link will i be able to find data currently in my file system?

---

### Post by jdchurchill on 2011-02-24
so i guess i will update later with specifics of error messages (there are three in total) and hopefully somebody can help me get my system back to working condition

---

### Post by jdchurchill on 2011-02-24
so can't i use the terminal to add a new user, and then get to the desktop and alter the original user?

---

### Post by jdchurchill on 2011-02-24
feel free to lend me yr opinions 

IS THERE ANYBODY OUT THERE?

---

### Post by Krytarik on 2011-02-24
Imo no need to immediately re-install!

It seems like this has happened to you:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Check the ownership of the file ".ICEauthority" in your home directory:
```
ls -al /home/USER/.ICEauthority
```If it is indeed root change it back:
```
sudo chown USER.USER /home/USER/.ICEauthority
```Then reboot/relogin.

If there are any more error messages after doing this, post them.

---

### Post by jdchurchill on 2011-02-24
thanks krytarik i will try that

---

### Post by jdchurchill on 2011-02-24
ok just for posterity or whatever future help for whomever the errors i received upon trying to login (i also changed the name of the user that i set to admin and removed the password for login thing) 

could not update ICEauthority file /home/double-j/.ICEauthority

There is a problem with the configuration server.  (/usr/lib/libconfig2-4/gconf-sanity-check-2 exited with status 256)

Nautilus could not create the following required folders: /home/double-j/Desktop,/home/double-j/.nautilus  Before running Nautilus, please create these folders or set permissions such that Nautilus can create them

---

### Post by jdchurchill on 2011-02-24
ok this is also wierd when i ctrl-alt-F1 or F2-6 i get this login thing 
both old username and new user name don't work with the password i used to have

---

### Post by Krytarik on 2011-02-24
Did you check the .ICEauthority file(s) then?
If not, due to the apparent login issues, boot into recovery mode, then choose "root shell prompt" and check/fix it from there. This way any commands without "sudo".

---

### Post by Krytarik on 2011-02-24
> **jdchurchill said:**
> ok just for posterity or whatever future help for whomever the errors i received upon trying to login (i also changed the name of the user that i set to admin and removed the password for login thing) 

I don't get this one!?

---

### Post by jdchurchill on 2011-02-24
oh i meant to say that i changed the username at the time that i changed the password requirement and gave administrator priveledges

---

### Post by Krytarik on 2011-02-24
What do you mean by "changed the name"? Did you really change the user/loginname (which isn't possible), or the name of its directory?

---

### Post by jdchurchill on 2011-02-25
dude i don't know i thought i changed the username cuz it used to be my name and this computer is for me AND my fiance so i tried to change the name to both of our first names wtih & between.  and then i ticked the box which makes the user admin.  

anyways this is also not good dig
i can get into recovery mode and i try to change the password and neither my old or  new username are found user 'jdchurchill' does not exist

---

### Post by Krytarik on 2011-02-25
> **jdchurchill said:**
> dude i don't know i thought i changed the username cuz it used to be my name and this computer is for me AND my fiance so i tried to change the name to both of our first names wtih & between.  and then i ticked the box which makes the user admin.  
Ok, I guess you only changed the "long name".
> **jdchurchill said:**
> anyways this is also not good dig
i can get into recovery mode and i try to change the password and neither my old or  new username are found user 'jdchurchill' does not exist
This is getting weird, does the users directory still exist then?

---

### Post by jdchurchill on 2011-02-25
how do i check the users directory?

i tried my solution from above 
adding a new user and with that i can log in and get to the desktop but none of my documents or music is in there.  so that idea didn't work

but now in the recovery console ls /home returns my computer name and the new username that i just created.  it's like the old user account disappeared through the action i took earlier when i changed the user name, priveledges and password requirements.  i am not happy but am learning about commands and recovery consoles etc

---

### Post by Krytarik on 2011-02-25
There is no "computer name" in the directory listing of /home, I suppose that is your old user?

With the actions you have done you wouldn't have deleted the home directory of your user.

---

### Post by jdchurchill on 2011-02-25
so this is wierd now i have ascertained that what i was calling computer name (which is what i named my computer) has become a login.  ok let me take you through what happens:
restart machine (ctrl-alt-delete)
boots to login screen (which now has two users one the old which i have renamed and what i renamed it is displayed how i typed it and the new new user i created in the recovery console)

if i click the old user i get the error messages listed above: the one abt ICEauthority, the one abt the configuration server, and the one about nautilus couldn't create nautilus.  then it's just a background pink screen and does nothing.

then i ctrl-alt-F1 and i get 
Ubuntu 10.10 double-j tty1
double-j login:

which if i put it either the new user/new passwd i just made in the recovery console or double-j with my old passwd will get me in

then if i ls /home
no matter which is logged in i get 
double-j  newuser

this is bad right?

---

### Post by jdchurchill on 2011-02-25
so i finally checked what you told me earlier i put
ls -al /home/double-j/.ICEauthority            and i get
-rw------- 1 double-j double-j 15974 2011-02-23 17:41 /home/double-j/ICE.authority

note double-j is the name of my computer and how in the previous post how i figured out it was also the login somehow thus making it a USER???

either way the newuser i made in the recovery console i told you about earlier goes like this 

i type
ls -al /home/newuser/.ICEauthority           and i get
-rw------- 1 newuser newuser 326 2011-02-24 23:07 /home/newyser/.ICEauthority


also i tried doing usermod double-j        and i get
usermod: no flags given

dude plz tell me i can fix this

---

### Post by jdchurchill on 2011-02-25
if i do 
ls home/double-j/Documents 
it shows me all the documents i have saved.
so all the data is there.  it just seems like there is no actual login
like i push the box with the old username and i get the error messages i listed and then when i ctrl-alt-F1 it still asks me to login

and from the command line interface i can see the files i have stored.  so it must just be something or other that i have to modify to get my desktop to come back, amirite??

but what is it?

---

### Post by jdchurchill on 2011-02-25
> **Krytarik said:**
> Imo no need to immediately re-install!

It seems like this has happened to you:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Check the ownership of the file ".ICEauthority" in your home directory:
```
ls -al /home/USER/.ICEauthority
```If it is indeed root change it back:
```
sudo chown USER.USER /home/USER/.ICEauthority
```Then reboot/relogin.

If there are any more error messages after doing this, post them.

when i did sudo chown double-j.double-j /home/double-j/.ICEauthority
there was no indication that anything happened
i reboot and try login and get the same 3 error messages and the same pink background screen but no desktop
also when ctrl-alt-F1 it still wants login which i can but why wont my desktop go??

---

### Post by Krytarik on 2011-02-25
> **jdchurchill said:**
> 
then if i ls /home
no matter which is logged in i get 
double-j  newuser

this is bad right?
Sorry, I should have mentioned that I was about to leave.

The output is perfectly right, "double-j" is your old user, "newuser" is your new user.

The permissions/ownership of .ICEauthority are also correct.

I did a web/forums search on what else could be the reason for the error:
Please try renaming those file, then try to login again:
```
sudo mv /home/double-j/.ICEauthority /home/double-j/.ICEauthority-backup
```

---

### Post by jdchurchill on 2011-02-25
what is supposed to happen when one successfully utilizes the command line terminal to change directories?  

i did sudo mv /home/double-j/.ICEauthority  /home/double-j/.ICEauthority-backup
then it asked me for [sudo] password so i entered the password then nothing happened

so i exit restart try to login and i get the same 3 errors and i think to myself that perhaps i didn't key in the password correctly so i repeat the process this time i get

mv: cannot stat '/home/double-j/.ICEauthority' : No such file or directory

gah!  yo i'm mad frustrated.  does this seem like i can fix?  if not can i still get at my files somehow and then reinstall?  

btw krytarik you are wonderful.  respect!

---

### Post by jdchurchill on 2011-02-25
i was thinking does it matter that when i get into the command line terminal
ctrl-alt-F1 it says there are updates?  how do i do the updates cuz maybe some of this bologna is related to that, eh?

---

### Post by Krytarik on 2011-02-25
Thanks! Please try the following, this will re-assign your home directory and all its subdirs to you:
```
sudo chown double-j.double-j -R /home/double-j
```You can upgrade your packages from the command line with these commands:
```
sudo apt-get update
sudo apt-get upgrade
```And yes, since you have apparently full access to your home directory, you can of course copy all your stuff out there, and re-install if necessary.

And you entered the password correctly, otherwise you would have got an error message, and there is no output if the given command is successful.

---

### Post by jdchurchill on 2011-02-25
so i did what you suggested
i got some error abt wallpaper not being able to move restarted login and get the same darned 3 error messages still no desktop just the pink bkgd.  ug
this is really quite a learning experience.  i am so confused about why this is happening and the apparent mismatch between the gui that is the desktop and the command line interface in that my desktop is just the background image from the login screen that pink whatever it is and then when i do ls command to show files i have stored i can see they are there.  

the computer functions as normal with my newuser except i can't see any of the old files.  frankly i don't care to restore the old user and desktop, if i could just move all the important files to the new user i would be happy.

---

### Post by Krytarik on 2011-02-25
To get access to your old files from the desktop:
- press Alt+F2
- enter "gksudo nautilus"

This gives you root-access to all files/dirs. Then you can copy your stuff over to the new user, make sure that the ownerships is those of your new user afterwards, you can use the earlier used command accordingly to change the ownerships of all files/dirs in your home directory after you copied all necessary files/dirs.

But please do one more thing: since you have complete desktop access with the new user, please post the entire output of
```
ls -al /home/double-j
```
Please use the code-tags therefore, the #-button in the editor.

---

### Post by jdchurchill on 2011-02-26
alright so dig this
just for a laugh i log in with newuser and check System>Adminitration>Users and Groups
and i changed the old user login name back to double-j and also reset the password prompt then i logged off newuser and logged in double-j and EVERYTHING is back to normal!  ha so now i don't have to move everything and i got my desktop back.  so thanks krytarik for all your help and i think we can close the book on this one.  word

---

### Post by Krytarik on 2011-02-26
So, this is quite weird. Though I don't believe it has something to do with the change of the username (" Full Name"), it seems that the suppression of the password query was indeed the culprit. I wish we had tried this earlier, but who minds of that?!

However, I'm glad that you're now "on" again. ;-)

Then please mark this thread as "solved", via "Thread Tools"

---

### Post by jdchurchill on 2011-02-27
aw man i spoke to soon.  the problem is back.

---

### Post by jdchurchill on 2011-02-27
> **Krytarik said:**
> To get access to your old files from the desktop:
- press Alt+F2
- enter "gksudo nautilus"

This gives you root-access to all files/dirs. Then you can copy your stuff over to the new user, make sure that the ownerships is those of your new user afterwards, you can use the earlier used command accordingly to change the ownerships of all files/dirs in your home directory after you copied all necessary files/dirs.

But please do one more thing: since you have complete desktop access with the new user, please post the entire output of
```
ls -al /home/double-j
```
Please use the code-tags therefore, the #-button in the editor.

total 12
dr-x------ 3 double-j double-j 4096 2011-01-18 21:24 .
drwxr-xr-x 5 root        root        4096 2011-02-24 23:04  .  .
lrwxrwsrwx 1 double-j double-j  56 2011-01-18 21:04  Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
drwx------ 7 double-j double-j 4096 2011-02-24 23:43 .cache
lrwxrwxrwx 1 double-j double-j   34 2011-01-18 21:04 .ecryptfs -> /home/.ecryptfs/double-j/.ecryptfs 
lrwxrwxrwx 1 double-j double-j   33 2011-01-18 21:04 .Private -> /home/.ecryptfs/double-j/.Private
lrwxrwxrwx 1 double-j double-j   52 2011-01-18 21:04 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt

---

### Post by Krytarik on 2011-02-27
> **jdchurchill said:**
> total 12
dr-x------ 3 double-j double-j 4096 2011-01-18 21:24 .
drwxr-xr-x 5 root        root        4096 2011-02-24 23:04  .  .
lrwxrwsrwx 1 double-j double-j  56 2011-01-18 21:04  Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
drwx------ 7 double-j double-j 4096 2011-02-24 23:43 .cache
lrwxrwxrwx 1 double-j double-j   34 2011-01-18 21:04 .ecryptfs -> /home/.ecryptfs/double-j/.ecryptfs 
lrwxrwxrwx 1 double-j double-j   33 2011-01-18 21:04 .Private -> /home/.ecryptfs/double-j/.Private
lrwxrwxrwx 1 double-j double-j   52 2011-01-18 21:04 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
Well, that sends us in a new direction, you didn't mention that you use encryption, and we didn't even notice it before.

This guide states that you shouldn't have autologin enabled when using encryption. Maybe that also explains the issue with the disabling of the password query:
[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)

Seems that the home isn't decrypted already when you try to log in, I suppose it would work if you switch to the console and login there before.

Since I have no experience with encryption, I have also to do a web search about how to fix it.

---

### Post by jdchurchill on 2011-02-27
i am not sure i require encryption, is there a way to disable it?  

also i tried to run nautilus like you said in an effort to begin moving files and when logged in with the newuser i cannot run that.  because this user does not have administrative priveledges, right?  cuz it works with double-j, but home/double-j has a readme that says
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.  From the graphical desktop, click on "Access Your Private Data" or From the command line, run ecryptfs-mount-private

but when i click on Access-Your-Private-Data.desktop it says
Untrusted application launcher

---

### Post by Krytarik on 2011-02-27
To enable admin rights for the new user

- log into the console with your old user
```
sudo adduser newuser admin
```I don't know about the desktop launcher, just leave that alone.

---

### Post by Krytarik on 2011-02-27
To disable the encryption of your home directory, you may try one of the following guides, but DEFINETELY BACKUP your files/dirs before doing it (both found upon a web search):

[http://art.ubuntuforums.org/showthread.php?t=1373904](http://art.ubuntuforums.org/showthread.php?t=1373904)

[http://www.satansgarden.org/2010/03/05/removing-encryption-from-home-directories-in-ubuntu-9-10/](http://www.satansgarden.org/2010/03/05/removing-encryption-from-home-directories-in-ubuntu-9-10/)

---

### Post by jdchurchill on 2011-02-27
i am confused cuz even with adminstrative priveledges newuser finds the same access-your-private-data in home/double-j so i can't move the files with this strategy

---

### Post by Krytarik on 2011-02-27
> **jdchurchill said:**
> i am confused cuz even with adminstrative priveledges newuser finds the same access-your-private-data in home/double-j so i can't move the files with this strategy
The file is always there, but if you go to "/home/.ecryptfs/double-j", you should find your home directory, I guess in the subdirectory ".Private". Note, that I am learning at the same time as you.

---

### Post by jdchurchill on 2011-02-27
hey krytarik i don't remember ever putting on encryption, could this be an issue related to switching to the 'no password on login'  which even though i have changed back has not?  

also i looked at the satan'sgarden link and am not sure about what it means to change lines as the author describes.  perhaps you could refer me to some sort of primer on doing this?

---

### Post by Krytarik on 2011-02-27
I believe you probably set those option upon the initial install.

Could you access and backup your files as root now?

I recommend the first way I posted, since there are fewer steps necessary and it's proved by UF members.

---

### Post by jdchurchill on 2011-02-27
i think the encryption has been added perhaps very recently as upthread i posted that 
ls /home/double-j/Documents showed me my documents and currently that command returns no such directory because through the encryption the directory is on the unmounted partition.  man this is so frustrating; so much to learn

---

### Post by Krytarik on 2011-02-28
I don't believe that your home directory gets encrypted without order or any notice.

You have to be logged in as "double-j" to have access to your home directory at that exact location. I assume now that even root has no access to your files, though didn't see a specific statement regarding this.

So, please try the following, as mentioned earlier:
- when you are at the login screen switch to the console
- login there as "double-j"
- switch back to GDM
- login there

---

### Post by Krytarik on 2011-02-28
A further indication that your home directory not just recently has been encrypted are the timestamps of the files/dirs:
> **jdchurchill said:**
> total 12
dr-x------ 3 double-j double-j 4096 2011-01-18 21:24 .
drwxr-xr-x 5 root        root        4096 2011-02-24 23:04  .  .
lrwxrwsrwx 1 double-j double-j  56 2011-01-18 21:04  Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
drwx------ 7 double-j double-j 4096 2011-02-24 23:43 .cache
lrwxrwxrwx 1 double-j double-j   34 **2011-01-18 21:04** .ecryptfs -> /home/.ecryptfs/double-j/.ecryptfs 
lrwxrwxrwx 1 double-j double-j   33 **2011-01-18 21:04** .Private -> /home/.ecryptfs/double-j/.Private
lrwxrwxrwx 1 double-j double-j   52 **2011-01-18 21:04** README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt

---

### Post by jdchurchill on 2011-02-28
> **Krytarik said:**
> I don't believe that your home directory gets encrypted without order or any notice.

You have to be logged in as "double-j" to have access to your home directory at that exact location. I assume now that even root has no access to your files, though didn't see a specific statement regarding this.

So, please try the following, as mentioned earlier:
- when you are at the login screen switch to the console
- login there as "double-j"
- switch back to GDM
- login there
just tried this now, and this did not mount the directory.  i still have those durn three errors.  i may give a go removing the encryption as laid out in this link [http://www.satansgarden.org/2010/03/05/removing-encryption-from-home-directories-in-ubuntu-9-10/](http://www.satansgarden.org/2010/03/05/removing-encryption-from-home-directories-in-ubuntu-9-10/)  i think some of the directories might not be named the same but i think i get the idea.  however i am thinking that i will have to go ahead before backing up the data as i can't figure a strategy to open it.  maybe i will mess with the properties to change the ownership or put it into a group that can be accessed by newuser?

---

### Post by Krytarik on 2011-02-28
Since following this guide will simply change the mountpoint of the encrypted data instead of removing it altogether, I consider it safe to do so.

However you should always be able to access your files at the command line by simply logging in at the console, then you should have your home directory exactly at "/home/double-j". If you want to backup your files then, you could a command like this:
```
cp -a /home/double-j WHATEVER
```
This would copy all files/dirs, including subdirectories, while preserving all attributes, like ownership, permissions, timestamps.

---

### Post by jdchurchill on 2011-03-02
[LEFT][IMG]http://i224.photobucket.com/albums/dd210/jdchurchil/Screenshot.png[/IMG]
[/LEFT]

---

### Post by jdchurchill on 2011-03-02
ok i know this might be out of left field but see how there are 2 user bubbles in the upper right of the screen?  does that tell us anything? cuz there should only be one, right?

---

### Post by Krytarik on 2011-03-02
> **jdchurchill said:**
> ok i know this might be out of left field but see how there are 2 user bubbles in the upper right of the screen?  does that tell us anything? cuz there should only be one, right?
No, that isn't related. Sometimes there are those glitches, after switching users, I had those also after I initially installed Lucid at my mom's machine last summer, but it was fixed somehow.

Btw., how is the current progress?

---

### Post by jdchurchill on 2011-03-06
> **Krytarik said:**
> What do you mean by "changed the name"? Did you really change the user/loginname (which isn't possible), or the name of its directory?

if you go to system>administration>users and groups you can alter the users etc this is where i changed things [to be clear, not sure if it was before] it is possible to change the user (name) account type and password there and i changed them all at that time.

i haven't had time to work on this problem so i will be working on it now thru monday morning until i get in there and can see all my pictures and files etc

---

### Post by Krytarik on 2011-03-06
If you really *changed* your password, instead of just disabling its query, you may have to "rewrap" the passphrase of your encrypted home directory, although that should have been done by the password change via the mentioned GUI automatically.
See here for details: [http://ubuntuforums.org/showthread.php?p=10513844](http://ubuntuforums.org/showthread.php?p=10513844)

---

### Post by jdchurchill on 2011-03-06
> **Krytarik said:**
> If you really *changed* your password, instead of just disabling its query, you may have to "rewrap" the passphrase of your encrypted home directory, although that should have been done by the password change via the mentioned GUI automatically.
See here for details: [http://ubuntuforums.org/showthread.php?p=10513844](http://ubuntuforums.org/showthread.php?p=10513844)

yr correct tho 
i didn't change the password 
but i did tick the box that says 'do not ask for password on login'

---

### Post by jdchurchill on 2011-03-06
> **Krytarik said:**
> To disable the encryption of your home directory, you may try one of the following guides, but DEFINETELY BACKUP your files/dirs before doing it (both found upon a web search):

[http://art.ubuntuforums.org/showthread.php?t=1373904](http://art.ubuntuforums.org/showthread.php?t=1373904)

[http://www.satansgarden.org/2010/03/05/removing-encryption-from-home-directories-in-ubuntu-9-10/](http://www.satansgarden.org/2010/03/05/removing-encryption-from-home-directories-in-ubuntu-9-10/)

hmm tried cp -a home/double-j home/newuser and got cp cannot stat 'home/double-j' : No such file or directory so i am worried how to backup my files before moving forward . . .

also in that first link they give step one $ PRIVATE= 'cat ~/.ecryptfs/Private.mnt 2>/dev/null || echo $HOME/Private' 
i hit enter and all i get is 
>
then i enter ecryptfs-unmount-private
i hit enter and again all i get is
>

this means i am not doing anything or what?
don't i have to use sudo?

---

### Post by jdchurchill on 2011-03-06
and how 'bout this:
upon logging into a terminal [startup computer, when login screen appears i hit ctrl-alt-F1]
shows me keyctl_search: Required key not available
Perhaps try the interactive 'ecryptfs-mount-private'

so i think to myself yes why don't i try this and i enter 'ecryptfs-mount-private' and it asks me to Enter your login passphrase which i enter and press enter and i get 

Error: Unwrapping passphrase and inserting into the user session keyring failed [-5]
Info: Check the system log for more information from libecryptfs
Error: Your passphrase is incorrect

---

### Post by jdchurchill on 2011-03-06
but then i remember how i did use the command line to change the password for double-j briefly and i enter that password or passphrase and i get
Inserted auth tok with sig [70d924ebadfdc128e] into the user session keyring

INFO: Your private directory has been mounted
INFO: To see this change in your current shell: cd /home/double-j

so i am kinda excited cuz with this move i switch back to GUI [ctrl-alt-F7] and login there and i am back to the long lost desktop.  so currently i am backing up all the files to an outboard drive.:popcorn:

---

### Post by Krytarik on 2011-03-06
About the password/passphrase thing: The encrypted files are basically secured by the "passphrase", but in order to not having to enter such an complex code each time, it is "wrapped" with the "password". That password should generally be the same as the login password, so that the "passphrase" gets accessed at login and the encrypted files/dirs can be decrypted. It seems like you confused those at some point.

---

