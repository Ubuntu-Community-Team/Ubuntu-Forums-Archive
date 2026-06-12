---
title: "Samba share with group permissions"
date: 2010-11-18
forum: General Help
---

### Post by jamesisin on 2010-11-18
I am trying to set up a Samba share on one of my machines where I am the owner and a special group manages permissions for read-only access ( me:specialgroup ).  If I log into the share as me, there is no problem (I have read/write privs as per usual).  However, I am not able to log into the share using any of the group members (there is only one currently).  That user is not able to access the share (failed to mount).

The folder (which is the share) is owned by me:specialgroup and the permissions have been forced down the folder.  Samba is set to Share this folder with no guest or others write access.

How do I make this work?

---

### Post by Morbius1 on 2010-11-18
Not sure I followed that. Did you create a share that looks something like this:

> [Data]
    path = /home/me/Data
    writeable = no
;    browseable = yes
    valid users = me, @specialgroup
    write list = meAnd the remote user who is a member of the "specialgroup" can't get access?

---

### Post by jamesisin on 2010-11-18
Thanks, Morbius1.  I used the GUI to create the share.  I used the command line to alter ownership from me:me to me:specialgroup.  Can you tell me the location of the file which would contain the lines you suggest?

---

### Post by Morbius1 on 2010-11-19
If by GUI you mean the GUI for Classic Samba Shares then the share definition should be at /etc/samba/smb.conf.

If bu GUI you mean Nautilus itself, I don't think you can achieve what you seek. Nautilus-share has it's limitations. The following command will tell you if you are using Nautilus-share:
```
net usershare info --long
```

---

### Post by jamesisin on 2010-11-19
That command displays information about the share in question.  Where is that information housed?  (The smb.conf file makes no mention of said share.)

---

### Post by crustyBarnacle on 2010-11-19
jamesisin,

Since ```
net usershare info --long
``` showed the share, you are sharing directly with Nautilus (right-click on folder, Sharing Options).

This type of sharing will not put any information in **/etc/samba/smb.conf**.

If you want to allow read/write access to others, you can do so as follows:

[LIST=1]
[*]Right-click folder, Sharing Optoins
[*]Put a check in "Share this folder"
[*]Select either (or both): Allow others..  | Guest access...
[/LIST]

Let us know if this works for what you want to do.

-Mario

---

### Post by Morbius1 on 2010-11-19
> **jamesisin said:**
> That command displays information about the share in question.  Where is that information housed?  (The smb.conf file makes no mention of said share.)
Then you used Nautilus-share. The share definitions are located at:
> var/lib/samba/usersharesDespite other comments it is in fact Samba where it is called usershares and has been part of samba for years. The problem for you is it is not editable like a classic-share definition in smb.conf itself.

If the objective is to try to reproduce something with the same functionality as this classic-share:
```
[Data]
    path = /home/me/Data
    writeable = no
    valid users = me, @specialgroup
    write list = me                      
```It is probably possible to do that with usershares but not through Nautilus only by the command line and it would be a tricky maneuver.

If it were me I would simply cut and paste my example to the end of smb.conf, make whatever changes are necessary to point to the correct name, path, users, and groups and see if it produces your desired objective.

Always run the following command after you edit smb.conf to check for errors:
```
testparm -s
```If everything runs without errors restart samba:
```
sudo service smbd restart.
```

[COLOR=Blue]EDIT: If you do decide to add the share definition to smb.conf then you really should go back into Nautilus and "unshare" the Nautilus-share. Using both samba methods on the same target directory is not a good idea.[/COLOR]

---

### Post by jamesisin on 2010-11-21
Ok, that seems to do the trick.  I'll do some more testing, but so far so good.

Oh... and the restart command for Samba is *sudo /etc/init.d/samba restart* (though I used *sudo /etc/init.d/samba reload* as this reloads the conf file).

Thanks.

---

### Post by Morbius1 on 2010-11-21
> **jamesisin said:**
> Oh... and the restart command for Samba is *sudo /etc/init.d/samba restart* (though I used *sudo /etc/init.d/samba reload* as this reloads the conf file).

Thanks.
I didn't notice you were using Ubuntu 8.10 Intrepid Ibex. Sorry about that.

The samba service no longer exists and has been split apart into it's component smbd and nmbd daemons and smbd is no longer started by init.d but by upstart. This happened in 10.04 I think - maybe earlier.

Today the functional equivalent to *sudo /etc/init.d samba restart* is:
sudo service smbd restart
sudo service nmbd restart

---

### Post by jamesisin on 2010-11-21
Yeah, it's time to rebuild my main machine.  I've been putting it off.  For a while.

Is there no longer a reload equivalent?

---

### Post by Morbius1 on 2010-11-21
That I do not know. Your reference to the reload option was the first time I've ever seen it. I'm transferring some large files at the moment or else I'd check it out.

---

### Post by jamesisin on 2010-11-21
Well, maybe the share needs some adjustment.  I am able to access it as me, but group members are not yet able to do so.

Basically, I used your exact example from the first post:

```
[sharename]
    path = /path/to/sharename
    writeable = no
    valid users = me, @specialgroup
    write list = me
```

Any suggestions?

---

### Post by Morbius1 on 2010-11-22
I don't think this is a samba issue anymore I think it's a linux permissions issue. Since @specialgroup is only allowed read access the only requirement is that /path/to/sharename allow read access to "other".

If you do a [COLOR=Blue]*ls -dl /path/to/sharename *[COLOR=Black]it has to look something like this:
[/COLOR][/COLOR]> drwxr-xr-xIf it's not that then make it that:
```
sudo chmod 0755 /path/to/sharename
```If for some reason your directory is set to 0750 and you want to keep it that way then you might want to change ownership of the directory to have the group = specialgroup:
```
sudo chown :specialgroup /path/to/sharename
```

---

### Post by jamesisin on 2010-11-22
That is exactly how I have the permissions arranged: drwxr-x--- me:specialgroup.

---

### Post by Morbius1 on 2010-11-22
Did you create a samba user that's part of the "specialgroup":
```
sudo smbpasswd -a user-in-the-specialgroup
```[COLOR=Blue]EDIT:[/COLOR] And is that user a member of the group:
```
 sudo id user-in-the-specialgroup
```

---

### Post by jamesisin on 2010-11-23
> **Morbius1 said:**
> Did you create a samba user that's part of the "specialgroup":
```
sudo smbpasswd -a user-in-the-specialgroup
```[COLOR=Blue]EDIT:[/COLOR] And is that user a member of the group:
```
 sudo id user-in-the-specialgroup
```

Afraid I'm a little confused.

If I run *id userb* it shows that user is a member of both the sambashare and specialgroup groups.  This is as expected.

The second command (*sudo smbpasswd -a userb*) appears to add userb to the samba password file.  This would seem to defeat the purpose of using a group to control access (as I would have to add each member of specialgroup also to the samba password file).  Do you mean to add the group itself to samba (perhaps *sudo smbpasswd -a @specialgroup*)?

---

### Post by Roasted on 2010-11-23
I agree with what Morbius is saying. To add a little to the mix I figured I would notate some things here to be aware of.

When using Samba on Ubuntu, think of it like a dual layer setup. Just because you say on the Samba GUI that you want Fred to have read/write access on /media/storage, that does NOT mean Fred has read/write access.

There's two levels of permissions. Linux level (operating system) as well as Samba (network level). They must both mesh up properly in order to pass the user through and allow them to have the permissions necessary.

Let's say you're working with two users. Fred and Bob. And you are Fred and you own the computer, and you want yourself + Bob to have access to /media/storage. The easiest thing to do is to create a group and add Fred/Bob to the group. Make sure you log out + back in to "activate" the group settings. Then, assign group with read/write permissions to /media/storage. Blam - you just completed the operating system level. Now you must get the Samba level running.

Fire up the Samba GUI and assign yourself and Bob to have read/write to /media/storage. Blam. Done. :)

Just remember, there's always two levels to working with Samba on Linux. Yes, it may be more confusing, but it can add an extra level of security as well.

---

### Post by endotherm on 2010-11-23
one other thing to consider is the resultant permission set when you (as yourself) create a file within the share. it should default to "youruser:youruser" and not provide access to the group members. 
I set the permissions on my samba shares with SetGID, so that the group that owns the folder being shared, is set as the owner-group for any new files created within the folder. 
you can turn on SetGID with chmod, by putting a '2' in front of the standard permissions octet (eg: 'chmod 2750 .'). I also set the samba create mask and directory mask to use setgid.

on shares where the group can write, but you don;t want them to be able to delete files owned by other users, the "Sticky" bit can be very useful. like SetGid, you set it with chmod.

as for group membership, I've never needed to associate my samba users specifically with a group. the unix users that each samba user is associated with is a member of my sambausers group, so samba just uses those membership credentials. 

good luck. Morbius is a pro. he;ll get you sorted.

---

### Post by Morbius1 on 2010-11-23
First, what Roasted and endotherm just said.

I like to think of Samba as that gatekeeper of the share as it deals with authentication and what a remote user MAY do. It does not have authority over Linux file permissions. With Samba you can only equal or subtract from Linux file permissions which dictates what a remote user CAN do.

You have created a private share and instructed Samba to allow only a subset of all the remote users that have a samba username and password to enter. The @specialgroup is just an easier way of grouping a set of users so that you don't have to write each username individually.

For example: valid users = me, john, andy, mary, chris, .....
Becomes :      valid users = me, @specialgroup

---

### Post by jamesisin on 2010-11-23
I figured it out.

If I pulled up the Properties dialog in Nautilus for the share folder in question, it showed the group as specialgroup.  Excellent.  However, when I ssh'd into that box to see what one of the group members could do I noticed that ls -al showed me:me and not me:specialgroup.

So I ran *chown -R* and *chmod -R* and that fixed the problem.  (I think when I ran chown previously I had -R in the wrong location.)

---

### Post by endotherm on 2010-11-23
> **jamesisin said:**
> I figured it out.

If I pulled up the Properties dialog in Nautilus for the share folder in question, it showed the group as specialgroup.  Excellent.  However, when I ssh'd into that box to see what one of the group members could do I noticed that ls -al showed me:me and not me:specialgroup.

So I ran *chown -R* and *chmod -R* and that fixed the problem.  (I think when I ran chown previously I had -R in the wrong location.)

Good, it sounds like you are seeing the layering in action. 
now, if you want to make sure that any new files created in that folder are owned by "me:specialgroup" , then SetGID, is for you
```
sudo chmod g+s .  <where . is your shares root folder>

OR
sudo chmod 2### .   <replace ### with your desired permissions set>  


```

---

### Post by jamesisin on 2010-12-20
This is sorted out.  The solution, of course, was to stop using the Nautilus implementation of Samba and to prefer creating the share manually (as informed above).  As such I am marking this thread as solved.

endotherm - I did the g+s to lock permissions (good thing to know).  I didn't run the 2### because I couldn't figure out what it did.  Can you fill me in?

---

