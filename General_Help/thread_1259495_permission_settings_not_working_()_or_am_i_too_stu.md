---
title: "permission settings not working (?) or am i too stupid?"
date: 2009-09-06
forum: General Help
---

### Post by alejaaandro on 2009-09-06
hi there.. i need some help with my permission settings please..

to give you the background, i setup a new user for my brother to connect via sftp and dump some files to my machine.. the shell was set to /usr/lib/sftp-server so in case others manage to gain access, i think this will prevent them from doing any harm (that's what i read at least, correct if wrong)

i want to be able to manage the files he sends me,i can't, no matter what i do..(i can use root, but want to do it as simple user for various reasons)..

-i added myself to the new user's group ("ssh_usr") and verified with 'groups "me" ' & double checked in /etc/group where i found "ssh_usr":x:1001:"ssh_usr","me"

-changed "group" permissions in /home/ssh_usr to "create and delete"..(did it in terminal too, just to make sure it wasn't a nautilus problem)
ls -l now gives drwxrwxr-x, which should be correct (i think)..

i did mess up with some permissions earlier, which gave me some trouble (ie. sudo wouldn't work) but i reverted my changes, booted to recovery mode an fixed it.. just to make sure that i hadn't broke something else apart from sudo, i tried the same thing on my laptop and still couldn't manipulate the new users' home folder

am i doing something wrong, am i missing something? i m sure i had done that some time ago when i had to setup an extra user for some reason


both machines running ubuntu 9.04.. my brothers' is a mac, but that shouldn't matter

---

### Post by Bucky Ball on 2009-09-06
Are you running static IPs or both getting served DHCP from the same router? Are you both on the LAN or is your brother trying to get on to your LAN from WAN?

---

### Post by alejaaandro on 2009-09-06
thnx for the quick answer..
my problem is not with ssh.. we are on the same wlan, everything is configured ok, he can send me his files, i can see them in my computer under /home/"ssh_usr"..

problem is I can't manipulate them (or the /home/"ssh_usr") from my LOCAL machine (not talking ssh anymore, i mean after i have them in my computer), i hope i 'm clear now.. i want to create files in his folder, or edit/delete his files

---

### Post by orlox on 2009-09-06
I believe the problem is that ssh_usr copies the files with write permissions only to himself, and not to the group he belongs to...so, unless you are ssh_usr, you wont be able to access those files directly.

It doesnt matter if you added yourself to the ssh_usr group, or if you changed the permissions of /home/ssh_usr, you are not ssh_usr, adn when connected by ssh, he most probably copies files with only reading permission to "others" and "group"...

...not sure however how you can set some default permissions for copied files.  think this mght even be something that has to be configured in the client-side

---

### Post by alejaaandro on 2009-09-06
you are partially right... he does transfer files with write only permissions to group and others, and i think i saw a setting to change that when i was setting up his client.. will have to look later..

but that wouldn't explain why i can't create files in his folder.. and i used root to change the permissions on some of his incoming files, and still can't delete/edit..

please overlook the ssh thing, i m quite sure it's not the problem, i just wrote it as a background info.. i did mention i tried it on a different machine too (not the ssh, just setting a new account and trying to manipulate his home folder) and it didn't work.. is there an other setting i have to do, is it a know bug (i doubt, permission setting is one of the most basic/fundamental features in linux, it would've been fixed), or did i break something (on both my machines? i doubt cause i do experiment on my desktop, but not my laptop)..

---

### Post by orlox on 2009-09-06
Would you please post the result of checking the permission of the /home/ssh_usr folder and the contents of that one:

```

cd /home
ls -l
cd /home/ssh_usr
ls -l

```

---

### Post by alejaaandro on 2009-09-06
ls-l /home gives

total 8
drwxrwxr-x  2 ssh_usr	ssh_usr 4096 2009-09-06 21:17 ssh_usr
drwxr-xr-x 70 "me" 	"me" 	4096 2009-09-06 21:29 "me"

ls -l /home/ssh_usr

total 1408
-rw-r--r-- 1 ssh_usr ssh_usr 718718 2009-09-06 19:34 0019.2.jpeg
-rw-rw-r-- 1 ssh_usr ssh_usr 718718 2009-09-06 19:34 0019 (copy).2.jpeg

groups "me" gives

 "me" various other and ssh_usr


from my understanding, i should be able to:
*create/delete (i m not sure about deleting) files in /home/ssh_usr
*edit 0019 (copy).2.jpeg (which i modified permissions as root)

none of the above happen...

as a workaround i changed /home/ssh_usr to group "me" and i can   add/remove files.. i still want to fix the problem though cause  if i want more users modifying the folder, that wouldn't work..

---

### Post by orlox on 2009-09-06
That's certainly strange...

What do you get if you try to create a file by terminal:

```

touch /home/ssh_usr/newfile

```

---

### Post by alejaaandro on 2009-09-06
Permission denied
just as i expected.. the same with mkdir

---

### Post by Bucky Ball on 2009-09-06
Use sudo:

sudo touch /home/ssh_usr/newfile

---

### Post by alejaaandro on 2009-09-06
then, i can obviously make the file..

permissions are
-rw-r--r-- 1 root root      0 2009-09-06 22:06 newfile

---

### Post by orlox on 2009-09-06
> **Bucky Ball said:**
> Use sudo:

sudo touch /home/ssh_usr/newfile

That's not really the point...we're are trying to see why he gets the permission denied...

---

### Post by alejaaandro on 2009-09-06
well, then, in case it tells you anything more, here is the full thing

touch /home/usr_ssh/newfile
touch: cannot touch `/home/usr_ssh/newfile': Permission denied

and when using sudo there is no feedback..

is there any log file where this kind of things (authentication, permissions stuff) go?

---

### Post by orlox on 2009-09-06
> **alejaaandro said:**
> well, then, in case it tells you anything more, here is the full thing

touch /home/usr_ssh/newfile
touch: cannot touch `/home/usr_ssh/newfile': Permission denied

and when using sudo there is no feedback..

is there any log file where this kind of things (authentication, permissions stuff) go?

Not that I am aware, that info does not get logged...

Is there a particular reason why you cannot set the permission on that folder to read-write for all?? I know it should work as it is know, but perhaps if you don't have any security worries, you can try that...

Also, are the standard sharing options not viable for you?? What is the OS of your brother??

---

### Post by alejaaandro on 2009-09-06
i had already tried read/write to others and works ok.. no real security issues, but i like things working as they should.. anyway, at this point it has become more a curiosity thing of what could be the problem...

my brother has mac osx.. samba seems too much of a fuss to make a server with linux and i have no idea how to do it in mac (neither does my brother i guess).. plus i have been playing around with ssh (tunneling X to my laptop) over the past weeks so i learned how it works and was the easiest thing to setup, remaining safe (as opposed to ftp).. 

what other protocols can i try?

can you confirm this problem, or does it work ok with you?

---

### Post by orlox on 2009-09-06
Just replicated the problem under similar permissions. I'll try to see if Im doing something wrong somewhere and I'll tell you if I found a fix.

---

### Post by alejaaandro on 2009-09-06
hmmm... that's interesting... i'll wait to see if you get anywhere, or else, maybe i should file a bug...

---

### Post by orlox on 2009-09-06
I judt tried another thing...

I created a new user whore PRIMARY group was the one of the folder, and he can create files under the folder...strange though, permissions should apply even if the group is not the primary group of that user...

---

### Post by alejaaandro on 2009-09-06
shame on us... it seems to be just a matter of logging out and in again...

i first made my main group ssh_usr.. it didn't work
i created a third "test" user to try what you said.. i gave him main group ssh_usr and it worked ok.. so i thought, what did i do to now that was different? login!!!

i changed my own group back to "me" (i was still added to ssh_usr group).. logged out and in and it works fine..

please confirm so i can mark as solved...

---

### Post by Bucky Ball on 2009-09-07
> **orlox said:**
> That's not really the point...we're are trying to see why he gets the permission denied...

The point is you can't 'touch' to create a file without being root. That's why you need sudo or you will get 'Permission Denied' forever because you are not root. It will be denied.

Alejaaandro: When you run 'sudo touch' and there is no response, it is because you have created the file! That is the response. Look in the directory you tried to create the file. It should be there.

Sheesh, orlox!!

---

