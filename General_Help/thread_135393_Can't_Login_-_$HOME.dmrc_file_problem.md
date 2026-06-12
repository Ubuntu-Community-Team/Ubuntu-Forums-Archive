---
title: "Can't Login - $HOME/.dmrc file problem"
date: 2006-02-23
forum: General Help
---

### Post by fishmorg909 on 2006-02-23
I had to restart my computer when things wre slowing down. Everything seemed normal until I tried to log in, and got this message:

"Your $HOME/.dmrc file has incorrest permissions and is bbeing ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions."

Running in Failsafe GNOME doesn't help. What can I do? I'm working now from the live CD. Thanks. :(

---

### Post by pestilence4hr on 2006-02-23
Did you try changing the permissions on the file in question?  Locate where the live cd mounted your home partition, then from a command prompt:
```
sudo chown (your username) /path/to/.dmrc
sudo chmod 644 /path/to/.dmrc 
```

Note, if you hit ctrl+alt+f1 from your real installation, you can get to a command prompt (hit ctrl+alt+f7 to get back)

---

### Post by fishmorg909 on 2006-02-23
[QUOTE=pestilence4hr]Did you try changing the permissions on the file in question?  Locate where the live cd mounted your home partition, then from a command prompt:
```
sudo chown (your username) /path/to/.dmrc
sudo chmod 644 /path/to/.dmrc 
```

Note, if you hit ctrl+alt+f1 from your real installation, you can get to a command prompt (hit ctrl+alt+f7 to get back)[/QUOTE]

Thanks, but that did nothing at all. I did create a new user with "adduser" and can get on the hard drive that way, but I can't get to my files.

(This "$HOME/.dmrc file" thing seems to be a real bitch, judging by some searches in these threads. It seems very hard to beat. Is there some way I can change the permissions so I can get to my original owner/user files?)

UPDATE: the permissions problem seems unrelated to the number. I also tried

sudo chmod 755 .dmrc

but all that did was make a pause before the "Your $HOME/.dmrc file has incorrect permissions..." message pops up. Could it be some other thing in permissions?

---

### Post by nanotube on 2006-02-23
hey
check what permissions you have on the .dmrc file in your home dir. if they are correct (644 would show -rw-r--r-- for the file), then probably the permissions for your home directory itself are not properly set.
to reset those, do 
```
sudo chmod 755 /home/username
```
(of course replace "username" by your actual username that is having the problem with the .dmrc file).

this worked for the last person who had the problem with .dmrc, after i recommended this to him/her, so maybe will work for you too.

---

### Post by fishmorg909 on 2006-02-23
[QUOTE=nanotube]hey
check what permissions you have on the .dmrc file in your home dir. if they are correct (644 would show -rw-r--r-- for the file), then probably the permissions for your home directory itself are not properly set.
to reset those, do 
```
sudo chmod 755 /home/username
```
(of course replace "username" by your actual username that is having the problem with the .dmrc file).

this worked for the last person who had the problem with .dmrc, after i recommended this to him/her, so maybe will work for you too.[/QUOTE]

I looked in the .chmod file, and all it says is 

[Desktop]
Session=default

I tried the sudo chmod 755 /home/me/ command, but that didn't do anything, either... darn it!

Looking at properties for .dmrc, text view is -rw-------, and number view is 600 -- but I can't seem to get it to change!!

---

### Post by nanotube on 2006-02-23
hm, i dont know what that .chmod file is all about, but that's not how you check permissions.
to check permissions on a file, use command "ls -al". eg, 
```
ls -al .dmrc
```
and that will show you details about that file, including permissions.
to see permissions on a directory, use, eg,
```
ls -ald /home/username
```

---

### Post by fishmorg909 on 2006-02-23
[QUOTE=nanotube]hm, i dont know what that .chmod file is all about, but that's not how you check permissions.
to check permissions on a file, use command "ls -al". eg, 
```
ls -al .dmrc
```
and that will show you details about that file, including permissions.
to see permissions on a directory, use, eg,
```
ls -ald /home/username
```[/QUOTE]

NOT the ".chmod" file, I mean the .dmrc file!! (Dumb fingers.) 

Checking with the first command tells me that the permissions are "-rw-------" in this user account. The second command directed to my **original** account gives me "drwxr-xr-x"

---

### Post by nanotube on 2006-02-24
hehe ic. i was wondering what that .chmod file was... :)

hm, so how about
```
ls -al /home/username/.dmrc
```
to see what the permissions are on .dmrc in your original account?
also see if it is owned by your originar account username, too?

---

### Post by fishmorg909 on 2006-02-24
[QUOTE=nanotube]hehe ic. i was wondering what that .chmod file was... :)

hm, so how about
```
ls -al /home/username/.dmrc
```
to see what the permissions are on .dmrc in your original account?
also see if it is owned by your originar account username, too?[/QUOTE]

I tried that, and it says it's still owned by my original user name.

---

### Post by stansaraczewski on 2006-04-30
I've encountered this problem numerous times and have gotten out of it with the 

[I]sudo chmod 755 /home/myusername
sudo chmod 644 .dmrc
sudo chown myusername .dmrc[/I]

sequence of commands...

Observation: judging by the traffic on this forum it happens to a LOT of people a LOT of times; can this be somehow 'fixed' permanently ?

I realize a number of things could be causing it... 

:confused:

---

### Post by chettyk on 2006-04-30
[QUOTE=stansaraczewski]
Observation: judging by the traffic on this forum it happens to a LOT of people a LOT of times; can this be somehow 'fixed' permanently ?
[/QUOTE]

Amen! It has happened to me and I tried everything I could think of. Finally, in despair, I tar-gzipped all the important sub-directories and files under the home directory before deleting the user and the entire home directory. Of course, it meant putting back the user and restoring the tar-gzipped file. 

As I recall, the error message did not stop me from logging in. It just kept popping up every time I logged in and irritating the heck out of me.

I'd love to know what is causing the problem in the first place.

---

