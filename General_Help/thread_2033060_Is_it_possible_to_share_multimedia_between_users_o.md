---
title: "Is it possible to share multimedia between users on the same computer?"
date: 2012-07-25
forum: General Help
---

### Post by idonald on 2012-07-25
Hi,

I have installed ubuntu 12.04 on my new laptop and I have a lot of family photos, music and videos that will be saved on the hard disk.  I will be creating 3 user accounts on this system, one for me, another for my wife and a third for my daughter.

I wanted to have the media shared so that any user account can access and modify the contents(mainly by adding new items)which would be visible by all user accounts.

Is there an easy way of doing this?

---

### Post by HermanAB on 2012-07-25
Yes.
:)

Make a directory somewhere, e.g. sudo mkdir /home/fampics
Make a group for everybody, e.g. sudo groupadd family
Make everybody members of that group, e.g. sudo usermod -G family joesoap
Set the directory group, e.g. sudo chown root:family /home/fampics
Make the directory SGID, e.g. sudo chmod g+s /home/fampics

Now files uploaded to /home/fampics should be usable by all members of group family.

---

### Post by idonald on 2012-07-25
Hi Herman,

Thanks for this.  Would I need to make some sort of shortcut in my own home directly to that folder or will it already be visible by going into my own home folder?

Kind Regards

---

### Post by idonald on 2012-07-26
Could anyone advise on the above please?

---

### Post by steeldriver on 2012-07-26
It would be visible by going UP one directory from your home folder, i.e. from 

```
/home/*yourname*
```to

```
/home
```If that's not enough, you could create a symbolic link (shortcut) from your home folder,

```
mkdir ~/fampics
ln -s ~/fampics /home/fampics
```

---

### Post by idonald on 2012-07-26
Thanks Steeldriver I really appreciate the assist.  

Out of curiosity, are there any alternative/better ways of achieving this? I'm not saying the above suggestion is bad or unhelpful(the complete opposite in-fact), I would just like to look at several options if possible so I can choose the one that makes most sense to me.

The more I learn the better I guess.

Many Thanks

---

### Post by Grenage on 2012-07-26
> **idonald said:**
> Out of curiosity, are there any alternative/better ways of achieving this?

The above suggestion is probably the most elegant, and simplest to maintain!

---

### Post by LewisTM on 2012-07-26
As an alternative, use ACLs (Access Control Lists).

Install eiciel which will allow you to edit ACLs in Nautilus for each file and directory. This lets you to pick permissions for each user as well as specify defaults for each directory.

ACLs are enabled on recent Ubuntu versions.
More on ACLs: [https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport](https://help.ubuntu.com/community/UbuntuLTSP/ACLSupport)

---

### Post by idonald on 2012-07-26
Very helpful guys, thanks.

---

### Post by Morbius1 on 2012-07-26
The only problem I foresee is that the following won't work:
> Make a directory somewhere, e.g. sudo mkdir /home/fampics
Make a group for everybody, e.g. sudo groupadd family
Make everybody members of that group, e.g. sudo usermod -G family joesoap
Set the directory group, e.g. sudo chown root:family /home/fampics
Make the directory SGID, e.g. sudo chmod g+s /home/fampics

Now files uploaded to /home/fampics should be usable by all members of group family.     
It's missing a step. As posted the ownership / permissions on /home/fampics is: **drwxr-sr-x  root family**

No one has write access except root. So fix it with a:
```
sudo chmod 2775 /home/fampics
```Or this is you want the ability to let anyone add files to the folder but restrict who can remove files to the original owner:
```
sudo chmod 3775 /home/fampics
```*[COLOR=Blue]Side note[/COLOR]: This will work in 12.04 as  presented because the default umask on new files for non root users has changed to 002 from  022. If you were running an earlier version of Ubuntu you would also  have to change the default umask.*

---

### Post by Morbius1 on 2012-07-26
*Double post for some reason*

---

### Post by idonald on 2012-07-27
This forum is amazing, thanks for the assist Morbius1

---

### Post by Morbius1 on 2012-07-27
If you'd like to be confused further there is another way to do this and that's to make your folder look and act as though it was on an NTFS partition.

[1] Go through the same steps of creating the directory and group and adding users to the group.

[2] Install bindfs
```
sudo apt-get install bindfs
```[3] Run the following command as a test:
```
sudo bindfs -o group=family,perms=0660:ug+D /home/fampics /home/fampics
```[COLOR=Blue][I]Note: To unmount this:
```
sudo umount /home/fampics
```[/I][/COLOR]
That's going to need some explanation since it looks like one big typo:

What you are doing is creating a "view" of the /home/fampics directory by mounting it to itself with options set by bindfs. In this case all folders and files will have the group set to "family" with permissions of folders = 770 and files = 660.

This is a temporary mount that will not persist with a reboot. You can add a line to /etc/fstab to have this done automatically when the machine is booted but I have found the safest way is to create your own upstart job:

[1] Create an upstart config file:
```
gksu gedit /etc/init/bindfs-remounts.conf
```[2] Add this content:
```
# Create List of Bindfs Remounts
  description "Bindfs Remounts"

  start on stopped mountall

  script
    bindfs -o group=family,perms=0660:ug+D /home/fampics /home/fampics
  end script
```[3] Run the following command to test for errors and execute the upstart job:
```
sudo initctl start bindfs-remounts
```Admittedly, it's a bit more work to do it this way but once the "bindfs-remounts" job is created you can add multiple bindfs lines - one after the other between the "script" and "end script" statements- to the file as the need arises.

Advantage of bindfs: It's immutable. Some applications and things like Samba have their own ideas about how file permissions should be set when they create files and these will override normal Linux permission defaults ( like umask ). bindfs is impervious to this - just like an ntfs partition.

Disadvantages of bindfs:

** There is no counterpart to the "sticky bit" ( at least none that I have found yet ) which prevents one user from removing a file created by another - again, just like an ntfs partition.

** There are reports that a bindfs remouted folder has a slower resonse time ( R/W time ) than a normal folder presumably because a bindfs remount uses fuse to create a virtual file system. I haven't expericnced that myself but my needs may not be as intensive as yours.

---

### Post by idonald on 2012-08-03
Now you are showing off :-p

Seriously though, thanks.  I am going to read over all of these suggestions and setup my folders over the weekend.

Thanks
Iain

---

### Post by idonald on 2012-08-11
Hi All,

See below for tl:dr

I followed the guides below to try and create my shares.  I created a **/home/share/pictures** directory and set the **/home/share** directory as the groups home folder.

I then tried creating a symbolic link to **/home/share** using the the info below but whenever I tried using the shortcut in my home directory, I couldn't see the 'pictures' sub-directory of **/home/share - **it seemed to open up an empty folder.  I also tried placing a test file in **/home/share** to see if I could view it but the folder was still blank so I suspect I am doing it wrong.  I set the symlink to **/home/share** as I assumed it would show all sub folders if I use the symlink.

I tried deleting the symlinks from my own home folder and from **/home/share** but now when I try to use sudo, the system says my username is not part of the sudoers file.  My account was the only admin level account on the system, is there any way of fixing these issues?  Mainly the sudo issue and the symlink problem?

**TL;DR - SYMLINK ISNT WORKING AND I AM NO LONGER PART OF THE SUDOERS FILE**



> **HermanAB said:**
> Yes.
:)

Make a directory somewhere, e.g. sudo mkdir /home/fampics
Make a group for everybody, e.g. sudo groupadd family
Make everybody members of that group, e.g. sudo usermod -G family joesoap
Set the directory group, e.g. sudo chown root:family /home/fampics
Make the directory SGID, e.g. sudo chmod g+s /home/fampics

Now files uploaded to /home/fampics should be usable by all members of group family.

> **steeldriver said:**
> It would be visible by going UP one directory from your home folder, i.e. from 

```
/home/*yourname*
```to

```
/home
```If that's not enough, you could create a symbolic link (shortcut) from your home folder,

```
mkdir ~/fampics
ln -s ~/fampics /home/fampics
```

> **Morbius1 said:**
> The only problem I foresee is that the following won't work:
It's missing a step. As posted the ownership / permissions on /home/fampics is: **drwxr-sr-x  root family**

No one has write access except root. So fix it with a:
```
sudo chmod 2775 /home/fampics
```Or this is you want the ability to let anyone add files to the folder but restrict who can remove files to the original owner:
```
sudo chmod 3775 /home/fampics
```*[COLOR=Blue]Side note[/COLOR]: This will work in 12.04 as  presented because the default umask on new files for non root users has changed to 002 from  022. If you were running an earlier version of Ubuntu you would also  have to change the default umask.*

---

### Post by idonald on 2012-08-11
anyone?

---

### Post by idonald on 2012-08-11
I found out that the issue may have been caused by this step:

> Make everybody members of that group, e.g. sudo usermod -G family joesoap

According to [this site]("http://maketecheasier.com/fixing-sudo-error-in-ubuntu/2012/01/03") you need to put -a there too, or you will be removed from the sudoers group.  Unfortunately these steps are not working to get it back though as when I try to add myself back a message appears staing the admin group does not exist.

---

### Post by idonald on 2012-08-11
Managed to resolve the issue with sudo, there is no admin group in 12.04, it is now called sudo so by using the commands on my previous post it worked fine.

---

### Post by warm cardigan on 2012-08-11
Of course, there is also the option of simply storing all of this media on an external hard drive.

---

### Post by idonald on 2012-08-11
> **warm cardigan said:**
> Of course, there is also the option of simply storing all of this media on an external hard drive.

Of course, but if I wanted to do this then I would have. I will keep a backup of the files on an external HDD but it is inconvenient for me to pull out an external HDD whenever I wish to look at a picture, I have a hard drive in my computer with more than enough storage space so why not use it?.

---

### Post by cwsnyder on 2012-08-11
I don't know why this wasn't suggested before, but why not an additional partition on your hard drive which is loaded in /etc/fstab by each user, but owned by root or a group to which all members belong.  This has drawbacks in that it is a fixed size, but has the advantage that it can be shared between distros as well as an external drive.

---

### Post by idonald on 2012-08-11
> **cwsnyder said:**
> I don't know why this wasn't suggested before, but why not an additional partition on your hard drive which is loaded in /etc/fstab by each user, but owned by root or a group to which all members belong.  This has drawbacks in that it is a fixed size, but has the advantage that it can be shared between distros as well as an external drive.

I never gave it much thought because I had decided to create /home on it's own partiton from the beginning and figured it was much the same.

---

### Post by cwsnyder on 2012-08-11
No, the folders on /home are private to the individual users.  You can even share the same /home partition between distributions, but you should have separate, distinct usernames to prevent problems where one distribution does not track the same application versions as another distribution.

---

### Post by idonald on 2012-08-11
> **cwsnyder said:**
> No, the folders on /home are private to the individual users.  You can even share the same /home partition between distributions, but you should have separate, distinct usernames to prevent problems where one distribution does not track the same application versions as another distribution.

I do have seperate distinct usernames, all I did was create a shared folder in /home which is seperate from each users home directory.  So it's on a seperate partition and is user independant.

---

### Post by cwsnyder on 2012-08-14
The shared folder in /home (that is not a separate partition) could be shared between users, but you would have to manually add users to the group which owns the folder, and probably have to chmod the permissions to allow anyone other than the original owner to have more than read-only permissions in the folder.

---

### Post by idonald on 2012-08-16
> **cwsnyder said:**
> The shared folder in /home (that is not a separate partition) could be shared between users, but you would have to manually add users to the group which owns the folder, and probably have to chmod the permissions to allow anyone other than the original owner to have more than read-only permissions in the folder.

I have already done that using a guide one of the other members posted.  There will never be any more users on this machine so I am confident this setup will work, but I have a query in relation to this setup.  

If I copy a folder from my own personal home folder, into the shared folder it keeps the previous group permissions.  Is there anyway I can configure the system so that any file or folder that is moved into the shared directory inherits the shared groups permissions, rather than retaining the ones that it belonged to in the previous directory?

---

### Post by Morbius1 on 2012-08-16
That should have been taken care of by the "chmod 2775 ... " or the "chmod 3775 ... " commands.

---

### Post by idonald on 2012-08-20
> **Morbius1 said:**
> That should have been taken care of by the "chmod 2775 ... " or the "chmod 3775 ... " commands.

It hasn't turned out this way for me i'm afraid.  I used "chmod 2775" as I want all users to have R/W access to the shared folder.  But when I transferred all of the files from my home folder, to the shared folder, they were still being flagged as belonging to the group "iain" which is my user name.  I have the "iain" group setup so that none of the other users can view the contents of my home directory as I was surprised that Ubuntu allowed this by default.

So once I had moved all of the files from my home directory, to the shared directory, I had to manually change the group the files belonged to, to the "family" group.  It's a little inconvenient for me but I could plod along in this fashion but the other 2 users(my wife and daughter)would find this difficult so I was hoping that by transferring files from a users home folder to the shared folder, the files in question would automatically be transferred to the "family" group.

---

### Post by Morbius1 on 2012-08-20
First, Post #12 starting to look better to you now?  ;)

Anyway, could you please explain this comment:
 > I have the "iain" group setup so that none of the other users can view  the contents of my home directory as I was surprised that Ubuntu allowed  this by default.And could you post the ownership and permissions of the directory you set up to be shared. If I read you posts correctly it's something like /home/shared:
```
ls -dl /home/shared
```

---

### Post by idonald on 2012-08-20
> **Morbius1 said:**
> First, Post #12 starting to look better to you now?  ;)

Anyway, could you please explain this comment:
 And could you post the ownership and permissions of the directory you set up to be shared. If I read you posts correctly it's something like /home/shared:
```
ls -dl /home/shared
```

Post #12 seems like a lot of effort but I am intrigued a little hehe.

What I meant by the comment is that I have 3 user accounts on this laptop.  If I login to any of the other 2 user accounts, I am able to browse the contents of /home/iain.  So I setup the permissions via Nautilus to not allow people of the same group(iain) to view my files as this is why I am setting up a shared folder. 

Hope that makes more sense.

The results of the command you requested is:

```
iain@ubuntu:/home$ ls -dl /home/share
drwxrws--- 5 root family 4096 Aug 11 17:44 /home/share
```

---

### Post by Morbius1 on 2012-08-21
This is a guess. And it's a guess only because it's the only way so far that I can reproduce your symptoms.
> So I setup the permissions via Nautilus to not allow people of the same  group(iain) to view my files as this is why I am setting up a shared  folder. ** The group "iain" is a "private group" or "usergroup" so the only one that has access to that group is the user: iain.

** The default ownership and permissions of your home folder was 755 meaning only iain had read /write access but everyone else had read access.

** Instead of changing permissions to 750, which would have made your home folder inaccessible to everyone other that iain, you went to the limit and set it to 700 which would have made it inaccessible to the group iain which was unnecessary.

** When you did that you selected "Apply Permissions to Enclosed Files" making all your files have permissions of 600. There was no need to do that because the parent directory was already set to 700 so no one other than iain could have opened up that folder to get to the contents. 

If I move a file with permissions of 600 from /home/iain to /home/share it's group will in fact change from iain to family but it's permissions will remain at 600 forcing you to change permissions not group.

At this point I would argue that the easiest way is to use bindfs on the shared folder. If setting up an Upstart job seems too complex to you there is another way:

[1] Make sure a temporary manual mount does what you want it to do:
```
sudo bindfs -o group=family,perms=0660:ug+D /home/share /home/share
```From that point on during that session is doesn't matter what permissions you set via Nautilus or with a chmod or chown. Normal Linux permission utilities will no longer have any affect - bindfs is in charge. All new and existing files will be 660, all new and existing folders will be 770, and all will have group = family.

[2] Instead of an upstart job edit a file as root:
```
gksu gedit /etc/rc.local
```And right above the "exit 0" line add the following line:
```
bindfs -o group=family,perms=0660:ug+D /home/share /home/share

```An upstart job removes all doubt that the bindfs command will only run after the partition is mounted because it's designed to wait for confirmation. Since the partition in question in this topic is the root partition itself rc.local should work as well.

---

### Post by idonald on 2012-08-21
Wouldnt it just be easier to revert those permission changes than setup bind fs?  I cant fully get my head around bindfs, I get the basic concept of it bit get a little lost on the technicalities and I don't like the idea of running a configuration that I don't understand easily.

I read on ask ubuntu that the default user permissions were changed in 12.04 which allows users to share files easier which is why I made the permission changes via Nautilus.

Here is the link: [https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha2#Default_file_permissions](https://wiki.ubuntu.com/OneiricOcelot/TechnicalOverview/Alpha2#Default_file_permissions)

By the way I just want to say thanks for taking the time to assist with this, I really appreciate your help

---

### Post by Morbius1 on 2012-08-21
The default umask was changed in 12.04 from 022 to 002 resulting in new files [COLOR=Blue]created by a given user[/COLOR] having permissions of 664 instead of 644. That in itself doesn't make them shareable unless you change the group to a common group or use something like setgid. But you circumvented all that and rather than repeatedly messing with permissions in your home folder my suggestion was to use bindfs and leave your home folder alone.

If you feel more comfortable with reverting somehow to the original permissions then go for it.

---

### Post by idonald on 2012-08-21
> **Morbius1 said:**
> If you feel more comfortable with reverting somehow to the original permissions then go for it.

The way you wrote that makes me think it's not easily done, is it possible?

---

### Post by Paddy Landau on 2012-08-22
You can submit the following two commands, but be aware that it will set *all* of your files and folders in your own home folder, which is not necessarily what you want.

Warning: I have not tested these commands, so wait until someone such as Morbius replies in case they find problems with my commands.

```
chmod u+rwx,g+rx,g-w,o-rwx ~
find ~ -xdev '(' -type d -exec chmod ug+rwx,o-rwx {} + ')' -o '(' -type f -exec chmod ug+rw,o-rwx {} + ')'
```*Morbius: I have learned from you in this thread, thank you. Is there a "dummy's guide" to advanced chmod functions, such as chmod 2775 and SGID? I have been experimenting with them and, although I get it to work as you explain, I don't understand how they work.*

---

### Post by Morbius1 on 2012-08-22
> **Paddy Landau said:**
> You can submit the following two commands, but be aware that it will set *all* of your files and folders in your own home folder, which is not necessarily what you want.

Warning: I have not tested these commands, so wait until someone such as Morbius replies in case they find problems with my commands.

```
chmod u+rwx,g+rx,g-w,o-rwx ~
find ~ -xdev '(' -type d -exec chmod ug+rwx,o-rwx {} + ')' -o '(' -type f -exec chmod ug+rw,o-rwx {} + ')'
```*Morbius: I have learned from you in this thread, thank you. Is there a "dummy's guide" to advanced chmod functions, such as chmod 2775 and SGID? I have been experimenting with them and, although I get it to work as you explain, I don't understand how they work.*
I don't know if I'm the ultimate authority on this subject but it should be in the man pages for chmod.

Your commands look like they will work but there is an easier way to do this:
```
chmod -R ug+rwX,o-rwx /path
```The big "X" sets folders to x but not files unless the files where executable to begin with. 

This will set the home folder to 770 instead of 750 but it's group is still the same as the user so it doesn't really matter. All the files will be set to 660 unless they were individually set to executable in which case those will be 770.

Like you though I generally don't like to mess around with changing permissions of home folders. In looking at my own home folder there a lot of odd permissions in there and a few files that are owned by root so ...
[COLOR=Blue][B]
EDIT[/B][/COLOR]: What can be done is copy all the existing files from the user's home directory to the /home/share that he wants to have in there. Then change permissions on all of them in /home/share so that they are writeable to group. Any newly created files added to his home folder or to the share folder will save as 660 so it's not a continuing problem only an initial one.

---

### Post by Paddy Landau on 2012-08-22
Morbius, thank you for pointing out the +X. That does indeed make things simpler!

---

### Post by idonald on 2012-08-23
I'm at work just now but just wanted to give my thanks for the help posted here by everyone, I will be trying these steps over the weekend.

---

### Post by idonald on 2012-08-23
After reading the man page for chmod and a few other articles on file/folder permissions in general(on top of what I have learned from this thread), I am beginning to realise the scope of my error in changing the permissions in my home directory.

I will play about with these extra commands and see how it goes but I might re-install the OS over the weekend and start from scratch.  I don't have any files on the computer yet as it was a fairly new installation anyway.

If I do decide to re-install, I shall follow the advice from this thread more closely so I do not make the same mistakes.

---

### Post by idonald on 2012-08-24
I did a re-install last night to get myself back to stage where the permissions were not messed up.  I have set things up a little different this time.  I have made a separate partition in **/media/shared** and left the OS on one partition.

I will probably create a group called **usershare** or something and set **/media/shared** as the home location for this group.

I am going to go through this guide again and use bindfs with an upstart job as Morbius1 has suggested as I now understand it more clearly.  I am going to follow the guide to the letter and not adjust any permissions via Nautilus like I did last time.

Hopefully everything will work as intended and I don't mess anything up.  The cool thing I have noticed with this is that the second partition shows on the launcher in Unity as a second hard drive and my partner and daughter will find it a lot easier accessing the files/folders.

I have only put the OS back on at this stage and not configured applications and settings yet so I guess this is the best time to ask before I progress with this over the weekend.  Because the second partition is mounted at /**media/shared**, would I loose the contents of this partition if I ever decided to do a format/re-install?

---

### Post by Paddy Landau on 2012-08-24
> **idonald said:**
> I will probably create a group called **usershare** or something and set **/media/shared** as the home location for this group.
A group does not have a "home location".

> **idonald said:**
> I have only put the OS back on at this stage and not configured applications and settings yet so I guess this is the best time to ask before I progress with this over the weekend.  Because the second partition is mounted at /**media/shared**, would I loose the contents of this partition if I ever decided to do a format/re-install?
If it is a separate partition, it will not be touched — *provided* that you exclude it from the reformat or re-installation. As a note, you should always keep backups anyway — even if your installation or reformat works correctly, what happens should your hard drive die?

If it is a separate partition, you don't need to create a new group or go through the bindfs method. Just format that partition as NTFS, and you're done!

(If it is not a separate partition, reformatting your data partition (which is the same as your OS partition if you chose the default installation) will indeed erase the data. But by what you have described, it does sound as though you have created a separate partition.)

---

### Post by Morbius1 on 2012-08-24
Some more random thoughts:

** If you are going to use a group I wouldn't use "usershare" only because there is a Samba thing called usershare. There already exists a group you can use call **plugdev**. Once upon a time during the "Golden Age" of Linux all new users were automatically made members of the plugdev group but now you have to add them manually.

** Creating a shared partition as NTFS will in fact work just as Paddy Landau indicated as long as you have it mount automatically. In fact one way of looking at bindfs is that you are doing to a Linux partition what ntfs does by default. Creating an view of a partition or folder with immutable permissions.

---

### Post by idonald on 2012-08-24
I'd feel bad if I decided to create an NTFS partition purely because of the effort you guys have put into this thread to assist and educate me but then it does seem like it will make things a lot easier for me.

I don't like the idea of having an NTFS partition because I am trying to move away from Windows but then, maybe i'm being silly and am just making things difficult for myself.

---

### Post by Paddy Landau on 2012-08-24
> **idonald said:**
> I'd feel bad if…
No, it's OK, really! You must do what is best. You have learned plenty from this thread; and too I have learned some new tricks. We'll feel bad if you go ahead and use a sub-optimal solution.

> **idonald said:**
> I don't like the idea of having an NTFS partition because I am trying to move away from Windows…
Well, I firmly believe in the idea that you do what is most reliable and usable. In this particular case, NTFS will suit your needs best of all. Go ahead and use it!

However, you may want to play around with a couple of test folders doing what Morbius suggested just to learn new tricks.

---

### Post by jammybob56 on 2012-08-24
External Hard Drive Plugged in with your media copyed onto it, that's what i do, works a treat!

---

### Post by idonald on 2012-08-28
Decided to use the NTFS partition and it worked a treat, thanks for all the help guys, I really appreciate your help and I have learned a lot.

---

### Post by Paddy Landau on 2012-08-28
> **idonald said:**
> Decided to use the NTFS partition and it worked a treat…
Excellent; I think you did the best thing.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by idonald on 2012-08-30
> **Paddy Landau said:**
> Excellent; I think you did the best thing.

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

Done, thanks Paddy

---

