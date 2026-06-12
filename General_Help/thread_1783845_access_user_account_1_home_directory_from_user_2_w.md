---
title: "access user account 1 home directory from user 2 work space?"
date: 2011-06-16
forum: General Help
---

### Post by tej1984 on 2011-06-16
[I]Do you think there is a way of accessing different user data from another account which I have set up. 

Ie. user 1 = account has messed up 

user 2 = account works fine 

access user account 1 home directory from user 2 work space?[/I]

---

### Post by seawolf167 on 2011-06-16
Sure - the user's directory is under

/home/*username*

You'll need to use sudo to access the files outside your directory, the easiest method would be to open a root file manager window

```
gksu nautilus
```

then simply browse to the above [modified] location.

---

### Post by nothingspecial on 2011-06-16
To move the, for example Video directory over to user2 from user1, assuming user2's Videos directory is empty

In user2's account
```
cd
rm -r ~/Videos
sudo chown -R $USER:$USER /home/user1/Videos && sudo mv /home/user1/Videos ./
```

Now user1's Video folder will be in user2's home and owned by user 2.

Don't leave a space after any / in the 3rd command or you really will break your system.

---

### Post by tej1984 on 2011-06-16
> **nothingspecial said:**
> To move the, for example Video directory over to user2 from user1, assuming user2's Videos directory is empty

In user2's account
```
cd
rm -r ~/Videos
sudo chmown -R $USER:$USER /home/user1/Videos && sudo mv /home/user1/Videos ./
```

Now user1's Video folder will be in user2's home and owned by user 2.

Don't leave a space after any / in the 3rd command or you really will break your system.
ok nothing special 
 
user 1 = tej
user 2 = singh 
 
so i should do the follwoing in terminal of singh  as root 
 
cd
rm -r ~/Videos
sudo chmown -R $USER:$USER /home/tej/Videos && sudo mv/home/tej/Videos./

---

### Post by tej1984 on 2011-06-16
> **seawolf167 said:**
> Sure - the user's directory is under

/home/*username*

You'll need to use sudo to access the files outside your directory, the easiest method would be to open a root file manager window

```
gksu nautilus
```

then simply browse to the above [modified] location.
and i will have access to the home directory what if the user has created other folders outside that dir.

---

### Post by nothingspecial on 2011-06-16
> **tej1984 said:**
> ok nothing special 
 
user 1 = tej
user 2 = singh 
 
so i should do the follwoing in terminal of singh  as root 
 
cd
rm -r ~/Videos
sudo chmown -R $USER:$USER /home/tej/Videos && sudo mv/home/tej/Videos./

No, because I spelt it wrong. And you need a space before the final . and after mv (it's important not to leave spaces after the /
```

sudo chown -R $USER:$USER /home/tej/Videos && sudo mv /home/tej/Videos ./
```

I've edited my first post.

---

### Post by seawolf167 on 2011-06-16
> **tej1984 said:**
> ok nothing special 
 
user 1 = tej
user 2 = singh 
 
so i should do the follwoing in terminal of singh  as root 
 
cd
rm -r ~/Videos
sudo chmown -R $USER:$USER /home/tej/Videos && sudo mv/home/tej/Videos./

There is a typo in the command posted:

```
cd
rm -r ~/Videos
sudo **chown **-R $USER:$USER /home/tej/Videos && sudo mv /home/tej/Videos ./
```

---

### Post by tej1984 on 2011-06-16
cd
rm -r ~/Videos
sudo **chown **-R $USER:$USER /home/tej/Videos && sudo mv /home/tej/Videos ./
 
this is correct so i move from tej to singh? 
 
why it say move /tej/Videos && sudo mv /home/**tej/**Videos ./
 
**should this be singh?***

---

### Post by seawolf167 on 2011-06-16
> **tej1984 said:**
> cd
rm -r ~/Videos
sudo **chown **-R $USER:$USER /home/tej/Videos && sudo mv /home/tej/Videos ./
 
this is correct so i move from tej to singh? 
 
why it say move /tej/Videos && sudo mv /home/**tej/**Videos ./
 
**should this be singh?***

You want to
> **tej1984 said:**
> *access user account 1 home directory from user 2 work space?*

So the command is changing the ownership of the Videos folder to your current user (user2), then moving the folder from user1 (mv /home/tej/Videos) to the current directory of user2 (./)

---

### Post by nothingspecial on 2011-06-16
Because you are already in singh's account.

mv <whatever> ./ 

means move <whatever> here

The . means here which because you've tped cd, is /home/singh

---

### Post by tej1984 on 2011-06-16
> **nothingspecial said:**
> Because you are already in singh's account.

mv <whatever> ./ 

means move <whatever> here

The . means here which because you've tped cd, is /home/singh
i get it!!! i will try it!!!  fingers cross if this works you guys are Legends!!

---

### Post by tej1984 on 2011-06-16
sohal@Tyson:~$ cd
sohal@Tyson:~$ rm -r ~/Videos
sohal@Tyson:~$ sudo chown -R $USER:$USER /home/tej/Videos && sudo mv /home/tej/Videos ./
[sudo] password for sohal: 
sohal is not in the sudoers file.  This incident will be reported.
sohal@Tyson:~$ 



it didnt work

---

### Post by tej1984 on 2011-06-16
Omg u legend !!! This works i have access to everything!!!

---

### Post by tej1984 on 2011-06-16
> **seawolf167 said:**
> Sure - the user's directory is under

/home/*username*

You'll need to use sudo to access the files outside your directory, the easiest method would be to open a root file manager window

```
gksu nautilus
```

then simply browse to the above [modified] location.
i want to transfer all the stuff form user 1 to user 2 and delete user one forever can this be done?

---

### Post by seawolf167 on 2011-06-16
To delete a user, use the following command

```
sudo deluser *username*
```

This command only deletes the user, it does not delete that user's home folder, so you can use this command to delete the "bad" user, then transfer the files over. Once you transfer the files, if you didn't use the commands previously listed, you'll want to make yourself the owner of the transfered files with the *chown *command

---

### Post by tej1984 on 2011-06-16
> **seawolf167 said:**
> To delete a user, use the following command

```
sudo deluser *username*
```

This command only deletes the user, it does not delete that user's home folder, so you can use this command to delete the "bad" user, then transfer the files over. Once you transfer the files, if you didn't use the commands previously listed, you'll want to make yourself the owner of the transfered files with the *chown *command
Great this will only delete that user and what about the space which the suer has taken on the Hard-drive will that will delete? also I can only copy some docs and not all I keep getting this you "you only have read permission"

---

### Post by seawolf167 on 2011-06-16
> **tej1984 said:**
> Great this will only delete that user and what about the space which the suer has taken on the Hard-drive will that will delete? also I can only copy some docs and not all I keep getting this you "you only have read permission"

Since the user's files/folders do not reside in your /home/user folder, you need *sudo*, i.e. open a root file manager window as previously posted.

As for deleting his space on the hard-drive, if you remove his files/folders, the space taken up by them will be empty (i.e. move to trash -> empty trash, or using the *rm* command)

---

### Post by tej1984 on 2011-06-16
> **seawolf167 said:**
> Since the user's files/folders do not reside in your /home/user folder, you need *sudo*, i.e. open a root file manager window as previously posted.

As for deleting his space on the hard-drive, if you remove his files/folders, the space taken up by them will be empty (i.e. move to trash -> empty trash, or using the *rm* command)
I can not empty his trash can ....as for when i transfer stuff over to my workspace the disk spaces gets eaten up 

how do i use the chown command? example please....

because when i try it doesnt work but the gksu nautilus command works thats how im copying and pasting them over to the new work space but some are read only....which i can not do .

---

### Post by seawolf167 on 2011-06-16
The Trash Bid resides in the location: ~/.local/share/Trash, i.e. /home/username/.local/share/Trash

See the previous posts for a chown example, you can also read the man page for more information

```
man chown
```

---

### Post by nothingspecial on 2011-06-16
Is singh an admin account?

---

### Post by tej1984 on 2011-06-16
> **nothingspecial said:**
> Is singh an admin account?
yes i had to change it to admin otherwise the gksu nautilus command would not run

---

### Post by nothingspecial on 2011-06-16
> **tej1984 said:**
> sohal@Tyson:~$ cd
sohal@Tyson:~$ rm -r ~/Videos
sohal@Tyson:~$ sudo chown -R $USER:$USER /home/tej/Videos && sudo mv /home/tej/Videos ./
[sudo] password for sohal: 
sohal is not in the sudoers file.  This incident will be reported.
sohal@Tyson:~$ 



it didnt work

That's why that didn't work.

Anyway, what is not working with the chown command now that you have an admin account?

---

### Post by tej1984 on 2011-06-17
> **nothingspecial said:**
> That's why that didn't work.

Anyway, what is not working with the chown command now that you have an admin account?
What I have done now is because there so much work on the other account I thought I just would create a launcher to the work space form the new work space desktop -- which I have created.

However there is a "lock" icon on some of the files not all? which I can not access any ideas?

but you where right - there are files which exist in the  ~/.local/share/Trash, i.e./ root  /home/username/.local/share/Trash also which I deleted and I could   [FONT=&quot]find [/FONT] the lost space.

---

### Post by nothingspecial on 2011-06-17
The eventual outcome of this is to move (not copy) all the work and documents and stuff from from the old account to singh.

Make a folder on singh's Desktop called stuff (all lowercase letters)

Using gksu nautilus move (drag and drop, not copy and paste or you might not have enough space) everything you want from tej's account into it, even if you have moved it over already - that's all the stuff with locks on them as well as anything you haven't moved over yet.

Once you are done, open a terminal in singh's account and type

```
sudo chown -R $USER:$USER ~/Desktop/stuff
```

Now everything in the folder called stuff on your Desktop will be owned by singh and not tej and will not have a lock on it.

---

### Post by tej1984 on 2011-06-17
> **nothingspecial said:**
> The eventual outcome of this is to move (not copy) all the work and documents and stuff from from the old account to singh.

Make a folder on singh's Desktop called stuff (all lowercase letters)

Using gksu nautilus move (drag and drop, not copy and paste or you might not have enough space) everything you want from tej's account into it, even if you have moved it over already - that's all the stuff with locks on them as well as anything you haven't moved over yet.

Once you are done, open a terminal in singh's account and type

```
sudo chown -R $USER:$USER ~/Desktop/stuff
```

Now everything in the folder called stuff on your Desktop will be owned by singh and not tej and will not have a lock on it.
This is very interesting ----- so everything is stil owned by tej so if i was to delete that user from user groups, stuff owned by him will also be deleted? I have moved some stuff over without the locks & not ran that command yet does that mean this will stuff is still owned by Tej or Singh?>

---

### Post by nothingspecial on 2011-06-17
Don't delete tej until everything is over on singh's account and owned by singh

Moving the files over to singh will not make them owned by singh, they are still owned by tej until you run the chown command. That's why the have locks on them.

The reason I suggest you put everything in one folder is that you can run the chown command on a folder and change the owner of everything in it. This means you only have to do it once.

---

### Post by tej1984 on 2011-06-17
> **nothingspecial said:**
> Because you are already in singh's account.

mv <whatever> ./ 

means move <whatever> here

The . means here which because you've tped cd, is /home/singh
Is it worth me trying to use something like "Back  in Time" application incase anything happens like this i can restore using this back up application the core systems hence

---

### Post by seawolf167 on 2011-06-17
> **tej1984 said:**
> Is it worth me trying to use something like "Back  in Time" application incase anything happens like this i can restore using this back up application the core systems hence

It is always worth it to have backups. There are *many* ways of creating backups for your system, however, I think the best solution for you (IMO) would be to use [Clonezilla]("http://www.clonezilla.org"). With this you can create an image of your entire hard drive (including boot records), then write that image to an external drive. If your drive crashes or you mess something up and you can't fix it, you can simply write the image to your drive and be back to the exact same spot you were when you made the backup.

[Here are ]("https://help.ubuntu.com/community/BackupYourSystem")some other methods.

---

